### LRU/LFU相关字段
```
typedef struct redisObject {
    unsigned type:4;  
    unsigned encoding:4;
    unsigned lru:LRU_BITS; 
    int refcount;      
    void *ptr;            
} robj;
```
lru字段包含24位其中
### LRU时间更新
```
robj *lookupKey(redisDb *db, robj *key, int flags) {
    dictEntry *de = dictFind(db->dict,key->ptr);
    robj *val = NULL;
    if (de) {
        val = dictGetVal(de);
        int force_delete_expired = flags & LOOKUP_WRITE;
        if (force_delete_expired) {
            /* Forcing deletion of expired keys on a replica makes the replica
             * inconsistent with the master. The reason it's allowed for write
             * commands is to make writable replicas behave consistently. It
             * shall not be used in readonly commands. Modules are accepted so
             * that we don't break old modules. */
            client *c = server.in_script ? scriptGetClient() : server.current_client;
            serverAssert(!c || !c->cmd || (c->cmd->flags & (CMD_WRITE|CMD_MODULE)));
        }
        if (expireIfNeeded(db, key, force_delete_expired)) {
            /* The key is no longer valid. */
            val = NULL;
        }
    }

    if (val) {
        /* Update the access time for the ageing algorithm.
         * Don't do it if we have a saving child, as this will trigger
         * a copy on write madness. */
        if (!hasActiveChildProcess() && !(flags & LOOKUP_NOTOUCH)){
            if (server.maxmemory_policy & MAXMEMORY_FLAG_LFU) {
                updateLFU(val);
            } else {
                val->lru = LRU_CLOCK();//更新LRU时间
            }
        }

        if (!(flags & (LOOKUP_NOSTATS | LOOKUP_WRITE)))
            server.stat_keyspace_hits++;
        /* TODO: Use separate hits stats for WRITE */
    } else {
        if (!(flags & (LOOKUP_NONOTIFY | LOOKUP_WRITE)))
            notifyKeyspaceEvent(NOTIFY_KEY_MISS, "keymiss", key, db->id);
        if (!(flags & (LOOKUP_NOSTATS | LOOKUP_WRITE)))
            server.stat_keyspace_misses++;
        /* TODO: Use separate misses stats and notify event for WRITE */
    }

    return val;
}
```
### LFU计数统计变更,这里最大只能是255了，
LFU 时lru字段高16位为时间戳(分钟级)，低8位为计数器
#### LFU计数增长
```
void updateLFU(robj *val) {
    unsigned long counter = LFUDecrAndReturn(val);
    counter = LFULogIncr(counter);
    val->lru = (LFUGetTimeInMinutes()<<8) | counter;
}
uint8_t LFULogIncr(uint8_t counter) {
    if (counter == 255) return 255;
    double r = (double)rand()/RAND_MAX;
	
    double baseval = counter - LFU_INIT_VAL;
    if (baseval < 0) baseval = 0;
    double p = 1.0/(baseval*server.lfu_log_factor+1);
    if (r < p) counter++;
    return counter;
}
unsigned long LFUGetTimeInMinutes(void) {
    return (server.unixtime/60) & 65535;//2的16次方65536
}
```
#### LFU计数减少
```
unsigned long LFUDecrAndReturn(robj *o) {
    unsigned long ldt = o->lru >> 8;
    unsigned long counter = o->lru & 255;
    unsigned long num_periods = server.lfu_decay_time ? LFUTimeElapsed(ldt) / server.lfu_decay_time : 0;
    if (num_periods)
        counter = (num_periods > counter) ? 0 : counter - num_periods;
    return counter;
}
```
processCommand入口
```
int processCommand(client *c) {
//...
  if (server.maxmemory && !scriptIsTimedout()) {
  int out_of_memory = (performEvictions() == EVICT_FAIL);//调用performEvictions函数
  }
//...
}
```

### 采样删除
```

```


