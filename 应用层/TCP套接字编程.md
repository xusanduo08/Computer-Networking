​	运行在不同机器上的进程彼此通过向套接字发送报文来进行通信。每个进程好比一座房子，进程的套接字好比是一个门。

​	套接字是应用进程和TCP之间的门，应用程序开发者最多设置一些TCP参数，如最大缓冲长度和最大报文段长度等。

​	为了能对客户机程序发起的连接做出响应，服务器需满足以下条件：

​	1、服务器在客户机程序试图发起连接之前，必须已经作为一个进程在系统中运行；

​	2、服务器程序必须有某种类型的门（更为精确地说是套接字），能够响应来自运行在任意机器上的客户机程序发起的连接。可以将客户机发起连接称为“敲欢迎之门”。

​	客户机程序通过创建一个套接字来向服务器发起一个TCP连接，该套接字包含客户机的指定的服务器IP地址和进程端口号。客户机套接字建立后，客户机的TCP与服务器的TCP发起3次握手并建立一个TCP连接。3次握手发生在运输层，对于客户机程序和服务器程序是完全透明的。

​	三次握手中，客户机“敲”服务器进程的“欢迎之门”（通过服务器欢迎套接字发送连接建立请求）。服务器“听”到敲门时，它将创建一个新门（一个新的套接字，连接套接字），用来为某个特定的客户机程序服务。握手的最后阶段，客户机套接字和服务器套接字之间已存在一个TCP连接。因此，新的套接字又称为服务器的__连接套接字__。

​	TCP连接是客户机套接字和服务器连接套接字之间的一个直接的虚拟管道。客户机进程向它的套接字发送任意字节的数据，TCP保证服务器进程能够通过自己的连接套接字按客户机发送的顺序接收到每个字节的数据。所以，TCP在客户机进程和服务器进程之间提供了__可靠字节流服务__。

​	客户机进程也能从它的的套接字接受字节，服务器进程也能向它的的套接字发送字节。

​	套接字在客户机/服务器应用程序中起着核心作用，所以客户机/服务器应用程序开发又叫套接字编程。

