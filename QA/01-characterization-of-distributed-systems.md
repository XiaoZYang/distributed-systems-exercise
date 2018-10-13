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

#### Compare and contrast cloud computing with more traditional client-server computing? What is novel about cloud computing a concept?

The similarities between cloud computing and traditional client-server computing are including:
1. Both cloud computing and traditional client-server computing are sharing resources

The dissimilarities between cloud computing and traditional client-server computing are including:
1. Cloud computing provides visualized resources but traditional client-server computing utilize physical resources
