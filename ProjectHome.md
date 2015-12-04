# What is this project about? #
serial-to-tcp is a **serial port over tcp/IP server** written in [node.js](http://www.nodjs.org). Originally, this tool was intended for use by the [PlugWise-java](http://code.google.com/p/plugwise-java/) project, so I could acces remotely installed [PlugWise](http://www.plugwise.com) Stick module. However I created a separate project for this tool in order to enable reuse by others.

# Features #
  * This tool supports **multiple connections**. The first connection made to the server will have **write** permission, all other connections will have **read** permission only. Upon disconnect of the oldest connection, the second-oldest connection will obtain write permission.
  * This tool can be run in **monitoring** mode using the -monitor command line option. This way, it will output the serial/tcp conversation to the console.
  * You can terminate the tool and all connections using **ctrl-c**, or the [SIGTERM](http://en.wikipedia.org/wiki/SIGTERM) and [SIGINT](http://en.wikipedia.org/wiki/SIGINT_(POSIX)) [POSIX signals](http://en.wikipedia.org/wiki/POSIX_signal).
  * The node js module exposes the **SerialServer class**, which does all the work (except for the monitoring). You may instantiate this class within your own code in order to incorporate serial-to-tcp features.

# Usage #
In order to run this tool, you need to have node.js installed and working, preferably a recent version. You also need to install [npm](http://npmjs.org/) (The node package manager), and the serialport module. See the installation section on the wiki.