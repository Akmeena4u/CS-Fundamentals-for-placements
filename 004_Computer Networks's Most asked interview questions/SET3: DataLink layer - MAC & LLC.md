
### What are the two sublayers of the data-link layer as defined by the IEEE?
> The IEEE has subdivided the data-link layer into two sublayers: the logical link control (LLC) sublayer and the media access control (MAC) sublayer. The LLC sublayer handles flow control, error control, and part of the framing duties, while the MAC sublayer defines the specific access method for each LAN and takes care of addressing at the LAN technology level.ensuring that multiple nodes or stations can transmit data without conflicts.


### What is propagation delay and transmission delay, and how is it calculated?**
> **Propagation delay** is the time it takes for a bit to travel from point A to point B in the transmission media. It is calculated using the formula:
> `TP = Distance\Propagation speed ` 
> 
> **Transmission delay** is the time it takes for a sender to put all the bits of a packet onto the transmission medium. It is calculated using the formula:
> `Tt = Packet length(L)\Transmission rate or Bandwidth(B)= L/B `

###  Can you explain the different framing techniques used in data communication?
> Framing is a crucial process in data communication that involves dividing a continuous stream of data into manageable units called frames. Each frame contains a portion of the data along with control information such as headers and trailers, which are used to ensure the correct interpretation and delivery of the data. Several framing techniques are used in data communication, each suited to different types of protocols and network environments. The main framing techniques include **Character Count**, **Byte Stuffing**, and **Bit Stuffing**.
> 
> 
> **1. Character Count**
> The Character Count method involves using a field at the beginning of each frame that indicates the total number of characters (or bytes) contained in that frame. This count includes both the data and any additional control information (like headers and trailers). When the receiver reads this field, it knows exactly how many characters to expect in that frame.
> 
> **Advantages:**
> - Simple and straightforward to implement.
> - Requires minimal additional overhead since the only extra information is the count field itself.
> 
> **Disadvantages:**
> - Vulnerable to errors: If the character count field is corrupted during transmission, the receiver may misinterpret the length of the frame, leading to loss of synchronization. 
> 
> **Example Use Case:**
> The Character Count method was commonly used in older, simpler protocols where the reliability of the physical layer was assumed to be high, and minimal overhead was desired.
> 
> 
> **2. Byte Stuffing**
> 
> **Explanation:**
> Byte Stuffing (also known as Character Stuffing) is used in byte-oriented protocols, where data is transmitted as a series of bytes. In this technique, special flag bytes are used to denote the start and end of each frame. A common flag might be a specific sequence like `01111110` (in binary) or a special character like `ESC` in text-based protocols. To ensure that the data within the frame does not accidentally contain the flag sequence (which could be misinterpreted as a frame boundary), the transmitter "stuffs" an extra byte (typically an escape character) before any occurrence of the flag byte within the data. The receiver then removes the stuffed byte upon receiving the frame.
> 
> **Advantages:**
> - Provides clear frame boundaries, which simplifies frame recognition.
> - Effective in differentiating data from control information, ensuring accurate data transmission.
> 
> **Disadvantages:**
> - Increases the amount of data transmitted (due to the additional stuffed bytes), which can be inefficient, especially if the data frequently contains the flag byte.
> - Can be complex to implement correctly, particularly in environments with diverse data types.
> 
> **Example Use Case:**
> Byte Stuffing is commonly used in protocols like **PPP (Point-to-Point Protocol)**, where it's essential to transmit data with clear boundaries between frames.
> 
> 
> 
> **3. Bit Stuffing**
> 
> **Explanation:**
> Bit Stuffing is used in bit-oriented protocols, where data is transmitted as a continuous stream of bits. In this technique, a specific bit pattern is used to mark the start and end of a frame. For example, a common bit pattern might be `01111110`. To prevent this pattern from appearing in the data portion and being mistaken as a frame boundary, the transmitter inserts (or "stuffs") an extra bit (usually a `0`) after any sequence of five consecutive `1` bits in the data. The receiver removes this stuffed bit to reconstruct the original data.
> 
> **Advantages:**
> - Minimizes overhead since only a single bit is added when necessary, making it more efficient than Byte Stuffing for binary data.
> - More flexible and can be used in any bit-oriented protocol, making it widely applicable across different types of networks.
> 
> **Disadvantages:**
> - More complex to implement compared to the Character Count and Byte Stuffing methods.
> - Can still introduce some overhead, though less than Byte Stuffing, especially in data streams with many consecutive `1` bits.
> 
> **Example Use Case:**
> Bit Stuffing is widely used in protocols such as **HDLC (High-Level Data Link Control)** and **CAN (Controller Area Network)**, where efficient and reliable data transmission is critical, and the communication is often in binary form.


### Explain MAC layers protocols.
> - The Medium Access Control (MAC) layer is a sublayer of the Data Link Layer (Layer 2) in the OSI model
> - When nodes or stations are connected and use a common link, we need a multiple-access protocol to coordinate access to the link. Many protocols have been devised to handle access to a shared link.
> - ![image](https://github.com/user-attachments/assets/6ebe328c-e219-4e4a-af28-9b7fea54f1b9)


### What are the key features of random access methods?

> - In this each device has an equal privilege to access the network and transmit data. These protocols allow nodes to send and receive data without taking turns or waiting for permission.
> - The main protocols used in random access methods include ALOHA, Slotted ALOHA, and CSMA (Carrier Sense Multiple Access). These protocols answer the following questions:
> - **Pure ALOHA** In this Each station sends data whenever it has data to send. After sending a frame, the station waits for an acknowledgment .If an acknowledgment is not received within a certain time frame (due to a collision), the station resends the frame after a random time.
> - In pure ALOHA, the vulnerable time is 2 times the frame transmission time (2 x Tfr).
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


### Explain all Sliding Window protocols in CN?
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





### Explain the Stop-and-Wait ARQ protocol, including how it handles corrupted and lost frames, the role of sequence numbers, and how various delays (propagation delay, transmission delay, queuing delay, processing delay) affect its performance. Additionally, describe how to calculate the total time for a complete cycle, the protocol's efficiency, and throughput.**
> 
> The Stop-and-Wait ARQ protocol is used for reliable data transmission by sending one frame at a time and waiting for an acknowledgment (ACK) before sending the next frame. It handles corrupted frames by discarding them and not sending an ACK, while lost frames are managed by retransmitting the frame if the ACK is not received within the timeout period. Sequence numbers (typically 0 and 1) help distinguish between new and retransmitted frames, ensuring proper frame order and handling duplicates.
> 
> Delays impacting performance include:
> - **Propagation Delay (Tp):** Time for a bit to travel from sender to receiver. Longer distances increase Tp.
> - **Transmission Delay (Tt):** Time to put all bits of a frame on the line, calculated as `Tt = L/B`, where  L is frame length and B  is bandwidth.
> - **Queuing Delay (Delayque):** Time spent waiting in router queues, generally minimal in Stop-and-Wait.
> - **Processing Delay (Delaypr):** Time to process the packet at the receiver, including error checking and forwarding.
> 
> -bThe total time for a cycle is:
> `Total Time = Tt(data) + Tp(data) + Tt(ack) + Tp(ack)`
> 
> - Efficiency `eta`is:
> `eta = Tt/Tt + 2*Tp = 1/1 + 2a where  a = Tp/Tt}`
> 
> - Throughput is calculated as:
> `Throughput= eta*B`
> 
> Higher efficiency indicates better utilization of the channel, with throughput showing the effective data rate achieved after accounting for protocol overheads.

### Describe the Go-Back-N ARQ protocol and explain how it improves upon Stop-and-Wait ARQ. Include details on the sliding window concept, sequence numbers, acknowledgment process, and how the window size and sequence number calculation contribute to its efficiency.
> 
> The Go-Back-N ARQ protocol enhances the Stop-and-Wait ARQ by allowing multiple frames to be sent before receiving acknowledgments, thus utilizing the channel more efficiently. It uses a sliding window concept where:
> - The **send window** covers a range of sequence numbers for frames that can be in transit, with a maximum size of `2^m - 1`.
> - **Sequence numbers** are divided into regions for acknowledged frames, outstanding frames, frames ready to be sent, and inaccessible frames.
> - The protocol uses a single timer for the first outstanding frame; if this timer expires, all frames in the window are resent.
> - The **receiver** sends positive acknowledgments for correctly received frames and remains silent (which causes a timeout) for corrupted or out-of-order frames, triggering a resend of all frames from the one with the expired timer.
> - **Cumulative acknowledgments** can be issued to improve efficiency by acknowledging multiple frames at once.
> 
> - The efficiency is maximized with a window size `Ws = 1 + 2a`, where `a` is the ratio of propagation delay to transmission delay. The number of bits required for sequence numbers is calculated as `ceil(log_2 (1 + 2a))`, allowing the protocol to handle multiple frames effectively.


### Explain the Selective Repeat ARQ protocol and how it differs from Go-Back-N ARQ. Discuss how it handles frame retransmissions, the management of data windows, and the role of timers in this protocol.**

> Selective Repeat ARQ improves upon Go-Back-N ARQ by focusing on retransmitting only the frames that are received incorrectly, rather than resending all frames from the point of error. This is particularly useful in unstable connections where minimizing retransmission can save time and bandwidth.
> 
> Key features include:
> - **Frame Management:** Selective Repeat ARQ allows the receiver to store out-of-order frames until they can be correctly reassembled and processed. This requires the receiver to maintain more complex buffering compared to Go-Back-N.
> - **Data Windows:** Both sender and receiver use small data windows, typically up to \(2^m - 1\), to manage frames efficiently. Each frame has its own timer, which allows more precise tracking of frame statuses.
> - **Retransmissions:** If a frame is received with errors, only that specific frame is retransmitted upon receiving a Negative Acknowledgment (NAK). On receiving an acknowledgment (ACK), the sender clears the acknowledged frame and adjusts the window's starting point.
> - **Timers:** Each frame has its own countdown timer, so only frames that time out are retransmitted, reducing unnecessary data retransmissions compared to Go-Back-N.
> 
> Selective Repeat ARQ thus balances the need for reliable transmission with efficiency, especially in environments with higher error rates.


### What is PiggyBacking
> **Piggybacking** refers to the practice of including acknowledgment (ACK) information along with data frames that are being sent from one party to another. Instead of sending an acknowledgment in a separate frame, the receiver waits until it needs to send its own data frame and includes the acknowledgment in this frame. This helps in optimizing the use of network resources and reducing the overhead caused by separate acknowledgment messages.



### What are the differences between single-bit errors and burst errors in data transmission, and how do they impact error detection and correction?
> - Single-bit errors involve the alteration of only one bit in a data unit, changing its value from 1 to 0 or vice versa. This type of error is less common and easier to detect and correct using simple error-detection mechanisms.
> - Burst errors, on the other hand, involve the alteration of two or more bits within a data unit, potentially in non-adjacent positions. Burst errors are more common due to noise and can be more challenging to detect and correct as they affect multiple bits simultaneously. Techniques like Hamming codes and cyclic redundancy checks (CRC) are often used to handle burst errors.

### Explain what Hamming distance is and how it is used to measure the difference between two binary strings. How do you calculate the Hamming distance between the binary strings 10101 and 11110?**
>  Hamming distance is a measure of the difference between two strings of equal length, calculated by counting the number of positions at which the corresponding bits are different. To calculate the Hamming distance between 10101 and 11110, perform an XOR operation on the two strings:
> 
> ```
> 10101
> 11110
> ------
> 01011 (result of XOR)
> ```
>
> Count the number of 1s in the result (which is 3), so the Hamming distance between 10101 and 11110 is 3.

### Describe the simple parity-check code and its purpose. How does it work, and what is its limitation in terms of error detection?
> - The simple parity-check code involves adding an extra parity bit to a k-bit dataword to form an n-bit codeword (where n = k + 1). This parity bit ensures that the total number of 1s in the codeword is either even or odd, depending on the parity scheme used. This method can detect single-bit errors because any change in a single bit will result in an incorrect parity.
> - However, it cannot detect or correct multiple-bit errors effectively, as multiple errors can cancel each other out and still result in a valid parity.

### How does the two-dimensional parity-check method work to detect errors in data transmission? What are its limitations?
> -In the two-dimensional parity-check method, data is arranged in a matrix with parity bits added to both rows and columns. The receiver checks these parity bits to identify "syndromes" indicating possible errors.
> - This method can detect up to three errors but may not reliably detect errors if four or more bits are corrupted, as the syndromes might not always clearly indicate the exact location of the errors.

