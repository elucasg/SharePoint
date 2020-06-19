# How to test network connection is open
Determine if the port has a listener on the server you want to connect to:

`nestat -an | find "<port number>"`

Two methods to see if the port is open over the network:

**Telnet**

From the command prompt run the following:

`telnet <Destination IP> <port number>`

**PowerShell Script**


```
$socket = new-object Net.Sockets.TcpClient
$socket.Connect("<Destination IP>",<port number>)
$socket.Connected
```
