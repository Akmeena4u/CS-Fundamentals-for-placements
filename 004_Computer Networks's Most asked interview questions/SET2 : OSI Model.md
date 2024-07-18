

### What is OSI model in computer networking.
>- The OSI Model (Open Systems Interconnection Model) is a conceptual framework used to understand and describe how different networking systems communicate with each other. Created by the International Organization for Standardization (ISO) in 1984, the OSI Model divides the communication process into seven distinct layers. Each layer has a specific role, ensuring that different technologies and products can work together smoothly.
> - The OSI model consists of seven ordered layers. Each layer communicates with its adjacent layers, following specific protocols, to ensure efficient and reliable data transmission.
> -  Each layer communicates with its peer layer on another device, following standardized protocols.

### Explain 7 layers of OSI Model
> **1. Physical Layer**
> - **Definition:** The Physical Layer is the lowest layer of the OSI Model, concerned with transmitting raw bit streams over a physical medium.
> - **Function:** It manages the physical connection between devices, defining specifications such as voltage levels, pin layout, and physical medium characteristics (cables, fibers, wireless frequencies).
> - **Crucial Components:** Network hubs, repeaters, cables (twisted-pair, fiber-optic), connectors.
> - **Example Protocols:** Ethernet, RS-232, USB, HDMI.
> 
> **2. Data Link Layer**
> - **Definition:** The Data Link Layer provides error-free transfer of data frames between directly connected nodes.
> - **Function:** It packages raw bits into frames, adds physical addresses (MAC addresses), and detects/corrects errors that may occur at the Physical Layer.
> - **Crucial Components:** Switches, network interface cards (NICs), bridges.
> - **Example Protocols:** Ethernet (IEEE 802.3), Wi-Fi (IEEE 802.11), PPP (Point-to-Point Protocol).
> 
> **3. Network Layer**
> - **Definition:** The Network Layer handles logical addressing and routing of data packets from the source to the destination across different networks.
> - **Function:** It determines the best path for data to travel (routing) using logical addresses (IP addresses) and manages internetwork communication.
> - **Crucial Components:** Routers, IP addresses.
> - **Example Protocols:** IP (Internet Protocol), ICMP (Internet Control Message Protocol), ARP (Address Resolution Protocol).
> 
> **4. Transport Layer**
> - **Definition:** The Transport Layer ensures reliable data transfer between end systems and provides error-checking mechanisms.
> - **Function:** It segments and reassembles data into packets, manages data flow, and provides error detection/correction and sequencing.
> - **Crucial Components:** TCP ports, UDP ports.
> - **Example Protocols:** TCP (Transmission Control Protocol), UDP (User Datagram Protocol), SCTP (Stream Control Transmission Protocol).
> 
> **5. Session Layer**
> - **Definition:** The Session Layer establishes, manages, and terminates sessions (connections) between applications.
> - **Function:** It synchronizes dialogues between devices, manages session checkpoints, and handles session recovery.
> - **Crucial Components:** Session establishment protocols.
> - **Example Protocols:** NetBIOS (Network Basic Input/Output System), PPTP (Point-to-Point Tunneling Protocol), SIP (Session Initiation Protocol).
> 
> **6. Presentation Layer**
> - **Definition:** The Presentation Layer translates, encrypts, and formats data for the application layer.
> - **Function:** It ensures that data sent from the application layer of one system can be properly interpreted by the application layer of another system.
> - **Crucial Components:** Data compression standards, encryption/decryption protocols.
> - **Example Protocols:** SSL/TLS (Secure Sockets Layer/Transport Layer Security), JPEG (Joint Photographic Experts Group), ASCII (American Standard Code for Information Interchange).
> 
> **7. Application Layer**
> - **Definition:** The Application Layer provides network services directly to end-user applications.
> - **Function:** It allows access to network resources and supports application-level functions such as file transfers, email services, and remote access.
> - **Crucial Components:** Application-level protocols, APIs.
> - **Example Protocols:** HTTP (Hypertext Transfer Protocol), FTP (File Transfer Protocol), SMTP (Simple Mail Transfer Protocol), DNS (Domain Name System).
> 
> Each layer of the OSI Model plays a crucial role in ensuring effective communication and interoperability between different systems and networks. Understanding these layers helps in designing, troubleshooting, and optimizing network architectures and protocols.
> 
> - ![image](https://github.com/user-attachments/assets/0e6bc0b1-8c12-420e-a423-88f37816693f)
>


### Explain Data flows through the OSI model in a step-by-step process
> Application Layer: Applications create the data.
> Presentation Layer: Data is formatted and encrypted.
> Session Layer: Connections are established and managed.
> Transport Layer: Data is broken into segments for reliable delivery.
> Network Layer: Segments are packaged into packets and routed.
> Data Link Layer: Packets are framed and sent to the next device.
> Physical Layer: Frames are converted into bits and transmitted physically.



### Describe a comparison between the OSI model and the TCP/IP model.

| Parameters         | OSI Model                                                  | TCP/IP Model                                             |
|--------------------|-------------------------------------------------------------|----------------------------------------------------------|
| **Full Form**      | OSI stands for Open Systems Interconnection                 | TCP/IP stands for Transmission Control Protocol/Internet Protocol |
| **Layers**         | It has 7 layers                                            | It has 4 layers                                           |
| **Usage**          | It is less commonly used compared to TCP/IP                  | It is widely used, especially on the Internet            |
| **Approach**       | It is a vertically approached model                         | It is a horizontally approached model                    |
| **Delivery**       | Delivery of the package is guaranteed                      | Delivery of the package is not guaranteed                |
| **Replacement**    | Replacement of tools and changes can be done easily         | Replacing tools is not as easy as in the OSI Model       |
| **Reliability**    | It is generally considered less reliable                    | It is generally considered more reliable                 |
| **Protocol Examples** | Not tied to specific protocols, but examples include HTTP (Application), SSL/TLS (Presentation), TCP (Transport), IP (Network), Ethernet (Data Link) | HTTP, FTP, TCP, UDP, IP, Ethernet                         |
| **Error Handling** | Error handling is built into Data Link and Transport layers | Error handling is built into protocols like TCP          |
| **Connection Orientation** | Supports both connection-oriented (TCP) and connectionless (UDP) protocols at the Transport layer | TCP is connection-oriented, UDP is connectionless        |
>
>- ![image](https://github.com/user-attachments/assets/f4559caa-bc0f-483b-82f1-36a706906a7e)


