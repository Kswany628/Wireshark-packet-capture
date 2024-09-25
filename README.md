# Wireshark Packet Capture

## Objective

The packet capture Lab project aimed to establish a controlled environment for simulating Wireshark on Ubuntu. The primary focus was to capture packets, save them,and use filters. The IT manager in this scenario wants to be able to capture ethernet network web traffic on the server and be able to detect certain ip addresses.
### Skills Learned

- Start a packet capture on an ethernet port and save it.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

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



*Ref 1: Network Diagram*


