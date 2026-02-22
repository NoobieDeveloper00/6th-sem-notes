
# Architecture of Distributed Operating Systems

## 1️⃣ Introduction to Distributed Systems

You need a tight, exam-ready structure here.

---

## 📌 Definition (Write this cleanly in exam)

A **Distributed System** is a collection of independent computers connected by a network that appear to users as a *single coherent system.*

That phrase “single coherent system” is straight from standard texts like Coulouris. Safe to use.

---

## 📌 Key Characteristics

- Multiple autonomous computers
    
- Communication via message passing
    
- No shared global clock
    
- Independent failure of components
    
- Resource sharing

That “no global clock” line is very important. Professors love it.

---

## 📌 Why Distributed Systems? (Motivations)

This is where marks hide.

### 1️⃣ Resource Sharing

Printers, files, databases shared across machines.

### 2️⃣ Performance Improvement

Parallel execution → faster processing.

### 3️⃣ Scalability

Add more machines instead of upgrading one.

### 4️⃣ Reliability / Fault Tolerance

If one node fails, system continues.

### 5️⃣ Cost Effectiveness

Many small machines cheaper than one supercomputer.

---

## 📌 Core Challenges (very scoring)

- Concurrency
    
- Lack of global clock
    
- Partial failures
    
- Network latency
    
- Security

If exam asks:  
“What are issues in distributed systems?”  
These bullets win marks.

---

## Refined Version (Exam-Ready)

### Client–Server:

> A centralized architecture where dedicated servers provide services and clients request them.

Key idea: **Role distinction.**  
Server = provider  
Client = requester

---

### Peer-to-Peer (P2P):

> A decentralized architecture where each node can act both as a client and as a server.

Key idea: **No central authority.**  
Every peer is equal.

---

In **Distributed Operating Systems (DOS)**, architecture is commonly classified into three models:

# 1️⃣ Minicomputer Model

Back when dinosaurs roamed the data center.
### Idea:

Several minicomputers are connected via a network.  
Each one serves multiple users through terminals.

## Structure:

```
[Terminal Users]
       ↓
[Minicomputer 1] --- Network --- [Minicomputer 2] --- [Minicomputer 3]
```

Each minicomputer:

- Has its own CPU
    
- Has its own memory
    
- Has its own users
    

They cooperate when needed.

### Key Point:

Users are tied to a specific machine, but machines can share resources.

### Pros:

- Simple extension of centralized systems
    
- Resource sharing possible
    

### Cons:

- Load imbalance (one machine busy, another idle)
    
- Users still logically attached to one system
    

---

# 2️⃣ Workstation Model

Now we enter the “everyone has their own machine” era.

### Idea:

Each user has a personal workstation.  
All workstations are connected via a network.

## Structure:

```
[Workstation 1] ---\
[Workstation 2] ---- Network ---- [Workstation 3]
[Workstation 4] ---/
```

Each workstation:

- Has its own CPU
    
- Runs its own processes
    
- Owned by one user
    

### Important feature:

If your workstation is idle, others can use its resources.

So instead of machines serving many users,  
each user has a machine.

### Pros:

- High autonomy
    
- Interactive performance is good
    

### Cons:

- Wasted CPU when idle
    
- Load balancing becomes tricky
    
- Security issues if others use your machine
    

---

# 3️⃣ Processor Pool Model
### Idea:

There are **no personal machines for computation**.  
There is a pool of processors.  
Users submit jobs, and processors are dynamically assigned.

## Structure:

```
Users → Network → Processor Pool → Assigned CPU(s)
```

Users don’t “own” a machine.

When you run a program:

- System picks an available processor
    
- Assigns it to you
    
- After completion, it returns to pool
    

### This is resource sharing done right.

### Pros:

- Excellent load balancing
    
- High utilization
    
- Flexible resource allocation
    

### Cons:

- More complex OS
    
- Requires good scheduling mechanism
    

---

# Quick Comparison (Exam Table)

|Model|User Owns Machine?|Resource Usage|Load Balancing|
|---|---|---|---|
|Minicomputer|No (shared multi-user machine)|Moderate|Poor|
|Workstation|Yes|Often inefficient|Moderate|
|Processor Pool|No|Very efficient|Excellent|

---

# Conceptually Think Like This

Minicomputer → Many users per machine  
Workstation → One user per machine  
Processor Pool → No ownership, pure shared computation

# System Architecture Types in Distributed OS

---

## 1️⃣ Client–Server Architecture

![Image](https://images.openai.com/static-rsc-3/PypEzVoLqpAs4-CRZBbe8XR8EydcD3ZiV44-493_y6VDv6f86ModU368McuF7Jsr34pQLXny4vNqJCaMNaYsZer0UWipyVhrLhGt3FwZsrI?purpose=fullsize&v=1)





![Image](https://www.researchgate.net/publication/271341309/figure/fig3/AS%3A759210509881347%401558021299645/Three-tier-Client-server-architecture.jpg)

### Characteristics:

- Centralized server
    
- Easy management
    
- Easier security control
    
- Single point of failure

### Example:

Web server systems

---

## 2️⃣ Peer-to-Peer Architecture

![Image](https://images.openai.com/static-rsc-3/PoKYh8s_JdT6IEPEdtRahI_x9kPKM4jQ47grlUNBSKCm89C0gBI8_7hwcX-6JPmKp3rb0wA1nYU4fyXu4x3fdazH5n6GdADPrhwZUn_LK0U?purpose=fullsize&v=1)



![Image](https://images.openai.com/static-rsc-3/qMqmJmVT6tAzSCGmVIUysIN-BEQY58OF5xXtYrRZPLMmrDLMqEMtmXNspiTG6N9qE_KGjUF1sPU0Wt2d3DKEw1rK3DkSp0_nKJPMqPq9EXU?purpose=fullsize&v=1)


### Characteristics:

- Decentralized
    
- No single point of failure
    
- Harder to manage
    
- More scalable

---

## 3️⃣ Hybrid Architecture

Combination of client-server and P2P.

Example:  
Modern distributed applications where:

- Central server for authentication
    
- Peers exchange data directly

---
# Three Distributed System Models

These are _ways of viewing_ a distributed system. Same system, different lens.

## 1️⃣ Physical Model

This is the hardware-level view.

It describes:

- How many machines
    
- How they’re connected
    
- What kind of network
    
- What kind of processors
    

Think:

- Is it a cluster?
    
- Is it geographically distributed?
    
- Are nodes homogeneous or heterogeneous?
    

Example:

- A cloud data center with 1000 servers connected by high-speed LAN.
    
- Multiple regional data centers connected via WAN.
    

This model answers:

> What does the system physically look like?

It does NOT care about software structure yet.

---

## 2️⃣ Architectural Model

Now we move to software structure.

This describes:

- How components interact
    
- How responsibilities are divided
    
- Communication patterns
    

Typical architectural styles:

- Client–Server
    
- Peer-to-Peer
    
- Multi-tier (like 3-tier architecture)
    
- Microservices
    

Here we ask:

> How are services organized and who talks to whom?

For example:  
Client → Server → Database  
or  
Peers communicating equally.

This model defines interaction patterns.

---

## 3️⃣ Fundamental Model

Now we go deeper into theoretical properties.

This model captures assumptions about:

- Timing
    
- Failures
    
- Security
    

It is usually divided into:

1. **Interaction model**
    
2. **Failure model**
    
3. **Security model**
    

This is where examiners get philosophical.

It answers:

> What assumptions are we making about time, communication, and faults?

---

# Clean Conceptual Summary

|Model Type|Focus|
|---|---|
|Physical Model|Hardware structure|
|Architectural Model|Software organization|
|Fundamental Model|Assumptions about timing, failures, security|

|Issue|Why It Happens|
|---|---|
|Concurrency|Multiple processes execute simultaneously|
|No Global Clock|Each node has its own local clock|
|Independent Failures|Nodes and network fail separately|

---

# Issues in Distributed Operating Systems (Very Important)

This topic is heavy scoring. If a 5-mark question appears from UNIT-2, this is a prime suspect.

We structure it cleanly so you can expand or compress based on marks.


## 1️⃣ Transparency

**Transparency** in a distributed system means hiding the distributed nature of the system from users and applications.

Issue:  
System must hide distribution while still handling complexity internally.

Difficulty:

- Network delays
    
- Failures
    
- Replication management

---

## 2️⃣ Scalability

System should handle:

- Increasing users
    
- Increasing nodes
    
- Increasing data

Challenges:

- Bottlenecks
    
- Centralized components
    
- Network congestion

---

## 3️⃣ Concurrency

Multiple users/processes access shared resources simultaneously.

Problem:

- Race conditions - A **race condition** happens when two or more processes access and modify shared data at the same time, and the final result depends on the order in which they execute.
    
- Inconsistent data

Requires:

- Synchronization mechanisms
    
- Distributed locking

---

## 4️⃣ Consistency

Especially important in distributed databases.

If data is replicated:

- Updates must reflect everywhere
    
- Avoid stale data
    

Major challenge:  
Maintaining ACID properties across nodes.

---

## 5️⃣ Fault Tolerance

Nodes can fail independently.

Problem:

- Partial failures (hardest issue in distributed systems)
    

System must:

- Detect failures
    
- Recover automatically
    
- Maintain service continuity
    

---

## 6️⃣ Heterogeneity

Different:

- Hardware
    
- Operating systems
    
- Network protocols
    

System must work across all.

---

## 7️⃣ Security

More attack surface:

- Data interception
    
- Unauthorized access
    
- Node compromise
    

Needs:

- Authentication
    
- Encryption
    
- Access control

---

## 2️⃣ No Global Clock

Every machine has its own clock.

Clocks:

- Drift
    
- Are not perfectly synchronized
    
- Have different time perceptions
    

So if:

Machine A logs event at 10:00:01  
Machine B logs event at 10:00:00

You cannot immediately conclude B happened first.

This creates problems in:

- Ordering events
    
- Debugging
    
- Coordinating transactions
    

Solution concepts:

- Logical clocks (Lamport clocks)
    
- Vector clocks
    
- Clock synchronization algorithms
    

Key exam line:

> In distributed systems, there is no single global time reference, making event ordering difficult.

---

## 3️⃣ Independent Failures

This one is brutal.

In centralized systems:  
If the system fails, everything fails.

In distributed systems:  
One node may fail while others continue working.

So you can have:

- Partial failures
    
- Network partition
    
- One server down
    
- Message lost
    

This is harder than total failure.

Because:  
You may not even know whether:

- The machine crashed
    
- The message was delayed
    
- The network dropped packets
    

This uncertainty makes distributed systems extremely complex.

----
# Communication Networks and Protocols in Distributed OS

This is important because distributed systems = machines talking over networks. If communication fails, everything collapses.

We structure this for exam scoring.

---

# 1️⃣ Communication Networks

A distributed system relies on a communication network to connect nodes.

### Types of Networks (exam bullets):

- LAN (Local Area Network)
    
- MAN (Metropolitan Area Network)
    
- WAN (Wide Area Network)
    
- Internet (global scale)
    

For exams, just write:

> Nodes communicate via message passing over LAN/WAN networks.

That’s enough unless they ask deeper.

---

# 2️⃣ Communication Models

Two major models in Distributed OS:

### 1️⃣ Message Passing Model

In distributed systems, processes do NOT share memory.

They communicate by **sending messages over a network**.

That’s it. No shared RAM fairy.

## Basic Model

Process A  →  Network  →  Process B

Communication happens via:

- `send()`
    
- `receive()`
    

---

## Types of Message Passing

### 1️ Synchronous (Blocking)

Sender waits until:

- Message is received
    
- Or acknowledged
    

Like calling someone and waiting until they pick up.

Good for:

- Strong coordination
    

Bad for:

- Performance if network slow
    

---

### 2️  Asynchronous (Non-blocking)

Sender sends and moves on.

Like texting and not staring at “typing…”

Good for:

- Scalability
    
- Performance
    

But harder to reason about ordering.

---

## Communication Modes

- **Unicast** → one-to-one
    
- **Broadcast** → one-to-all
    
- **Multicast** → one-to-group
    

---

## Reliability Issues

Message passing faces:

- Loss
    
- Duplication
    
- Delay
    
- Reordering

---

### 2️⃣ Remote Procedure Call (RPC)

Allows a program to execute a procedure on a remote machine as if it were a local call.

This is very important. Very exam-friendly.

If they ask:  
“What is RPC?”

Write:

> RPC allows a process to invoke a procedure on a remote system transparently.

Use the word “transparently.” Professors like that.

---

# 3️⃣ Communication Protocols

A protocol defines rules for communication.

Most common layered model:

## OSI Model (conceptual)

7 layers:

1. Physical
    
2. Data Link
    
3. Network
    
4. Transport
    
5. Session
    
6. Presentation
    
7. Application
    

---

In practical distributed systems:

## TCP/IP Model

- Application
    
- Transport (TCP/UDP)
    
- Internet (IP)
    
- Network Access
    

TCP → reliable  
UDP → faster but unreliable

---
# IP Addressing

An IP address identifies a device on a network.

In IPv4:  
32 bits  
Example:

192.168.1.10

Now historically, IP was divided into **classes**.

---

# Classful IP Addressing

Old-school method. Rigid. Inefficient.

Addresses were divided into fixed classes:

---
**Not important - just give a read
## Class A

- Range: 1.0.0.0 to 126.255.255.255
    
- First octet = Network
    
- Remaining = Host
    
- Very large networks
    

---

## Class B

- Range: 128.0.0.0 to 191.255.255.255
    
- First 2 octets = Network
    

---

## Class C

- Range: 192.0.0.0 to 223.255.255.255
    
- First 3 octets = Network
    

---

### Why Classful Was Bad

If you needed:  
2000 hosts

Class C (max 254 hosts) → too small  
Class B (65,534 hosts) → way too big

Massive wastage.

Engineers looked at this and thought, we can do better.

---

# Classless IP Addressing (CIDR)

CIDR = Classless Inter-Domain Routing

Instead of classes, we use:

	IP / PrefixLength

Example:

	192.168.1.0/24

The `/24` means:  
First 24 bits = network

Remaining bits = host.

Now you can create:

- /30 (very small)
    
- /26
    
- /19
    
- /17
    

Flexible. Efficient. Logical.

---

# Example

Need 500 hosts?

You can choose:

/23 → 512 addresses

Perfect fit.

No waste like classful.


*****Not important ended

---

# Quick Comparison

|Feature|Classful|Classless (CIDR)|
|---|---|---|
|Fixed boundaries|Yes|No|
|Efficient|No|Yes|
|Used today|No|Yes|
|Flexible subnetting|No|Yes|

---
# Trends in DOS: 


# 1️⃣ Pervasive Networking Technology

“Pervasive” means networking is **everywhere**.

Earlier:

- Few isolated computers
    
- Limited connectivity
    

Now:

- Internet everywhere
    
- WiFi everywhere
    
- 5G everywhere
    
- Devices everywhere
    

Everything talks to everything.

This explosion of connectivity made Distributed OS not optional but necessary.

---

## What Enabled This?

- High-speed LANs
    
- Global Internet backbone
    
- Affordable routers
    
- Cloud infrastructure
    

Key internet backbone component:

## Internet Engineering Task Force

Sets standards like IP, TCP, etc.

---

## Role of Firewall

Now, if everything is connected, everything is also attackable.

So we use:

## Firewall

A firewall:

- Monitors incoming/outgoing traffic
    
- Applies security rules
    
- Blocks unauthorized access
    
- Allows trusted communication
    

In distributed systems, firewalls:

- Protect internal nodes
    
- Enforce access control
    
- Segment networks
    

Example:  
Company data center behind firewall  
Public internet outside

Without firewalls, distributed systems become distributed disasters.

---

### Exam line:

> Pervasive networking has enabled large-scale distributed systems, but requires security mechanisms like firewalls to protect internal resources.

---

# 2️⃣ Mobile and Ubiquitous Computing

Now humans decided computing shouldn’t sit politely on desks.

Computing became:

- Mobile
    
- Embedded
    
- Everywhere
    

Ubiquitous computing = computing embedded in everyday objects.

Phones.  
Smartwatches.  
IoT devices.  
Smart home systems.

Key enabler:

## Wi-Fi

## 5G

---

## Challenges in DOS due to Mobility

1. Devices move across networks
    
2. IP addresses change
    
3. Connectivity unstable
    
4. Limited battery power
    
5. Limited CPU power
    

So distributed systems must support:

- Dynamic reconfiguration
    
- Location tracking
    
- Handoff mechanisms
    
- Lightweight protocols
    

Classic example:  
You start streaming on WiFi → move → switch to mobile data → connection continues.

That’s distributed coordination.

---

### Ubiquitous Computing Concept

Proposed by:

## Mark Weiser

Idea:  
Computers disappear into background.  
Interaction becomes seamless.

Distributed OS must support:

- Context awareness
    
- Scalability
    
- Device heterogeneity
    

---

# 3️⃣ Distributed Multimedia Systems

Now let’s talk about streaming.

Multimedia = audio + video + graphics.

Distributed multimedia systems:

- Deliver media across networks
    
- Require timing guarantees
    

Example platforms:

## Netflix

## YouTube

---

## Why Multimedia Is Hard in DOS

Unlike text files, multimedia:

- Is time-sensitive
    
- Requires synchronization
    
- Needs continuous data flow
    

Problems:

- Latency
    
- Jitter
    
- Packet loss
    
- Bandwidth limits
    

If packets arrive late:  
Video stutters.

If audio desynchronized:  
Human brain gets annoyed instantly.

---

## Requirements of Distributed Multimedia Systems

1. High bandwidth
    
2. Real-time scheduling
    
3. QoS (Quality of Service) guarantees
    
4. Compression algorithms
    
5. Buffering techniques
    

Protocols used:

- RTP (Real-time Transport Protocol)
    
- Streaming over TCP
    

---

# Big Picture Summary

|Trend|Why It Matters|
|---|---|
|Pervasive Networking|Massive connectivity enabling distributed systems|
|Mobile & Ubiquitous|Devices everywhere, dynamic topology|
|Distributed Multimedia|Real-time data delivery challenges|

---

# Conceptual Flow

Networking everywhere →  Devices everywhere →  Media everywhere →  
System must handle scale, security, timing, mobility.

Distributed OS evolved because centralized computing simply couldn’t survive this explosion.

---

# 1️⃣ WAN – Wide Area Network

WAN connects computers over **large geographic areas**.

In Distributed OS context:  
If your nodes are globally distributed, you are operating over WAN.  
So latency becomes a design constraint.

---

# 2️⃣ LAN – Local Area Network

LAN connects computers within a **small geographic area**.


LAN is what most clusters and internal data centers run on.

In Distributed OS:

- Faster message passing
    
- Easier synchronization
    
- Lower communication cost
    

---

## Quick Comparison

|Feature|LAN|WAN|
|---|---|---|
|Area|Small|Large|
|Speed|High|Lower|
|Latency|Low|High|
|Ownership|Private|Public/Telecom|

---

# 3️⃣ Packet Switching vs Circuit Switching

This is fundamental network design philosophy.

Two very different mindsets.

---

## Circuit Switching

Old telephone system style.

A **dedicated communication path** is established before data transfer.

Think of it like booking an entire road lane for yourself.

Example:

## Public Switched Telephone Network

Process:

1. Establish connection
    
2. Reserve full bandwidth
    
3. Communicate
    
4. Release connection
    

Characteristics:

- Guaranteed bandwidth
    
- Fixed route
    
- No interference once established
    

Problem:  
If you’re silent, bandwidth is wasted.

---

## Packet Switching

Modern internet model.

Data is broken into packets.

Each packet:

- Can take different routes
    
- Shares network resources
    
- Is reassembled at destination
    

Used by:

## Internet Protocol

No dedicated path.

Packets compete for bandwidth.

Characteristics:

- Efficient resource usage
    
- Scalable
    
- No guaranteed timing
    

Problems:

- Delay
    
- Packet loss
    
- Reordering
    

---

## Why Distributed Systems Use Packet Switching

Because:

- Many nodes communicate dynamically
    
- Scalability matters
    
- Dedicated lines are impractical
    

The internet would collapse if we tried circuit switching for billions of devices.

---

# Final Comparison

|Feature|Circuit Switching|Packet Switching|
|---|---|---|
|Dedicated path|Yes|No|
|Efficient usage|No|Yes|
|Setup delay|Yes|No|
|Used in Internet|No|Yes|

# In One Clean Exam Line

> LAN provides high-speed communication over small areas, while WAN connects geographically distant systems. Modern distributed systems rely on packet switching networks, which divide data into packets and dynamically route them without reserving dedicated paths.


---

# 1️⃣ Baseline Physical Models

These describe how distributed systems evolved physically over time.

---

## (a) Early Distributed Systems

Era: 1970s–1980s

Characteristics:

- Few machines
    
- Connected by LAN
    
- Homogeneous systems
    
- Trusted environment
    

Example:  
University lab machines connected via Ethernet.

Main goal:

- Resource sharing
    
- Remote login
    
- File sharing
    

Security wasn’t the obsession yet because networks were closed.

---

## (b) Internet-Scale Distributed Systems

Era: 1990s–2000s

Explosion of:

## World Wide Web

Characteristics:

- Millions of nodes
    
- Open environment
    
- Heterogeneous systems
    
- Untrusted users
    

Challenges:

- Scalability
    
- Security
    
- Fault tolerance
    
- Global addressing
    

Now latency across continents became real.

---

## (c) Contemporary Distributed Systems

Current era.

Think:

- Cloud computing
    
- Edge computing
    
- Microservices
    
- IoT
    

Examples:

## Amazon Web Services

## Kubernetes

Characteristics:

- Massive scale
    
- Virtualization
    
- Containers
    
- Dynamic resource allocation
    
- Elastic scaling
    

System boundaries are fluid.  
Nodes appear and disappear constantly.

---

# Architectural Models – 3 Stage Approach

This is how we analyze system architecture properly instead of hand-waving.

---

## Stage 1: Core Underlying Architectural Elements

Basic building blocks:

- Processes
    
- Communication mechanisms
    
- Naming systems
    
- Coordination mechanisms
    

These define:  
Who exists?  
How do they talk?  
How are they identified?

This is foundational.

---

## Stage 2: Composite Architectural Patterns

Now we combine elements into patterns:

Common patterns:

- Client–Server
    
- Peer-to-Peer
    
- Multi-tier
    
- Service-Oriented Architecture
    
- Microservices
    

These are higher-level structural designs.

Instead of isolated components, we examine how they form meaningful system structures.

---

## Stage 3: Middleware Platforms

Middleware sits between OS and applications.

It provides:

- Communication abstraction
    
- Naming services
    
- Security services
    
- Transaction management
    

Examples:

## Remote Procedure Call

## Java RMI

Middleware hides distribution complexity.

Instead of writing raw socket code, developers use middleware APIs.

---

# Architectural Elements (Important)

Core elements typically include:

1. Processes or Objects
    
2. Communication channels
    
3. Interfaces
    
4. Coordination mechanisms
    
5. Data models
    

If they ask “What are architectural elements?”  
This is what you write.

---

# 3️⃣ Communicating Entities

Who exactly is communicating?

There are two perspectives.
The real difference lies in:

- What is visible
    
- What is abstracted
    
- What assumptions are made

---

## (a) System Perspective

From OS viewpoint:

Communicating entities are:

- Processes
    
- Threads
    
- Services
    
- Nodes
    

Focus:

- Addressing
    
- Ports
    
- Sockets
    
- Process IDs
    

Example:  
Process A sends message to Process B via TCP port.

System sees:  
Binary packets.  
Buffers.  
Network interfaces.

---

## (b) Programming Perspective

From developer viewpoint:

Entities are:

- Objects
    
- Components
    
- Services
    
- APIs
    

Example:  
Calling a remote method via RPC feels like:

```java
service.getData();
```

Programmer does NOT see:

- Packet routing
    
- Serialization
    
- TCP retransmission
    

Middleware abstracts it.

So:

System perspective = low-level communication  
Programming perspective = high-level abstraction

Same communication. Different mental layer.

# Clean Comparison Table

|Aspect|System Perspective|Programming Perspective|
|---|---|---|
|Unit of Communication|Bytes / Packets|Objects / Messages|
|Identity|IP + Port|Service name / Interface|
|Concern|Reliability, delay|Logic, workflow|
|Failure|Timeouts, crashes|Exceptions|
|Communication Tool|Sockets|RPC, API calls|

---
