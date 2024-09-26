# Wireshark Packet Capture

## Objective

The packet capture Lab project aimed to establish a controlled environment for simulating Wireshark on Ubuntu. The primary focus was to capture packets, save them,and use filters. The IT manager in this scenario wants to be able to capture ethernet network web traffic on the server and be able to detect certain ip addresses.
### Skills Learned

- Start a packet capture on an ethernet port and save it.
- Proficiency in analyzing and interpreting network logs.
- Detect IP addresses using a display filter.
- Enhanced knowledge of network protocols.
- Use conditional statements to eliminate IP packets associated with an IP address from the display
- Using display filters to show only HTTP and HTTPS traffic.

### Tools Used
[Bullet Points - Remove this afterwards]

- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Network analysis tools (such as Wireshark) for capturing and examining network traffic.
- Telemetry generation tools to create realistic network traffic and attack scenarios.

## Steps
drag & drop screenshots here or use imgur and reference them using imgsrc

# Filter for wired connections
![image](https://github.com/user-attachments/assets/49c2058f-06db-4c75-a277-c5d8105bbf44)
The It manager requested they only want to view network traffic of wired connections.  Upon running Wireshark i use the interfaces drop down menu to filter for wired connections only.

# Initiating a packet capture
![image](https://github.com/user-attachments/assets/676fa8e1-6143-422d-803f-3521c522f80a)
I then click the eth0 as that ethernet adapter will include web visits in our packet capture.  Loopback:io is a machine sending packets back to itself so we wont be capturing this traffic. i then cick the blue fin to begin to initiate the capture.

# Save packet capture to a file after initiation
![image](https://github.com/user-attachments/assets/0ed5554f-928a-43d2-9775-ad30d8ef591f)
![image](https://github.com/user-attachments/assets/7718f1e3-ae3e-4764-a001-6029620e2d83)
Since the capture is now initiated, once i feel i have collected enough data i click the red stop button to stop the capture i then click the save capture button that is highlighted in the screen shot above.

# Using the display filter to show HTTPS traffic
![image](https://github.com/user-attachments/assets/97b67a34-e28a-4f00-8d25-d2a695bc7f1a)
The It manger in this scenario is asking for specficially web traffic. this capture is showing all packet captures in the moment in the above screenshot, going into the display filter field gives us the ability to filter for HTTPS traffic. since HTTPS and HTTP both use TCP we insert TCP.port == 443 to just show HTTPS since port 443 is used for HTTPS traffic.
![image](https://github.com/user-attachments/assets/ecd66752-a50b-4c5c-aa7d-924d49c81f92)
Now HTTPS traffic is only being shown for this capture file.

# Using the display filter to show HTTP traffic
![image](https://github.com/user-attachments/assets/bcbf6bc3-691d-4847-9f14-e073ee5a74e3)
Since the IT manager is asking for all web traffic i also will use the display filter to show HTTP traffic in this scenario using the TCP.port == 80 capture filter.

# Using display filter to search for all "client hello" in a TLS handshake in a capture
![image](https://github.com/user-attachments/assets/d8270c91-aa43-466d-840f-3e4f073b8ce2)

We want to find what websites a client is visiting. one method used is to use the tls.handshake.type == 1 display filter to show all client side http/s hello requests in the tls handshake. when the filter is applied we get the following result.
![image](https://github.com/user-attachments/assets/94660dc8-a125-42f6-9d5e-8969291b2b6d)

# Using a display filter to focus on a specific IP address
![image](https://github.com/user-attachments/assets/85465902-b940-4306-afcb-17acf4d59e87)
We want to show the IT manager specifically traffic that is associated with google.com. to do this we use the "ip.addr == 142.250.31.106". As we seen in the previous section with the destination IP address in the TLS handshake going to google.com was associated with the mentioned ip address. using this display filter gave us the follwing results:
![image](https://github.com/user-attachments/assets/82e20071-f92a-4517-b79f-8921985ca8b8)
You can now see that only web traffic associated with the specified IP address is being displayed. if i want to further filter this by showing the IP address as the source or destination i can change "addr" to "src" or "dst" respectively.

# Locate all HTTPS traffic from a capture not containing a certain IP address
![image](https://github.com/user-attachments/assets/b7b556bd-fc21-46e4-b008-3e8ffa425d6d)
The IT manager has now sepecified they do not want duck duck go to be displayed in packet captures to reduce clutter. in order to do this i used the "!" operator to exclude the ip address in the attached parenthesis then used "and" to combine multiple conditions. the next condition was the "(tcp.port == 443)" to show all HTTPS traffic, when applying the display filter this is the following result:

![image](https://github.com/user-attachments/assets/73436a20-d608-49cc-901c-54ae4c2cd669)
As you can see any packet information containing IP address 52.149.246.39 is not included in the current display filter.

*Ref 1: Network Diagram*


