
### What are the two sublayers of the data-link layer as defined by the IEEE?
> The IEEE has subdivided the data-link layer into two sublayers: the logical link control (LLC) sublayer and the media access control (MAC) sublayer. The LLC sublayer handles flow control, error control, and part of the framing duties, while the MAC sublayer defines the specific access method for each LAN and takes care of addressing at the LAN technology level.ensuring that multiple nodes or stations can transmit data without conflicts.


### What is propagation delay and transmission delay, and how is it calculated?**
> **Propagation delay** is the time it takes for a bit to travel from point A to point B in the transmission media. It is calculated using the formula:
> `TP = Distance\Propagation speed ` 
> 
> **Transmission delay** is the time it takes for a sender to put all the bits of a packet onto the transmission medium. It is calculated using the formula:
> `Tt = Packet length(L)\Transmission rate or Bandwidth(B)= L/B `


### Explain MAC layers protocols.
> - The Medium Access Control (MAC) layer is a sublayer of the Data Link Layer (Layer 2) in the OSI model
> - When nodes or stations are connected and use a common link, we need a multiple-access protocol to coordinate access to the link. Many protocols have been devised to handle access to a shared link.
> - ![image](https://github.com/user-attachments/assets/6ebe328c-e219-4e4a-af28-9b7fea54f1b9)


### What are the key features of random access methods?

> - In this each device has an equal privilege to access the network and transmit data. These protocols allow nodes to send and receive data without taking turns or waiting for permission.
> - The main protocols used in random access methods include ALOHA, Slotted ALOHA, and CSMA (Carrier Sense Multiple Access). These protocols answer the following questions:
> - **Pure ALOHA** In this Each station sends data whenever it has data to send. After sending a frame, the station waits for an acknowledgment .If an acknowledgment is not received within a certain time frame (due to a collision), the station resends the frame after a random time.
> - **Slotted Aloha**  In this Time is divided into equal-sized slots that match the frame size. A station can only send a frame at the beginning of a time slot. If two or more stations attempt to send a frame in the same slot, a collision occurs, and each station waits a random number of slots before attempting to resend.
>   
>- **CSMA** Carrier Sense Multiple Access (CSMA) is a protocol where each station first senses the medium before transmitting. The vulnerable time for CSMA is the propagation time (Tp), during which a collision may occur if multiple stations try to send frames simultaneously.
> - **persistence methods** The different persistence methods in CSMA are:
> - **1-Persistent:** The station sends immediately after finding the line idle, which has a high chance of collision.
> - **Nonpersistent:** The station waits a random amount of time before sensing the line again if it is busy, reducing collisions but lowering network efficiency.
> - **P-Persistent:** The station sends with a probability \(p\) when the line is idle, and waits for the next time slot with probability \(1 - p\), combining advantages of the other two methods.
>
> -**CSMA/CD** In CSMA/CD, a station monitors the medium after sending a frame to detect collisions. If a collision is detected, the frame is retransmitted. The minimum frame size is important to ensure that collisions are detected before the entire frame is sent. The frame transmission time (Tfr) must be at least twice the maximum propagation time (2 x Tp) to detect collisions.
> - CSMA/CD is used in wired networks and relies on detecting collisions during transmission.
>
> - **CSMA/CA**
> - CSMA/CA is used in wireless networks and focuses on avoiding collisions before they occur. It is more complex but better suited for environments where collision detection is challenging.

### How does flow control And error control work in data communication?
> **Flow control:** Flow control prevents data overflow by using buffer memory in the receiving device. If the buffer is nearing capacity, the receiver communicates with the sender to reduce the number of frames sent or pause transmission temporarily, ensuring smooth data flow and preventing system overload.
>
> **Error control:** Error control involves error detection and correction, allowing the receiver to notify the sender about lost or damaged frames and facilitating their retransmission. In the data-link layer, error control is commonly implemented through Automatic Repeat Request (ARQ), where detected errors trigger the retransmission of specific frames to maintain data integrity.


### Explain bout Sliding Window protocols in CN?
> The Sliding Window Protocol is a method used in data link layer and transport layer protocols to ensure reliable transmission of frames or packets between two devices. It allows multiple frames to be in transit at the same time, improving the efficiency of data transfer. Here, we'll discuss three common types of Sliding Window Protocols: Stop-and-Wait ARQ, Go-Back-N ARQ, and Selective Repeat ARQ.
> 
> ### 1. Stop-and-Wait Automatic Repeat Request (ARQ)
> -  The sender sends one frame and waits for an acknowledgment (ACK) from the receiver before sending the next frame. If an ACK is not received within a certain time frame (timeout), the sender retransmits the frame. The receiver sends an ACK for each correctly received frame.
> -  it is Inefficient, as the sender must wait for an ACK for each frame before sending the next one.
> 

> ### 2. Go-Back-N Automatic Repeat Request (ARQ)
> - The sender can send multiple frames (up to a window size N) before needing an ACK.  The receiver keeps track of the sequence number of the next frame it expects.  If a frame is received out of order, it is discarded, and the receiver sends an ACK for the last correctly received frame. If an error is detected or a timeout occurs, the sender retransmits all frames from the last acknowledged frame.
> The advantage is that it is more efficient than Stop-and-Wait, as multiple frames can be in transit The disadvantage is that If an error occurs, all subsequent frames must be retransmitted, even if they were received correctly.
> 
> ### 3. Selective Repeat Automatic Repeat Request (ARQ)
>  - Similar to Go-Back-N, but the receiver can accept and buffer out-of-order frames The sender only retransmits the specific frames that were not acknowledged or were received in error. Both sender and receiver maintain a window of acceptable frame sequence numbers.

