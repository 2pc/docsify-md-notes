### sketchy-outline

```
@startuml
!theme sketchy-outline
participant Kafka as Foo
participant       Actor       as Foo1
participant    Boundary    as Foo2
participant     Control     as Foo3
participant      Entity      as Foo4
participant    Database    as Foo5
participant Collections as Foo6
queue       Queue       as Foo7
Foo -> Foo1 : To actor
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo3 -> Foo3 : Self callback

Foo3 --> Foo : callack

Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo6 --> Foo1 : callack

Foo -> Foo7: To queue
@enduml
```
### crt-green

```
@startuml
!theme crt-green
participant Kafka as Foo
participant       Actor       as Foo1
participant    Boundary    as Foo2
participant     Control     as Foo3
participant      Entity      as Foo4
participant    Database    as Foo5
participant Collections as Foo6
queue       Queue       as Foo7
Foo -> Foo1 : To actor
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo3 -> Foo3 : Self callback

Foo3 --> Foo : callack

Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo6 --> Foo1 : To collections

Foo -> Foo7: To queue
@enduml
```
### reddress-lightred
```
@startuml
!theme reddress-lightred
participant Kafka as Foo
participant       Actor       as Foo1
participant    Boundary    as Foo2
participant     Control     as Foo3
participant      Entity      as Foo4
participant    Database    as Foo5
participant Collections as Foo6
queue       Queue       as Foo7
Foo -> Foo1 : To actor
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo3 -> Foo3 : Self callback

Foo3 --> Foo : callack

Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo6 --> Foo1 : To collections

Foo -> Foo7: To queue
@enduml
```
### superhero-outline
```
@startuml
!theme superhero-outline
participant Kafka as Foo
participant       Actor       as Foo1
participant    Boundary    as Foo2
participant     Control     as Foo3
participant      Entity      as Foo4
participant    Database    as Foo5
participant Collections as Foo6
queue       Queue       as Foo7
Foo -> Foo1 : To actor
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo3 -> Foo3 : Self callback

Foo3 --> Foo : callack

Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo6 --> Foo1 : To collections

Foo -> Foo7: To queue
@enduml
```

### minty
```
@startuml
!theme minty
participant Kafka as Foo
participant       Actor       as Foo1
participant    Boundary    as Foo2
participant     Control     as Foo3
participant      Entity      as Foo4
participant    Database    as Foo5
participant Collections as Foo6
queue       Queue       as Foo7
Foo -> Foo1 : To actor
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo3 -> Foo3 : Self callback

Foo3 --> Foo : callack

Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo6 --> Foo1 : To collections

Foo -> Foo7: To queue
@enduml
```

### mimeograph
```
@startuml
!theme mimeograph
participant Kafka as Foo
participant       Actor       as Foo1
participant    Boundary    as Foo2
participant     Control     as Foo3
participant      Entity      as Foo4
participant    Database    as Foo5
participant Collections as Foo6
queue       Queue       as Foo7
Foo -> Foo1 : To actor
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo3 -> Foo3 : Self callback

Foo3 --> Foo : callack

Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo6 --> Foo1 : To collections

Foo -> Foo7: To queue
@enduml
```

### metal
```
@startuml
!theme metal
participant Kafka as Foo
participant       Actor       as Foo1
participant    Boundary    as Foo2
participant     Control     as Foo3
participant      Entity      as Foo4
participant    Database    as Foo5
participant Collections as Foo6
queue       Queue       as Foo7
Foo -> Foo1 : To actor
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo3 -> Foo3 : Self callback

Foo3 --> Foo : callack

Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo6 --> Foo1 : To collections

Foo -> Foo7: To queue
@enduml
```
