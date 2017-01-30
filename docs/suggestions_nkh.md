# Untrackable traffic jams detection
## Problem: Traffic jams early detection
- navigation apps are too slow
- some jams are not shown in yandex.maps or google.maps

## Solution
SM messagest related to particular product => sentiment analysis => get messages related to traffic jams and road blocks in a specific area => notify user

# Marketing activity detection
## Problem: Marketing activity detection
SMM or PR specialists need to respond on competitor's marketing/PR activity as soon as possible.

## Solution
SM messagest related to particular product => sentiment analysis => hype detection => notifications

# tech scheme
<img src="https://github.com/BigDataHSE2016/m03-nis-yach-team/blob/master/docs/img/tech-scheme-general-land.png?raw=true" height="400">
```
@startuml
title YACH app scheme

cloud "Input APIs" {
    interface "Twitter" as tw
    interface "VKontakte" as vk 
}

[Data Extraction App] as DEA

node "AWS" {
    [Spark Streaming] as ss
    [Spark Engine] as se
    [S3]
}

node "Output App" {
    [App] as OA
    [DB]
}
cloud "Output channels" {
    interface "telegram" as tg
    interface "slack" as slack 
}

tw -right-> ss
vk -right-> DEA
DEA -right-> [S3]
[S3] -> ss
ss -left-> se 
se -left-> DB
DB <-down-> OA
OA -left-> tg
@enduml
```
