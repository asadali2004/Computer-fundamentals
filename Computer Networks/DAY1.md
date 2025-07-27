# Computer Networks: 3.1 Networking Basics

Computer networking forms the backbone of modern computing, enabling devices to communicate and share resources. To begin, let's explore some fundamental concepts, network models, topologies, and common network devices.

## 3.1.1 Important Definitions

Here are some key terms that form the vocabulary of computer networks:

- **Network**: A **collection of interconnected computers, servers, mainframes, network devices, and other devices** that are connected to one another for sharing resources and information.
- **Protocol**: A **set of rules and conventions that govern how data is transmitted and received** in a network. Protocols ensure that different devices can understand each other's communication.
- **IP Address**: A **numerical label assigned to each device** connected to a computer network that uses the Internet Protocol for communication. It serves two main functions: **host or network interface identification and location addressing**.
- **Router**: A networking device that **forwards data packets between computer networks**. It operates at the network layer of the OSI model.
- **Switch**: A networking device that **uses MAC addresses to forward data frames within a local area network (LAN)**. It operates at the data link layer of the OSI model.
*   **Firewall**: A **security device or software that monitors and controls incoming and outgoing network traffic based on predetermined security rules**. It acts as a barrier between a trusted internal network and untrusted external networks.
*   **Gateway**: A **network node that connects different networks**, translating protocols if necessary, to enable communication between them.
*   **Subnet**: A **logical subdivision of an IP network**. It allows network administrators to divide an IP address space into smaller, manageable segments for better organization and security.
*   **LAN (Local Area Network)**: A network that is **limited to a small geographic area, such as a single building or campus**. Devices in a LAN are typically connected at high data transfer rates.
*   **WAN (Wide Area Network)**: A network that **covers a broad area, such as a city, country, or even global connections**. WANs connect multiple LANs and use various technologies to transmit data over long distances.
*   **DNS (Domain Name System)**: A protocol used to **translate human-readable domain names into IP addresses**, facilitating the identification of resources on the internet.
*   **DHCP (Dynamic Host Configuration Protocol)**: A network protocol that **automatically assigns IP addresses and other network configuration information to devices on a network**.
*   **Packet**: A **unit of data that is transmitted over a network**. It consists of both the data being sent and control information, such as source and destination addresses.
*   **Bandwidth**: The **maximum rate at which data can be transmitted over a network**. It is often measured in bits per second (bps).
*   **Latency**: The **time delay between the initiation of a network request and the receipt of the corresponding response**. It is often measured in milliseconds (ms).
*   **OSI Model**: The Open Systems Interconnection model, a **conceptual framework that standardizes the functions of a communication system or network into seven abstraction layers**.
*   **TCP (Transmission Control Protocol)**: A **connection-oriented protocol that ensures reliable and ordered delivery of data** between devices.
*   **UDP (User Datagram Protocol)**: A **connectionless protocol that provides a simple and faster way to transmit data**, often used for real-time applications.
*   **MAC Address**: A **unique identifier assigned to network interfaces** for communications at the data link layer of a network segment.
*   **HTTPS (Hypertext Transfer Protocol Secure)**: A **secure version of HTTP that encrypts data exchanged** between a user’s web browser and the web server.
*   **FTP (File Transfer Protocol)**: A protocol used for **transferring files between computers** on a network.
*   **SSL/TLS (Secure Sockets Layer/Transport Layer Security)**: Protocols that provide **secure communication over a computer network**. TLS is the successor to SSL.
*   **ARP (Address Resolution Protocol)**: A protocol used to **map an IP address to a physical MAC address** in a local network.
*   **NAT (Network Address Translation)**: A technique that allows **multiple devices within a local network to share a single public IP address** for internet access.
*   **QoS (Quality of Service)**: A set of technologies and mechanisms to **manage network resources and ensure a certain level of performance for specific applications or users**.
*   **VoIP (Voice over Internet Protocol)**: A technology that enables **voice communication and multimedia sessions over the internet**.
*   **DNS Spoofing**: An attack where the attacker **provides false DNS responses to redirect a user to malicious websites**.
*   **Ping**: A network utility tool used to **test the reachability of a host** on an Internet Protocol (IP) network.
*   **Traceroute**: A network diagnostic tool used to **display the route and measure transit delays of packets** across an IP network.
*   **RIP (Routing Information Protocol)**: A dynamic routing protocol used to **exchange routing information within an autonomous system**.
*   **OSPF (Open Shortest Path First)**: A link-state routing protocol used to **find the best path for routing data packets** within an IP network.
*   **LAN Party**: A gathering of people with computers or compatible game consoles connected to a local area network for multiplayer gaming.
*   **VPN (Virtual Private Network)**: A **secure and encrypted connection established over the internet**, providing privacy and anonymity for users.
*   **802.11 (Wi-Fi)**: A set of standards for **implementing wireless local area networking (WLAN) communication**.
*   **SNMP (Simple Network Management Protocol)**: A protocol used to **manage and monitor network devices and their functions remotely**.
*   **PoE (Power over Ethernet)**: A technology that allows **electrical power to be transmitted over Ethernet cables**, eliminating the need for separate power cables for certain devices.
*   **IPsec (Internet Protocol Security)**: A suite of protocols that **secure internet protocol (IP) communications by authenticating and encrypting each IP packet** in a communication session.
*   **SMTP (Simple Mail Transfer Protocol)**: A protocol used for **sending and receiving email between servers**.
*   **IMAP (Internet Message Access Protocol)**: A protocol used by **email clients to retrieve emails from a mail server**.
*   **POP3 (Post Office Protocol version 3)**: A protocol used by **email clients to retrieve emails from a mail server**.
*   **Wireshark**: A popular network protocol analyzer for **capturing and analyzing packets** on a network.
- **DNS Cache Poisoning**: A type of cyber attack where **false DNS information is introduced into the cache of a DNS resolver**.
- **MTU (Maximum Transmission Unit)**: The **maximum size of a data packet that can be transmitted** over a network.
- **Proxy Server**: An **intermediate server that acts as a gateway between a local network and the internet**, forwarding requests and responses.
- **DDoS (Distributed Denial of Service)**: An attack in which **multiple compromised computers are used to flood a target system with traffic**, causing a denial of service for users.

---

## 3.1.2 OSI Model and TCP/IP Model

These are two prominent conceptual frameworks that describe how network communication works.

### 3.1.2.1 OSI Model vs. TCP/IP Model Comparison

The **OSI (Open Systems Interconnection) model** and the **TCP/IP model** are both layered architectures that describe network communication, but they differ in their number of layers and specificity.

| Aspect              | OSI Model                                                              | TCP/IP Model                                       |
| :------------------ | :--------------------------------------------------------------------- | :------------------------------------------------- |
| **Number of Layers** | **7 layers**                                                     | **4 layers**                                 |
| **Layer Names**     | Physical, Data Link, Network, Transport, Session, Presentation, Application | Link, Internet, Transport, Application       |
| **Presentation and Session** | Separately defined                                               | **Combined into the Application layer**      |
| **Protocols**       | Diverse set of protocols                                         | Primarily based on TCP/IP protocols         |
| **Development**     | Developed by ISO                                                 | Evolved from ARPANET and Internet development |
| **Specificity**     | More detailed and comprehensive                                  | **More practical and widely used**           |
| **Standardization** | International standard (ISO/IEC)                                 | **De facto standard for the Internet**       |

### 3.1.2.2 OSI Model: Layer-Wise Functioning

The OSI model breaks down network communication into seven distinct layers, each with specific functions:

1. **Application Layer (Layer 7)**:
   - **Provides network services directly to end-users or applications**.
   - Acts as an **interface between software applications and the network**.
   - Examples of protocols include **HTTP, FTP, and SMTP**.
   - Supports network management functions like user authentication and resource sharing.

2. **Presentation Layer (Layer 6)**:
   - **Responsible for data formatting, encryption, and compression**.
   - Ensures that data is presented in a readable format for the application layer.

3. **Session Layer (Layer 5)**:
   - **Manages communication sessions between applications**.
   - Establishes, maintains, and terminates connections.
   - Handles synchronization and dialogue control.

4. **Transport Layer (Layer 4)**:
   - **Divides data into segments for transmission and reassembles them** at the destination.
   - **Ensures efficient and reliable data transfer through flow control**.
   - **Detects and corrects errors** in transmitted data.
   - Provides **end-to-end communication services**.

5. **Network Layer (Layer 3)**:
   - **Assigns logical addresses (IP addresses) to devices** on the network.
   - **Determines the optimal path for data packets (routing)** to reach their destination.
   - **Forwards packets between different networks**.
   - Handles errors that may occur during packet transmission.

6. **Data Link Layer (Layer 2)**:
   - **Divides data into frames for transmission and adds frame headers and trailers**.
   - Performs **error detection and, in some cases, correction** during transmission.
   - **Manages access to the shared communication medium (MAC)**.
   - Responsible for flow control and managing the link through Logical Link Control (LLC).

7. **Physical Layer (Layer 1)**:
   - Deals with the **physical connection between devices** and the **transmission and reception of raw bitstreams** over a physical medium (e.g., cables, fibers).
   - Specifies details like voltage levels, data rates, and physical connectors.

### 3.1.2.3 TCP/IP Model: Layer-Wise Functioning

The TCP/IP model is a more practical, four-layer model widely used for internet communication:

1. **Application Layer (Layer 4)**:
   - Provides **network services directly to end-users or applications**.
   - Allows software applications to communicate over the network.
   - Includes protocols such as HTTP, FTP, and SMTP.
   - Supports network management functions, including user authentication and resource sharing.

2. **Transport Layer (Layer 3)**:
   - Provides **end-to-end communication services**.
   - **Manages the flow of data** to ensure efficient and reliable transfer (Flow Control).
   - **Detects and corrects errors** in transmitted data.

3. **Internet Layer (Layer 2)**:
   - **Handles logical addressing (IP addressing) and routing** of data packets.
   - Responsible for forwarding packets across networks.
   - **Key protocol: IP (Internet Protocol)**.

4. **Link Layer (Layer 1)**:
   - Combines the functionalities of the OSI model's Physical and Data Link layers.
   - Responsible for **physical transmission of data** and handling **data frames within a local network**.
   - Includes network interface cards (NICs) and device drivers.

---

## 3.1.3 Network Topologies

Network topology describes the **arrangement or physical layout of devices, nodes, links, and connections** within a computer network. It significantly impacts performance, reliability, scalability, and ease of maintenance.

### 1. Bus Topology
- **Description**: All devices share a **common communication medium (a single cable called a "bus")**. Data is transmitted to all devices, but only the intended recipient processes it.
- **Advantages**: Simple and easy to implement, cost-effective for small networks.
- **Disadvantages**: Limited scalability; performance degrades with more devices.
### 2. Star Topology
- **Description**: Each device is **connected to a central hub or switch**. All communication flows through this central point.
- **Advantages**: Centralized control, easy to add or remove devices, **fault isolation** (failure in one connection doesn't affect others).
- **Disadvantages**: Dependency on the central hub; if it fails, the entire network may be affected
### 3. Ring Topology
- **Description**: Devices are connected in a **closed loop**, with each device connected to exactly two others. Data circulates around the ring until it reaches the recipient.
- **Advantages**: Simple and easy to install, no central hub needed.
- **Disadvantages**: Failure of one device or connection can disrupt the entire network, scalability challenges.
### 4. Mesh Topology
- **Description**: **Every device is connected to every other device** in the network (full mesh) or only critical devices (partial mesh).
- **Advantages**: **High redundancy and fault tolerance**, no single point of failure.
- **Disadvantages**: Complex cabling and configuration, high cost and resource requirements.
### 5. Tree Topology
- **Description**: Combines star and bus topologies, arranging devices hierarchically with multiple levels connected through a central backbone.
- **Advantages**: Scalable, suitable for larger networks, easy to expand.
- **Disadvantages**: Dependency on the central backbone; its failure can affect connected networks.
### 6. Hybrid Topology
- **Description**: A **combination of two or more different topologies** (e.g., star-bus, star-ring).
- **Advantages**: Provides flexibility and customization to meet specific network requirements.
- **Disadvantages**: Complex to design and implement, requires careful planning.
### 7. Wireless Mesh Topology
- **Description**: Devices communicate wirelessly, forming a mesh network where each device can relay data for others, improving reliability and coverage.
- **Advantages**: Flexibility, easy to expand, resilient to node failures.
- **Disadvantages**: Limited by wireless range, potential for interference.

### 8. Point-to-Point Topology
- **Description**: A **direct connection between two devices**. Common in telecommunications and WANs.
- **Advantages**: Simple, efficient for connecting two locations directly.
- **Disadvantages**: Limited scalability, not suitable for large networks.

---

## 3.1.4 Network Devices

Network devices are physical or virtual components that **facilitate communication and data exchange**. They operate at various layers of the OSI model.

### 1. Router
- **Description**: Forwards data packets between computer networks. Operates at the network layer of the OSI model.
- **Functionality**: Routes data between different networks, performs Network Address Translation (NAT), and provides security features.

### 2. Access Point (AP)
- **Description**: A device that allows wireless devices to connect to a wired network using Wi-Fi. Crucial for wireless LANs.
- **Functionality**: Bridges the gap between wired and wireless networks, providing wireless connectivity.

### 3. Modem
- **Description**: Short for modulator-demodulator, it **converts digital data into analog signals for transmission over communication lines and vice versa**.
- **Functionality**: Enables digital devices to communicate over analog lines (e.g., telephone or cable TV connections).

### 4. Network Attached Storage (NAS)
- **Description**: A dedicated storage device or server connected to a network that **provides file-based data storage services** to other devices.
- **Functionality**: Allows centralized storage and sharing of files among connected devices on the network.

### 5. VPN Concentrator
- **Description**: A device that **creates and manages multiple VPN connections**, facilitating secure communication over the internet.
- **Functionality**: Aggregates and manages VPN connections, ensuring secure data transmission over public networks.

---

## 3.1.5 Network Protocols

Protocols define the rules for communication. Here's a table of well-known protocols and their associated ports and OSI layers:

| Protocol      | Port(s) | Description                                       | OSI Layer       |
| :------------ | :------ | :------------------------------------------------ | :-------------- |
| HTTP          | 80      | Hypertext Transfer Protocol                       | Application Layer |
| HTTPS         | 443     | HTTP Secure (TLS/SSL)                             | Application Layer |
| FTP (Control) | 21      | File Transfer Protocol (Control)                  | Application Layer |
| FTP (Data)    | 20      | File Transfer Protocol (Data)                     | Application Layer |
| SSH           | 22      | Secure Shell                                      | Application Layer |
| Telnet        | 23      | Telnet protocol                                   | Application Layer |
| SMTP          | 25      | Simple Mail Transfer Protocol                     | Application Layer |
| DNS           | 53      | Domain Name System                                | Application Layer |
| DHCP          | 67/68   | Dynamic Host Configuration Protocol               | Application Layer |
| SNMP          | 161/162 | Simple Network Management Protocol                | Application Layer |
| POP3          | 110     | Post Office Protocol version 3                    | Application Layer |
| IMAP          | 143     | Internet Message Access Protocol                  | Application Layer |
| RDP           | 3389    | Remote Desktop Protocol                           | Application Layer |
| TCP           | N/A     | Transmission Control Protocol                     | Transport Layer |
| UDP           | N/A     | User Datagram Protocol                            | Transport Layer |
| IP            | N/A     | Internet Protocol                                 | Network Layer |
| ICMP          | N/A     | Internet Control Message Protocol                 | Network Layer |
| ARP           | N/A     | Address Resolution Protocol                       | Data Link Layer |

**Ports** are logical endpoints used in networking to uniquely identify specific processes or services running on a host. They range from 0 to 65535.

- **Well-known Ports** (0 to 1023): Reserved for common services like HTTP (port 80) and HTTPS (port 443).
- **Registered Ports** (1024 to 49151): Registered for specific services by IANA upon request.
- **Dynamic/Private Ports** (49152 to 65535): Available for dynamic or private use, commonly used for temporary connections.

Ports are primarily used at the **transport layer** (Layer 4) of the OSI model for TCP and UDP communication. A **socket** is a combination of an IP address and a port number, representing the endpoint of a communication channel.
