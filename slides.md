---
theme: seriph
background: https://kafka.apache.org/images/streams-and-tables-p1_p4.png
class: 'text-center'
highlighter: shiki
lineNumbers: false
info: |
  Kafka: a Distributed Messaging System and an ACID Database.

  Learn more at [Kafka](https://kafka.apache.org/)
drawings:
  persist: false
---

# Kafka: a Distributed Messaging System and an ACID Database

[hi-rustin](https://github.com/hi-rustin)

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

---
layout: center
---

# Kafka is a Distributed Messaging System
#### Requirements
#### Architecture And Design

<br/>

# Kafka is an ACID Database
#### Atomicity
#### Consistency
#### Isolation
#### Durability

<br/>

# TiCDC Writes To Kafka

--- 

# Messaging System Requirements
<br/>  
<br/>  


## Log Collection
### User activity events
### Operational metrics
<br/>  

## Message Queue
### 11.11
<br/>  


## Streaming processing
### Kafka streams

---

<div class="arch">
<div>

# Architecture

</div>

<div
  class="relation"
>

```plantuml {scale: 0.9}
@startuml

together {
  [Producer1]

  [Producer2]
}

package "Kafka Cluster" {
  node "Broker1" {
    [topic1/part1] as b1t1p1 #Yellow
    [topic1/part2] as b1t1p2 #Green
    [topic2/part1] as b1t2p1 #Green
  } 
  node "Broker2" {
    [topic1/part1] as b2t1p1 #Green
    [topic1/part2] as b2t1p2 #Yellow
    [topic2/part1] as b2t2p1 #Green
  } 
  node "Broker3" {
    [topic1/part1] as b3t1p1 #Green
    [topic1/part2] as b3t1p2 #Green
    [topic2/part1] as b3t2p1 #Yellow
  } 
}

together {
  package "Consumer Group1" as Group1 {
    [Consumer1]
    [Consumer2]
  }

  package "Consumer Group2" as Group2 {
    [Consumer3]
    [Consumer4]
  } 
}


[Producer1] --> Broker1
[Producer1] --> Broker2
[Producer1] --> Broker3
[Producer2] --> Broker1
[Producer2] --> Broker2
[Producer2] --> Broker3
[Consumer1] --> Broker1
[Consumer1] --> Broker2
[Consumer2] --> Broker1
[Consumer2] --> Broker2
[Consumer3] --> Broker3
[Consumer4] --> Broker3
@enduml
```

</div>
</div>

<style>
.arch {
  display: flex;
}

.arch img {
  margin-top: -80px;
}

.relation {
  position: absolute;
  z-index: 1;
  left: 120px;
  top: 60px;
  font-size: 12px;
}

h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 50%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
  writing-mode: vertical-rl;
  text-orientation: mixed;
}
</style>