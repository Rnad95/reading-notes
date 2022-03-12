# The HTTP Request Lifecycle

## 1. Local Processing  

---

The steps depending on browser:

1. Extract the protocol type such as: HTTPs, HTTP, ftp, and so on. With the port for this protocol (80 for HTTPs).  

2. Resolving the IP address using DNS Server which changes the scheme(url for example: www.google.com) to IP address.

## 2. Resolve an IP Address

---

DNS Server is a sequence that includes response for the request.  

1. If the cache of the DNS is not exist, the browser fires off using UDP which cares about the arriving the packet at/around the time and reach the packets without acknowledgement(ACK).  

2. The Request travel to find the DNS Server to change the hostname to IP Address using routing table.  

3. Next, the server find the route of DNS server to search of the hostname in cache to response the success or fail.  

![DNS](https://media.geeksforgeeks.org/wp-content/uploads/20200822065029/UntitledDiagram.png)

## 3. Establish a TCP Connection

---

The request has Two types either UDP (User Datagram Protocol) or TCP (Transmission Control Protocol)  

- The main difference between the TCP and UDP is that TCP concerns the reliability unlike UDP which cares about receive the packet at the time like video call.  

- TCP has a buffer to save the packet that re-order the packets, and an ack to check if the packet is reached or not.  

- TCP connection has three way handshake:

1. Firstly, sending a set of sequence number called SYN packet to check the connection and receiving the data.  

2. Next, the server send response to the client SYN-ACK which contains the same SYN sequence number + 1

3. Then, Sending ACK + 1 to ensure our data is reached.  

- The connection could be half duplex(bidirectional) or full duplex.  

The Difference between TCP and UDP.

![TCP and UDP](https://www.colocationamerica.com/wp-content/uploads/2018/12/udp-tcp.jpg)  

## 4. Send an HTTP Request

---

1. When sending the HTTP Request, the TCP header and body are sent. The size of Header is bytes and has flags, HTTP method, source and destination Address, and so on.

2. The body content of an HTTP request is completely optional, but often contains something like form data or JSON.

3. Then, it follows the same routing  operations. Once the server receive the HTTP Request, it generates a response contains status line, header, and the body.

4. The Buffer now is significant to order the packets (in TCP).

## 5. Tearing Down and Cleaning Up

---

the client send FIN packet when all packets delivered

![TCP tearDown](https://www.ionos.co.uk/digitalguide/fileadmin/DigitalGuide/Schaubilder/EN-tcp-verbindungsabbau.png)

## Way of performing HTTP requests in Java

- **HttpUrlConnection**
To create a HTTP request without create a new library.  

- **Creating a Request**

The HttpUrlConnection class has all method we need to HTTP Request like GET, POST, HEAD, OPTIONS, PUT, DELETE, TRACE.

Example of get method using HttpUrlConnection to pass URL

![Get Method](<https://i.ibb.co/nqpmYsM/Screenshot-from-2022-03-13-02-25-08.png>)

- **Adding Request Parameters**
One of the way to add parameters, we should store the data in string, use setDoOutput then passing the parameter using getParamsString.

- **Setting Request Headers**

To Add the Header to Request, we use `setRequestProperty()` and to read the header the method `getHeaderField()` is used.

- **Configuring Timeouts**

To determine the timeout of receiving a packet, we can use `setConnectTimeout()` and `setReadTimeout()` methods and the time will be in millisecond.

- **Handling Redirects**

we need to redirect method sometime in the Request, we can use `setInstanceFollowRedirects()` method for specific connection or `setFollowRedirects()` method for redirect all connections

- **Reading the Response**

Check the connection and the Request arriving could be using the response. To execute the request, we can use: `getResponseCode()`, `connect()`, `getInputStream()` or `getOutputStream()` methods:

- **Reading the Response on Failed Requests**

As mentioned in the previous section we have to read the Response but what can we do for the fails Response. Actually, we can use `getErrorStream()` with `InputStreamReader()`.
