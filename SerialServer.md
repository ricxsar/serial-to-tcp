# SerialServer #
The SerialServer class of this module does all the heavy lifting. It implements the following features:
  * Setup of the tcp/ip server socket
  * Opening of the serial port
  * Handling of incoming connections
  * Managing read/write permisisons for the connections
  * Handling of incoming and outgoing data
  * Emitting of events.

## Events ##
The SerialServer class is a node.js [EventEmitter](http://nodejs.org/api/events.html#events_class_events_eventemitter). It supports the following events:
  * on("**starting**",function(){});
  * on("**started**",function(){});
  * on("**stopping**",function(){});
  * on("**stopped**",function(){});
  * on("**in**",function(data){});
  * on("**out**",function(data){});

## Instantiation ##
In order to instantiate, use the following code:

```
var serialserver=require("serialserver");

var serialPortPath="/dev/tty.someSerialPort";
var baudrate=115200;
var tcpPortNumber=23;
var monitoring=true;

var serialServer=new serialserver.SerialServer(serialPortPath,baudrate, tcpPortNumber);

serialServer.on("started",function(){
    console.log("The serial server started.");
});

serialServer.on("stopped", function(){
    console.log("The serial server stopped.");
});

if (monitoring){
    serialServer.on("in",function(data){
        console.log("IN : "+data.toString("utf8"));
    });
    serialServer.on("out",function(data){
        console.log("OUT:"+data);
    });
}

serialServer.start();
```