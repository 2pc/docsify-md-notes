


mermaid时序图修改样式

Link: https://codepen.io/atnyman/pen/gabGXV
```
<!DOCTYPE html>
<html lang="en" >
<head>
  <meta charset="UTF-8">
  <title>CodePen - Mermaid Sequence Diagram</title>
  <link rel="stylesheet" href="./style.css">

</head>
<body>
<!-- partial:index.partial.html -->
<div class="mermaid">
sequenceDiagram
  participant System
  participant App
  participant Module
  participant App2
  System->>App: Do you hear me
  App->>Module: Alive?
  Module->>App2: app2
  App2-->>Module: app2 resp
  Module-->>App: Yay!
  App-->>System: Stop
</div>
<!-- partial -->
  <script src='https://cdnjs.cloudflare.com/ajax/libs/mermaid/0.5.1/mermaid.min.js'></script>
  <script  src="./script.js"></script>

</body>
</html>
```
style.css
```
@import url(https://fonts.googleapis.com/css?family=Arvo:700italic);

body {
  background: #222;
  color: #fff;
  font-family: 'Arvo', serif;
  font-weight: 700;
  font-style: italic;
}
.actor {
  stroke-width: 2;
  stroke: #fff;
  fill: #222;
  font-family: 'Arvo', serif;
  font-weight: 700;
  font-style: italic;
}
text.actor {
  fill: #fff;
  stroke: none; 
}
.actor-line {
  stroke: #fff;
}
.messageLine0 {
  stroke-width: 1;
  marker-end: "url(#arrowhead)";
  stroke: #fff;
}
.messageLine1 {
  stroke-width: 1;
  stroke-dasharray: "2 2";
  stroke: #fff;
}
#arrowhead {
  fill: #fff;
}
.messageText {
  fill: #222;
  stroke: #fff;    
}
```
