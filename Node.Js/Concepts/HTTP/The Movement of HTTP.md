![[Pasted image 20231005144134.png]]

how do these messages actually make it to their destinations?
	Just as a letter requires a carrier to arrive at its destination, so too does an HTTP request. The carrier, in this case, comes in the form of transport protocols.

#### TCP

The most common transport protocol used in conjunction with HTTP is [TCP](https://developer.mozilla.org/en-US/docs/Glossary/TCP). TCP stands for _Transmission Control Protocol_ and allows two hosts to connect and exchange data streams, guaranteeing the delivery of data packets in the same order as they were sent. This means that TCP ensures that packets are delivered reliably and free from [errors](https://www.codecademy.com/resources/docs/javascript/errors), positioning itself as an incredibly stable way to move data from one location to another.

#### UDP

[UDP](https://developer.mozilla.org/en-US/docs/Glossary/UDP), or _User Datagram Protocol_, is a less commonly used transport protocol. It operates using a connectionless communication model, requiring no “handshaking,” which can potentially lead to unreliability in the delivery of messages. As such, UDP has no mechanism by which to guarantee delivery or ordering of messages. While these are certainly drawbacks for some types of applications, other applications that want to prioritize transmission speed and efficiency over security and reliability may leverage UDP.

While these transport protocols are great for moving your [requests](https://www.codecademy.com/resources/docs/javascript/requests) to their destination, they lack any meaningful security to protect the data while in transit. In order to remedy this issue, encryption protocols are commonly used.

#### TLS

[TLS](https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/), also known as _Transport Layer Security_, is a widely adopted security protocol designed to facilitate secure data transmission via encryption.

TLS evolved out of the encryption protocol known as [SSL](https://www.cloudflare.com/learning/ssl/what-is-ssl/) (Secure Sockets Layer), which has since been deprecated in favor of TLS. While these two protocols are different, the terms are sometimes used interchangeably. Using TLS with HTTP will allow you to use `HTTPS` (_Hypertext Transfer Protocol Secure_), which helps denote the presence of the extra security.

----------------------------------------------------

In conjunction with the different transport protocols mentioned above, there also exist different versions of HTTP. These distinct versions at a baseline operate similarly in that they carry information between entities and maintain important distinctions.

#### HTTP/1.1

[HTTP/1.1](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) was one of the first versions of the HTTP protocol to be designed and implemented. It operates by sending messages in the form of text. HTTP/1.1 is commonly used over TCP and is the slowest of the HTTP versions regarding data transmission.

#### HTTP/2

[HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) is a major revision of HTTP/1.1, developed with the intent to try and reduce web page load latency. However, the most significant departure from HTTP/1.1 is the encapsulation of all messages in binary format rather than plain text. This allows HTTP/2 to apply different techniques for data transmission, including sending smaller packets of data for greater flexibility of data transfer. This also allows a single connection to be made between two communicating entities rather than multiple as required by HTTP/1.1. Similar to HTTP/1.1, HTTP/2 also leverages TCP for transport.

#### HTTP/3

[HTTP/3](https://en.wikipedia.org/wiki/HTTP/3) is the third major version of HTTP. While there are quite a few complex technological differences between HTTP/3 and the previous versions, one of the most important is how the protocol deals with lost packets. HTTP/3 also differs through its use of transport protocol, leveraging a transport protocol called [QUIC](https://en.wikipedia.org/wiki/QUIC), which applies specific controls over UDP. HTTP/3 is currently an [Internet Draft](https://en.wikipedia.org/wiki/Internet_Draft).


_No matter which of these versions of HTTP are used over which transport protocol, the outcome is the same—the transmission of information in the form of a request and the reply to that request in the form of a response._

