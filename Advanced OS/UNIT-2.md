
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

Now let’s properly structure this topic.

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

Processes communicate by sending and receiving messages.

No shared memory.

Used in distributed systems because machines do not share physical memory.

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
