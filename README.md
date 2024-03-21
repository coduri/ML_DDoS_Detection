# DDoS Attacks Detection and Characterization
Internet security is one of the most important challenges, especially when the demand for
IT services is increasing every day. Among the many existing threats, DDoS (Distributed
Denial of Service) attack is a relatively simple but very effective technique to attack intranet
and Internet resources. Typically, this attack uses a large number of compromised machines
to prevent legitimate users from using web-based services. DDoS attacks can be carried out
at the network, transport and application layers using various protocols such as TCP, UDP,
ICMP, and HTTP.

By assuming that different DDoS attacks exhibit different traffic patterns, researchers
focused on the application of ML algorithms to detect and characterized such patters.
Indeed, the automatic detection of DDoS attacks can ease the network monitoring activity of
network administrators and allow to quickly take countermeasures.
The goal of this project is to develop a complete Machine Learning pipeline to automatize
the detection and analysis of flows generated during DDoS attacks solving two tasks: (i) one
supervised task, i.e., classification and (ii) one unsupervised task i.e., clustering. Through the
analysis of the results coming from the two tasks you should be able to identify and
characterize flows generated during a specific DDoS attack understanding, when possible,
the attack behaviors.

## Dataset
The provided dataset contains benign and the most recent common DDoS attacks that
resemble the real world data. It also includes the results of network traffic analysis using
CICFlowMeter-V3 (https://www.unb.ca/cic/research/applications.html#CICFlowMeter) with
labeled flows-based on timestamps, source and destination IPs, source and destination
ports, protocols and attacks. The dataset has been built replicating the behaviour of 25 users
based on the HTTP, HTTPS, FTP, SSH and email protocols.
In this dataset, you have different modern reflective DDoS attacks such as NetBIOS, LDAP,
MSSQL, UDP, UDP-Lag, SYN, NTP, DNS and SNMP. Attacks were subsequently executed
during the data acquisition period period.
The ground truth (GT) is made of the name of the attack a considered flow is referred to.
The provided dataset contains traffic traces collected during the execution of some of the most common DDoS attacks.

Each row is referred to a flow (sequence of packets exchanged between a source and a destination IP).

### Labels
The provided dataset is classified in 12 labels. 11 related to DDoS attacks (e.g., `ddos_ldap`, `ddos_udp`, ...).
The last one is `benign` and specifies that the labelled flow does not belong to any attack.

### Features Description
-   Flow ID: a unique identifier for each flow of network traffic in the dataset
-   Source IP: the IP address of the device or host that is sending the traffic
-   Source Port: the port number on the source device used for sending the traffic
-   Destination IP: the IP address of the device or host that is receiving the traffic
-   Destination Port: the port number on the destination device used for receiving the traffic
-   Protocol: the protocol used for the traffic, such as TCP, UDP, or ICMP
-   Timestamp: the time at which the traffic was recorded
-   Flow Duration: the duration of the traffic flow
-   Total Fwd Packets: the total number of packets sent from the source to the destination
-   Total Backward Packets: the total number of packets sent from the destination to the source
-   Total Length of Fwd Packets: the total length, in bytes, of the packets sent from the source to the destination
-   Total Length of Bwd Packets: the total length, in bytes, of the packets sent from the destination to the source
-   Fwd Packet Length Max: the maximum length, in bytes, of a packet sent from the source to the destination
-   Fwd Packet Length Min: the minimum length, in bytes, of a packet sent from the source to the destination
-   Fwd Packet Length Mean: the mean length, in bytes, of the packets sent from the source to the destination
-   Fwd Packet Length Std: the standard deviation of the lengths, in bytes, of the packets sent from the source to the destination
-   Bwd Packet Length Max: the maximum length, in bytes, of a packet sent from the destination to the source
-   Bwd Packet Length Min: the minimum length, in bytes, of a packet sent from the destination to the source
-   Bwd Packet Length Mean: the mean length, in bytes, of the packets sent from the destination to the source
-   Bwd Packet Length Std: the standard deviation of the lengths, in bytes, of the packets sent from the destination to the source
-   Flow Bytes/s: the rate at which bytes are transferred in the flow, in bytes per second
-   Flow Packets/s: the rate at which packets are transferred in the flow, in packets per second
-   Flow IAT Mean: the mean inter-arrival time of the packets in the flow, in seconds
-   Flow IAT Std: the standard deviation of the inter-arrival times of the packets in the flow, in seconds
-   Flow IAT Max: the maximum inter-arrival time of the packets in the flow, in seconds
-   Flow IAT Min: the minimum inter-arrival time of the packets in the flow, in seconds
-   Fwd IAT Total: the total inter-arrival time of the packets sent from the source to the destination, in seconds
-   Fwd IAT Mean: the mean inter-arrival time of the packets sent from the source to the destination, in seconds
-   Fwd IAT Std: the standard deviation of the inter-arrival times of the packets sent from the source to the destination, in seconds
-   Fwd IAT Max: the maximum inter-arrival time of the packets sent from the source to the destination, in seconds
-   Fwd IAT Min: the minimum inter-arrival time of the packets sent from the source to the destination, in seconds
-   Bwd IAT Mean: the mean inter-arrival time of the packets sent from the destination to the source, in seconds
-   Bwd IAT Std: the standard deviation of the inter-arrival times of the packets sent from the destination to the source, in seconds
-   Bwd IAT Max: the maximum inter-arrival time of the packets sent from the destination to the source, in seconds
-   Bwd IAT Min: the minimum inter-arrival time of the packets sent from the destination to the source, in seconds
-   Fwd PSH Flags: the number of packets sent from the source to the destination with the PSH flag set
-   Bwd PSH Flags: the number of packets sent from the destination to the source with the PSH flag set
-   Fwd URG Flags: the number of packets sent from the source to the destination with the URG flag set
-   Bwd URG Flags: the number of packets sent from the destination to the source with the URG flag set
-   Fwd Header Length: the total length, in bytes, of the headers of the packets sent from the source to the destination
-   Bwd Header Length: the total length, in bytes, of the headers of the packets sent from the destination to the source
-   Fwd Packets/s: the rate at which packets are sent from the source to the destination, in packets per second
-   Bwd Packets/s: the rate at which packets are sent from the destination to the source, in packets per second
-   Min Packet Length: the minimum length, in bytes, of a packet in the flow
-   Max Packet Length: the maximum length, in bytes, of a packet in the flow
-   Packet Length Mean: the mean length, in bytes, of the packets in the flow
-   Packet Length Std: the standard deviation of the lengths, in bytes, of the packets in the flow
-   Packet Length Variance: the variance of the lengths, in bytes, of the packets in the flow
-   FIN Flag Count: the number of packets in the flow with the FIN flag set
-   SYN Flag Count: the number of packets in the flow with the SYN flag set
-   RST Flag Count: the number of packets in the flow with the RST flag set
-   PSH Flag Count: the number of packets in the flow with the PSH flag set
-   ACK Flag Count: the number of packets in the flow with the ACK flag set
-   URG Flag Count: the number of packets in the flow with the URG flag set
-   CWE Flag Count: the number of packets in the flow with the CWE flag set
-   ECE Flag Count: the number of packets in the flow with the ECE flag set
-   Down/Up Ratio: the ratio of the number of packets sent from the source to the destination to the number of packets sent from the destination to the source
-   Average Packet Size: the average size, in bytes, of the packets in the flow
-   Avg Fwd Segment Size: the average size, in bytes, of the forward segments (i.e., packets sent from the source to the destination) in the flow
-   Avg Bwd Segment Size: the average size, in bytes, of the backward segments (i.e., packets sent from the destination to the source) in the flow
-   'Fwd Header Length.1': The length of the header in the forward direction of a network communication. The header is a part of a packet that contains information about the packet itself, such as its source and destination addresses, protocol, and other metadata. The "forward" direction refers to the direction of the communication from the sender to the receiver. 
-   'Fwd Avg Bytes/Bulk': The average number of bytes per bulk in the forward direction of a network communication. A bulk is a group of packets that are transmitted together as a single unit.
-   'Fwd Avg Packets/Bulk': The average number of packets per bulk in the forward direction of a network communication.
-   'Fwd Avg Bulk Rate': The average rate of bulk transmission in the forward direction of a network communication.
-   'Bwd Avg Bytes/Bulk': The average number of bytes per bulk in the backward direction of a network communication. The "backward" direction refers to the direction of the communication from the receiver back to the sender.
-   'Bwd Avg Packets/Bulk': The average number of packets per bulk in the backward direction of a network communication.
-   'Bwd Avg Bulk Rate': The average rate of bulk transmission in the backward direction of a network communication.
-   'Subflow Fwd Packets': The number of packets in the forward direction of a subflow of a network communication. A subflow is a separate channel within a larger communication flow that can be used to transmit data between two devices.
-   'Subflow Fwd Bytes': The number of bytes in the forward direction of a subflow of a network communication.
-   'Subflow Bwd Packets': The number of packets in the backward direction of a subflow of a network communication. The "backward" direction refers to the direction of the communication from the receiver back to the sender.
-   'Subflow Bwd Bytes': The number of bytes in the backward direction of a subflow of a network communication.
-   'Init_Win_bytes_forward': The initial window size (in bytes) in the forward direction of a network communication. The window size is a parameter that controls the amount of data that can be transmitted before an acknowledgement is required.
-   'Init_Win_bytes_backward': The initial window size (in bytes) in the backward direction of a network communication. The "backward" direction refers to the direction of the communication from the receiver back to the sender.
-   'act_data_pkt_fwd': The number of data packets in the forward direction of a network communication.
-   'min_seg_size_forward': The minimum size (in bytes) of a segment in the forward direction of a network communication. A segment is a unit of data that is transmitted between a sender and a receiver.
-   'Active Mean': The mean (average) value of the active time of a network communication. The active time is the amount of time that the communication is actively transferring data.
-   'Active Std': The standard deviation of the active time of a network communication. The standard deviation is a measure of the spread or dispersion of a set of values.
-   'Active Max': The maximum value of the active time of a network communication.
-   'Active Min': The minimum value of the active time of a network communication.
-   'Idle Mean': The mean (average) value of the idle time
-   'Idle Std': The standard deviation of the idle time of a network communication. The standard deviation is a measure of the spread or dispersion of a set of values. The idle time is the amount of time that the communication is not actively transferring data.
-   'Idle Max': The maximum value of the idle time of a network communication. The idle time is the amount of time that the communication is not actively transferring data.
-   'Idle Min': The minimum value of the idle time of a network communication. The idle time is the amount of time that the communication is not actively transferring data.
-   'SimillarHTTP': A measure of the similarity of the network communication to the HTTP protocol. HTTP (Hypertext Transfer Protocol) is a widely-used protocol for transmitting data over the internet, particularly for web browsing.
-   'Inbound': A binary value indicating whether the network communication is inbound (1) or outbound (0). An inbound communication is one that is directed towards the device, while an outbound communication is one that is initiated by the device.

> Written by Pietro Armenante, Christian Coduri, Eliana De Giuseppe and Luca Serafini.
