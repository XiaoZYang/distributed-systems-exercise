### Give five types of hardware resources and five types of data or software resource that can usefully be shared. Give examples of their sharing as it occurs in practice in distributed systems.

Shared hardware resources:
- *CPU*: computing service on cloud
- *disk*: NFS
- *memory*: in-memory database
- *router*
- *bridge*

Shared software resources:
- *database* on server
- *stream media* like audio or video, (listen to music or watch video)
- *domain name and IP mapping* in DNS server
- *route information* stored in the router
- *load balancer* which forwards requests from the client to real backend server

### How might the clocks in two computers that are linked by a local network be synchronized without reference to an external time source? What factors limit the accuracy of the procedure you have described? How cloud the clocks in a large number of computers connected by the Internet be synchronized? Discuss the accuracy of that procedure.
The procedure might be:
1. These two computer elect a leader by their IP address, the computer with lower address will be the leader and the other will be the follower
2. The leader sends two packets to the follower and the follower calculates the *latency* of the link
3. The leader sends its *clock* value
4. The follower synchronize its clock by the received *clock* plus the *latency*

The factors limit the accuracy of the procedure are:
1. The jitter of the network
2. The processing cost of adding the clock and the latency
3. The transmission delay of the leader
4. The acceptance delay of the follower

In a large number of computers connected by the Internet the clocks are synchronized by
1. All computers elect a leader, and the rest of computers are the followers,
2. All the followers synchronize clock from the leader.

The accuracy of that procedure are dependent on the delay and the latency of the network.

### Consider the implementation strategies for massively multiplayer online games as discussed in Section 1.2.2. In particular, what advantages do you see in doing a single server approach for representing the state of the multiplayer game? What problems can you identify and how might be resolved?

The advantages in doing a single server approach are:
1. It's easy to design and implementation the server,
2. It's easy to manage the state of the multiplayer game,
3. It's easy for the client to find the server,
4. It's easy for the clients to communicate with each other.

The problems are:
1. As the increasing of clients the server will easily be the bottleneck of the system,
2. It cost a lot to scale the server since there is only one server,
3. If the server is down all the clients can't work

The problems mentioned above might be solved to use a cluster of distributed servers instead of a central server.

### A user arrives at a railway station that they has never visited before, carrying a PDA that is capable of wireless networking. Suggest how the user could be provided with information about the local services and amenities at that station, without entering the station's name or attributes. What technical challenges must be overcome?

The user could be provided with local services by the station when the PDA connected to the network. The server could identify the station at which the user is by the information of the network such as SSID, IP, mac address.

The challenges must be overcome are including:
1. The mapping of network information and station should be maintained centrally,
2. The server of any station should manage the information about the station.

### Compare and contrast cloud computing with more traditional client-server computing? What is novel about cloud computing a concept?

The similarities between cloud computing and traditional client-server computing are including:
1. Both cloud computing and traditional client-server computing are sharing resources
2. xx
3. xx

The dissimilarities between cloud computing and traditional client-server computing are including:
1. Cloud computing provides visualized resources but traditional client-server computing utilize physical resources
2. xx
3. xx

### Use the World Wide Web as an example to illustrate the concept of resource sharing, client and server. What are the advantages and disadvantages of HTML, URLs and HTTP as core technologies for information browsing? Are any of these technologies suitable as a basis for client-server computing in general?

*Resource sharing*: different computers use or consume the same resource, in World Wide Web, the HTML files are consumed by all the browsers who visits the same website.

*Client and server*:
- client is the process which consumes the resources, whereas the server is the process who provides resources.
- client send requests  and server reply to the requests

---

The advantages of HTML, URLs and HTTP as core technologies are:
1. It's easy to extend the system as the information growing rapidly, because the URLs and HTTP are the standard of World Wide Web, the only thing new resources, services and applications need to do is compatible with it.
2. It's easy to scale the system, there is no limitations for the WWW system to increase a server or client
3. The WWW system is highly available, failure of any server won't break the whole system down
4. All the resources on the Web are expressed by the URLs, so it's transparent for the users

---

In my opinion, URLs and HTTP are suitable as a basis, 
- the model of HTTP is request-response which is suitable to implement client-server applications
- the HTTP and URLs hide the details of the resource, which helps the client-server computing manage resources


### A server program written in one language (for example, C++) provides the implementation of a BLOB object that is intended to be accessed by clients that may be written in a different language (for example, Java). The client and server computers may have different hardware, but all of them are attached to an internet. Describe the problems due to each of the five aspects of heterogeneity that need to be solved to make it possible for a client object to invoke a method on the server object.

1. Hardware problems: the server program and client program usually runs on different computers, for example, the server runs on the minicomputer, whereas the client runs on PC, laptop or even smart phones
2. Operating system problems: the server may run on Linux, but the client runs on Windows
3. Network problems: the server may connect to the Internet by Ethernet, but the client may connect to the Internet by WiFi, so we should ensure that the request from the client are transmitted to the server
4. Programming languages problems: as we know, the data are expressed diversely in different languages, for example, there is *one* bit representing the sign of an integer, but there are two in java. Therefore, we should eliminate these conflicts and make it transparent to the application.
5. Implementation problems: the program may be implemented by several groups of people, they follow different rules, we should make their programs compatible with each other.


### An open distributed system allows new resource-sharing services such as the BLOB object in Exercise 1.7 to be added and accessed by a variety of client programs. Discuss in the context of this example, to what extent the needs of openness differ from those of heterogeneity.

The needs of openness are the necessary basis to extend or reimplement the system, which are including:
1. the specification and the documentation of the public interfaces exposed to the client
2. the description of the functions of the server
3. the limitations of the implementation

The needs of solving heterogeneity problems are including:
1. Apply same hardware standard
2. Avoid using feature, inconsistent implementation, library of operating system
3. Declare the public documentation about data representation for different languages
4. Apply same network standard
5. Make agreement about the development

In conclusion, the openness concerns more on how to implement functionalities or new features which compatible with old system which is relatively high-level, but the heterogeneity pay attentions to solving inconsistencies among environments which is more low-level.

### Suppose that the operations of the BLOB object are separated into two categories -- public operations that are available to all users and protected operations that are available only to certain named users. State all of the problems involved in ensuring that only the named users can use a protected operation. Supposing that access to a protected operation provides information that should not be revealed to all users, what further problems arise?


