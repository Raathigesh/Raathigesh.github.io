---
published: false
layout: post
excerpt: There are some great logging framework in NodeJS which will allow you to log to various destinations. Winson in one of the good logging framework which can log to multiple transports.
modified: {}
tags: 
  - NodeJS
  - EventLog
  - Windows
  - Logging
  - WindowsNode
comments: true
---

There are some great logging framework in NodeJS which will allow you to log to various destinations. [Winson](https://github.com/winstonjs/winston) in one of the good logging framework which can log to multiple transports.

Recently I wanted to log to Windows event log from my Node JS application and I was planning to use Winston along with [Winston-winlog](https://github.com/jfromaniello/winston-winlog) to log the event viewer.

### Failed Attempt to use Winston-winlog
Winston-winlog uses [Windows Event Log Js](http://jfromaniello.github.io/windowseventlogjs/) internally to write to the event log. But unfortunately Windows Event Log Js is a native module and it has to be compiled. But I couldn't successfully compile it.

### Edge JS with a Class Library
Other option I was attempting to do was to write a simple Class library which will allow  me to log message to Windows Event log and I can invoke the methods from Node JS through the awesome [Edge Js Library](https://github.com/tjanczuk/edge). But Edge Js requires .Net 4.5 but we had to work with .Net 4.0 so this was no longer a viable option.

### node-windows - The Saviour
After some googling, I found an amazing module called [node-windows](https://github.com/coreybutler/node-windows), which can write to Windows Event Log and it not a native module so no need of compilation. 

Node windows not only has event logging functionality but it also has some other amazing windows related features.

Happy Noding Folks!