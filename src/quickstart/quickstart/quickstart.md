#1,netty的作用
​	The Netty project is an effort to provide an asynchronous event-driven network application framework and tooling for the rapid development of maintainable high-performance and high-scalability protocol servers and clients.

# 2，`ByteBuf` 在netty和NIO中的不同

`ByteBuf` does not have such a method because it has two pointers; one for read operations and the other for write operations. The writer index increases when you write something to a `ByteBuf` while the reader index does not change. The reader index and the writer index represents where the message starts and ends respectively.

In contrast, NIO buffer does not provide a clean way to figure out where the message content starts and ends without calling the flip method. You will be in trouble when you forget to flip the buffer because nothing or incorrect data will be sent. Such an error does not happen in Netty because we have different pointer for different operation types.