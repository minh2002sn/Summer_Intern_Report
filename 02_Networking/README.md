# **Report Networking**

## **1. What is network?**
A network consists of 2 or more computers that are linked in order to share resource, exchange files, or allow electric communication.

The computers in the network may be linked through cables, telephone lines, radio waves, satellites, or infrared light beams.

There are 2 common types of networks:
- Local Area Network (LAN).
- Wide Area Network (WAN).

### **1.1. LAN (Local Area Network)**

A local area network (LAN) is a collection of devices connected together in one physical location, such as a building, office, or home. 

LAN comprises cables, access points, switches, routers, and other components that enable devices to connect to internal servers, web servers, and other LANs via wide area networks.

### **1.2. WAN (Wide Area Network)**

A wide-area network (WAN) is a collection of local-area networks (LANs) or other networks that communicate with one another.

WAN can connect devices in large geography areas.

### **1.3. OSI model**

The OSI Model (Open Systems Interconnection Model) is a conceptual framework used to describe the functions of a networking system.

The OSI model characterizes computing functions into a universal set of rules and requirements in order to support interoperability between different products and software.

In the OSI reference model, the communications between a computing system are split into seven different abstraction layers: Physical, Data Link, Network, Transport, Session, Presentation, and Application.

![01_osi_model](images/01_OSI_Model.png)

**Physical Layer**: 
- It is responsible for the actual physical connection between the devices, information in the form of bits and responsible for transmitting individual bits from one node to the next.
- When receiving data, this layer will get the signal received and convert it into 0s and 1s and send them to the Data Link layer, which will put the frame back together.
- The functions of physical layer:
    - **Bit synchronization**: Provide clock.
    - **Bit rate control**: define number of bits per sent second.
    - **Physical topologies**: Specify how the different devices are arranged in a network (i.e. bus, star, mesh topologies).
    - **Transmit mode**: Define that the transmission mode is simplex, half-duplex or full-duplex.

- Physical layer devices: hub, repeater, modem, cables.

**Data Link Layer:**

- The packet received from the Network layer is further divided into frames depending on the frame size of the NIC(Network Interface Card). DLL also encapsulates Sender and Receiver’s MAC address in the header. 

- The functions of data link layer:
    - **Framing**: Attach special bit patterns to the beginning and end of the set of bits received from network layer when transmitting data.
    - **Physical address**: Add physical address (MAC address) of sender and receiver in header of each frame.
    - **Error control**: Can detect and retransmit damaged or lost frames.
    - **Flow control**: The data rate must be constant on both sides else the data may get corrupted thus, flow control coordinates the amount of data that can be sent before receiving an acknowledgment.
    - **Access control**: When a single communication channel is shared by multiple devices, the MAC sub-layer of the data link layer helps to determine which device has control over the channel at a given time.

- Data Link layer is handled by the NIC (Network Interface Card) and device drivers of host machines. 
- The set of bits in data link layer is called Frame.
- Data link layer devices: switch, bridge, NIC (Network Interface Card).

**Network Layer**:
- Network layer protocol provides logical communication between hosts 
- The Functions of the Network Layer: 
    - **Routing**: Determine which route is suitable from source to destination.
    - **Logical Addressing**: To identify each device on Internetwork uniquely, the network layer defines an addressing scheme. The sender & receiver’s IP addresses are placed in the header by the network layer. Such an address distinguishes each device uniquely and universally.

- The set of bits in network layer is called Packet.
- Network layer devices (or networking devices): router.

**Transport Layer:**
- Transport layer protocol provides the logical communication between processes running on different hosts.
- The Functions of the Transport Layer:
    - **Segmentation and Reassembly**: This layer accepts the message from the (session) layer, and breaks the message into smaller units. Each of the segments produced has a header associated with it. The transport layer at the destination station reassembles the message.
    - **Service Point Addressing**: To deliver the message to the correct process, the transport layer header includes a type of address called service point address or port address. Thus by specifying this address, the transport layer makes sure that the message is delivered to the correct process.
- Services Provided by Transport Layer:
    - Connected-oriented Service.
    - Connectionless Service.
- Transport layer is operated by the Operating System. It is a part of the OS and communicates with the Application Layer by making system calls.
- Set of bits in is called Segment.
- Transport layer device: gateway.

**Session Layer:**
- This layer is responsible for the establishment of connection, maintenance of sessions.

- The Functions of the Session Layer:
    - **Session establishment, maintenance, and termination**: The layer allows the two processes to establish, use and terminate a connection.
    - **Synchronization**: This layer allows a process to add checkpoints that are considered synchronization points in the data. These synchronization points help to identify the error so that the data is re-synchronized properly, and ends of the messages are not cut prematurely and data loss is avoided.
    - **Dialog Controller**: The session layer allows two systems to start communication with each other in half-duplex or full-duplex.

**Presentation Layer:**
- The presentation layer is also called the Translation layer. The data from the application layer is extracted here and manipulated as per the required format to transmit over the network. 

- The Functions of the Presentation Layer: 
    - **Translation**: For example, ASCII to EBCDIC.
    - **Encryption/Decryption**: Encrypt the transmitting data and decrypt the received data.  
    - **Compression**: Reduces the number of bits that need to be transmitted on the network.

**Application Layer:**
- The layer which is implemented by the network applications.
- These applications produce the data, which has to be transferred over the network.
- This layer also serves as a window for the application services to access the network and for displaying the received information to the user. 

### **1.4. TCP/IP model**

- The TCP/IP model was developed prior to the OSI model. It is not exactly similar to the OSI model.
- There are 2 types of TCP/IP model: TCP/IP 4 layers and TCP/IP 5 layers.

**TCP/IP 5 layers model**

![02_tcpip_5_layers](images/02_TCPIP_5_layers.jpg)

- The TCP/IP 5 layers model incudes the application layer, transport layer, network layer, data link layer and physical layer.
- The first four layers are the same as OSI model.
- The last layer is the combination of 3 last layers of OSI model.

**TCP/IP 4 layers model**

![03_tcpip_4_layers](images/03_TCPIP_4_layers.webp)

- Same as TCP/IP 5 layers model, but the Network Interface Layer and Physical Layer are combined into 1 layer called Network Access Layer.

## **2. Transport layer**
### **2.1. What is transport layer**
- A transport-layer protocol provides for logical communication between application processes running
on different hosts.
- Transport-layer protocols are implemented in the end systems but not in network routers.
- There are a lots transport layer protocols, e.g. the Internet has 2 protocols: TCP and UDP.

### **2.2. Relationship Between Transport and Network Layers**
- Transport layer protocol provides the logical communication between processes running on different hosts.
- A computer network may make available multiple transport protocols, with each protocol offering a different service model to applications.
- Certain services can be offered by a transport protocol even when the underlying network protocol doesn’t offer the corresponding service at the network layer. E.g. reliable data transfer service, encryption to guarantee.

### **2.3. Transport layer in the Internet**
- The Internet makes two distinct transport-layer protocols available to the application layer:
    - UDP (User Datagram Protocol): Provide unreliable, connectionless service to the invoking application.
    - TCP (Transmission Control Protocol): Provide a reliable, connection-oriented service to the invoking application.
- UDP and TCP extend IP's delivery service (IP stands for Internet network layer protocol) such as extending host-to-host delivery to process-to-process delivery, it is called multiplexing and demultiplexing.
- UDP and TCP provide integrity checking by including error-detection field in thier segment's header.
- Like IP, UDP is an unreliable service, it does not guarantee that data sent by one process will arrive intact to the destination process.
- TCP provides several services:
    - Reliable data transfer by using flow control, sequence numbers, acknowledgements, timers.
    - Congestion control.

### **2.4. Transmission Control Protocol (TCP)**
#### **2.4.1. TCP header format**
- TCP header includes 28 bytes:

![04_tcp_head_format](images/04_tcp_header_format.png)

- **Source port (16 bits):** The source port number.
- **Destination port (16 bits):** The destination port number.
- **Sequence number (32 bits):**
    - The sequence number of the first data octet in this segment (except     when SYN is present). If SYN is present the sequence number is the initial sequence number (ISN) and the first data octet is ISN+1.
- **Acknowledge number (32 bits):**
    - If the ACK control bit is set this field contains the value of the next sequence number the sender of the segment is expecting to receive. Once a connection is established this is always sent.
- **Data offset (4 bits):**
    - The number of 32 bit words in the TCP Header.  This indicates where the data begins. The header (even one including options) is an integral number of 32 bits long.
- **Reserve (6 bits):** Reserve for future use, must be zero.
- **Control bit (6 bits):**
    - URG: Urgent pointer field significant.
    - ACK: Acknowledgment field significant.
    - PSH: Push function.
    - RST: Reset the function.
    - SYN: Synchronize sequence number.
    - FIN: No more data from sender.
- **Window (16 bits):**
    - The number of data octets beginning with the one indicated in the acknowledgment field which the sender of this segment is willing to accept.
- **Checksum (16 bits):**
    - Checksum the 1s complement of the sum of all the 16-bit words in the TCP segment and 12 bytes pseudo header, which are carried in the Internet Protocol.
    - At the receiver, all TCP segment and 12 bytes pseudo IP header are added, including checksum. If no errors are introduced into the packet, result will be 1111 1111 1111 1111.
- **Urgent pointer (16 bits):**
    - This field communicates the current value of the urgent pointer as a positive offset from the sequence number in this segment. The urgent pointer points to the sequence number of the octet following the urgent data. This field is only be interpreted in segments with the URG control bit set.
- **Options:**
    - Options may occupy space at the end of the TCP header and are a multiple of 8 bits in length.  All options are included in the checksum.  An option may begin on any octet boundary. There are two cases for the format of an option:
        - Case 1: A single octet of option-kind.
        - Case 2: An octet of option-kind, an octet of option-length, and the actual option-data octets.
    - The option-length counts the two octets of option-kind and option-length as well as the option-data octets.
    - Note that the list of options may be shorter than the data offset field might imply. The content of the header beyond the End-of-Option option must be header padding (i.e., zero).
    - A TCP must implement all options.
    - Currently defined options include (kind indicated in octal):

    | Kind | Length | Meaning               |
    |:----:|:------:|:---------------------:|
    |  0   |   -    |End of option list     |
    |  1   |   -    |No-Operation           |
    |  2   |   4    |Maximum Segment Size   |


    - Specific Option Definitions

        - End of Option List (0000 0000 - Kind = 0):
            This option code indicates the end of the option list. This might not coincide with the end of the TCP header according to the Data Offset field.  This is used at the end of all options, not the end of each option, and need only be used if the end of the options would not otherwise coincide with the end of the TCP
            header.

        - No-Operation (0000 0001 - Kind = 1)"
            This option code may be used between options, for example, to align the beginning of a subsequent option on a word boundary.
            There is no guarantee that senders will use this option, so receivers must be prepared to process options even if they do not begin on a word boundary.

        - Maximum Segment Size: (0x0204XXXX - Kind  = 2, Length = 4)

            - Maximum Segment Size Option Data: 16 bits.
                - If this option is present, then it communicates the maximum receive segment size at the TCP which sends this segment.
                - This field must only be sent in the initial connection request (i.e., in segments with the SYN control bit set). If this option is not used, any segment size is allowed.
- **Padding:**
    - The TCP header padding is used to ensure that the TCP header ends and data begins on a 32 bit boundary. The padding is composed of zeros.

### **2.5. User Datagram Protocol (UDP)**
User Datagram Protocol (UDP) is a Transport Layer protocol. UDP is a part of the Internet Protocol suite, referred to as UDP/IP suite. Unlike TCP, it is an unreliable and connectionless protocol. So, there is no need to establish a connection prior to data transfer. The UDP helps to establish low-latency and loss-tolerating connections establish over the network.The UDP enables process to process communication.
#### **2.5.1. UDP header format**

![05_udp_head_format](./images/05_udp_header_format.png)

- **Source port (16 bits):** The source port number.
- **Destination port (16 bits):** The destination port number.
- **Length (16 bits):** The length of segment including the UDP header and the data.
- **Checksum (16 bits):**
    - Checksum the 1s complement of the sum of all the 16-bit words in the TCP segment and 12 bytes pseudo header, which are carried in the Internet Protocol.
    - At the receiver, all TCP segment and 12 bytes pseudo IP header are added, including checksum. If no errors are introduced into the packet, result will be 1111 1111 1111 1111.