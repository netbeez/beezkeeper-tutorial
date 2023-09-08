# WiFi Monitoring

NetBeez is a valuable tool to collect network performance data needed to troubleshoot WiFi networks. Both NetBeez network and remote worker agents support WiFi metrics. The following table summarizes the features that each agent type supports.

| | Network Agent | Remote Worker Agent |
|---|---|---|
|Wi-Fi configuration|WiFi configuration (SSID profile) is done on the dashboard, then assigned to the agent|WiFi configuration is done on the laptop/desktop where the remote worker agent is running|
|Wi-Fi Metrics|Available|Available|
|SSID Scanning|Available|Available|
|Wi-Fi Hopping|Available|Not available|
|Wi-Fi Connection Timing|Available|Not available|

## WiFi Monitoring on network agents

NetBeez WiFi network agents are small hardware units equipped with an external 802.11ac dual-mode card. These units have two interfaces: the Ethernet one, which is only used to establish the control channel with the server, and the WiFi one, which is used to run tests for monitoring. A WiFi agent is not capable of running any monitoring on the Ethernet interface. Once the agent is connected to the SSID network via the WiFi interface, the Ethernet plug can be removed, if desired.

![](https://lh5.googleusercontent.com/e587gH16dfIvhqH2lq3D9x3Off7YcMBkccD5wYQqfRtmWWJb_giWHEJrOrn3MHgX9zeHYLrM8OuwvhHtC1wkRH7LYgIyZDd6MlVnezV0Jn1UCKkq-SJQZ02MV-8XppYXsOdEw72MikEqVZn5T2iX6dM)

### WiFi networks

WiFi network agents must be configured with the SSID to be monitored. For this reason, one or more WiFi networks can be configured on the dashboard and then assigned to the agents. A WiFi network is defined by the following information:

- Network name - This optional field is displayed on the dashboard;
    
- SSID - This required field is the name of the SSID to needs to be monitored;
    
- Description - This is a description of the WiFi network that will be displayed on the dashboard;
    
- Reconnection interval - This optional field defines how often the agents will reconnect to the SSID, testing and timing the connection process;
    
- Network verification test - This optional test will be run right after an agent is connected to an SSID;
    
- Band - The profile can be set to a specific band (optional);
    
- Security type - WiFi agents support the following security settings:
	- Open,
    
	- WEP,
    
	- WPA pre-shared key, 
    
	- WPA with EAP methodologies (also called Radius or 802.1x). 
    

![](https://lh5.googleusercontent.com/q_mg5IR8cSCnang9MqckFZ0reJHK4hGbLCESleu6k_gAw4C8w0jcvmR31c7yzQI09JTcH0XiPAp18O6b3et62cxoCwrIUm8LCdl1phaN3g7Qh58eQrLAQOVMgL5FVUMp5MrMWvZfebsOSijvCKQnmDk)

If you wish to learn more about this configuration, please check out [this documentation page](https://netbeez.zendesk.com/hc/en-us/articles/360006974412-Add-Edit-WiFi-Network).

#### WiFi metrics

A WiFi network agent reports the following WiFi metrics about the monitored network:

|Metric to be plotted|Data Type|
|---|---|

|TX/RX data on WLAN interface|Bps (number)|
|SSID|string up to 32 chars|
|BSSID|HEX string similar to MAC address (FF:FF:FF:FF:FF:FF)|
|Signal Strength (RSSI)|dBm|
|Link Quality|%|
|Bitrate|Mbps|
|Channel|Numerical value based on band|
| |       - 5GHz - between 7 and 196 |
| |       - 2.4 GHz - between 1 and 14 |
|Channel Frequency|GHz ([https://en.wikipedia.org/wiki/List_of_WLAN_channels](https://en.wikipedia.org/wiki/List_of_WLAN_channels))|

The WiFi metrics are available under an agent’s details view, in a separate tab labeled “WIRELESS”. Please refer to the following screenshot for more information.

![](https://lh3.googleusercontent.com/xilCLFTs5gpU-A99MjhfKHG_fyBrcKBTUOHgMw2a9peBkZRbaRlryV6vlF5Ng3cA4DTUVRZwgBwl_twVfdsJAn5_RtBcNEjVJsq-TT_k4klQp_P-LDNC6QG14RtMHtlSO5Bs_IuVWRMTF9hXIL6Vols)

### SSID scanning
A WiFi network agent can run scans of locally available wireless networks. Users can initiate a WiFi SSID scan within the wireless tab available. SSID scans are useful to find how many external SSID are using the same channels and perhaps causing more contention on certain frequencies.

An SSID scan reports the following information:

- SSID
    
- BSSID
    
- Signal strength
    
- Frequency
    
- Channel
    
### WiFi connection timing

If a WiFi network is configured with a reconnection interval, the WiFi agents assigned to it will periodically test and time the WiFi connection process. The WiFi connection process is divided into three phases:

1. Association with a BSSID (access point) in proximity
    
2. Authentication with the selected SSID
    
3. DHCP to obtain an IP address
    

![](https://lh5.googleusercontent.com/SRFm1et_RGb7Vz0KMyuGloiJwxVR3DeVuBBYL32tyeS3ZkjPwXMLm1yuy7iVEVCtENSe3M_rYRdY6UVGhUENg-jbV1nD7WqSiKORwwMDsW7ekYcWiBasWDkPvvL-msZt9cF6QAAGe1qJTU1QFpN8irs)

This feature is used to verify that a WiFi network can authenticate clients, and times the time that it takes for WiFi clients to connect and receive an IP address by the DHCP server.
### SSID hopping

SSID hopping enables a single NetBeez WiFi monitoring sensor to test up to four SSIDs by regularly connecting to each one of them. This feature enables enterprises to use one single sensor at each location to monitor all of their WiFi networks, without having to deploy one sensor for each SSID.

SSID hopping works by having WiFi sensors connect to the first SSID for a certain amount of time, called the “Hopping Interval”, then disconnect and connect to the next SSID for the same amount of time, and so on. At the end of the cycle, the WiFi sensors repeat the loop. At each hop, the WiFi sensors will monitor the targets they’ve been assigned to and will run any scheduled tests configured for. 

![](https://lh6.googleusercontent.com/d9-YzfY7Ar350BiER-O2KC-fkYbtHeqMze0J73DGzwWA0vTq5rZW2pBzwerViCWjn3BJE83kUmTm6i06QEGDQ_G98yzpgpmH6L3JskURyUNr5vu5FbIaErW6o0zY6Q2QiuImalb8b1QW07lq7uE80No)

The WiFi connection timing feature in this case is provided by the hopping mechanism itself. At each hop, the WiFi sensors test how long it takes to connect to the next SSID. If a WiFi sensor can’t authenticate, or get a DHCP address, within the “WiFi disconnection threshold”, it will trigger an alert. By default, the WiFi disconnection threshold is set to 60 seconds. This value can be updated in the [Anomaly detection](https://docs.google.com/document/d/1GsIWkWI3mMj2xqG0Ce_1BNrb8t8RhePK_bokT24sjo4/edit#heading=h.n6ogakcoekwr) (under the “Device alerts”) section of the NetBeez dashboard.

An agent that is hopping through two or more SSIDs will display as many copies of the same test as many SSID it’s monitoring. This is done to identify performance or connectivity issues on a per-SSID basis. For example, in the screenshot below the SSID “lab-test” is reporting performance issues on ping tests that the SSID “lab-test-guest” is not.

![](https://lh6.googleusercontent.com/tgqgp43ZYQQ0jTd9w8qJUwmDGG_7cZNq4hoLFdX2-B2MDREe5MY2R4BlPQtqUyqSt_KJBbJUfyfTCIGw158fPyivKabDXvnKD_Sno9YBKH0-N6v_kThfJ-AAhlMHjSd15ksH0MxYx2Nv1B0Ioz5ON8U)

#### Band hopping

To enable band hopping, create two separate WiFi networks with the same SSID. In the first WiFi network configuration, force the agents to connect to the 2.4 GHz. In the second one, force the agents to connect to the 5.0GHz band. Lastly, add the two SSID into a hopping group.

![](https://lh6.googleusercontent.com/3p4kgjh9uBRO0FNJpI16yLWa5HgqAG-nIgAQjoH8UPwz4XCQgxxj0ZBgOHBG6K-lPneSc3hcEtcFR0LqqzWFVhGBkPSTQJ3Wz71PqSpXosF47jMR2G6NonlLAmeCcq3ibS46NjG1YmhAlDJwTP4oy8w)

## WiFi monitoring on remote worker agents

NetBeez remote worker agents for Windows and Mac support the reporting of WiFi metrics in real-time to the dashboard. Similar to network agents, remote workers’ WiFi metrics are displayed in a separate tab within the details view.

  
  

![](https://lh5.googleusercontent.com/LEiS6FqYISxoOtkvE44mhcDkrisl5c1--T4VsZDL86F5rH5zh6MlZqGvnvCsP2bczrCC4cNxHLkEK4LhufKvZEng9sNagQj1APBFDMYwj4Qfe8FcKf-zqAMI2E8_E4dX5V5wflHEd8GjxvrxJYqiLHU)

Please keep in mind that the Windows and macOS operating systems don’t report the same data. The table below lists all the metrics available based on the operating system where the remote worker agent is running.

|Metric to be plotted|Data Type|Windows|macOS|
|---|---|---|---|
|TX/RX|Bps (number)|yes|yes|
|SSID|string up to 32 chars|yes|yes|
|BSSID|HEX string similar to MAC address (FF:FF:FF:FF:FF:FF)|yes|yes|
|Signal Strength (RSSI)|dBm|yes|yes|
|Noise|dBm|no|yes|
|Link Quality|%|yes|no|
|Bitrate|Mbps|yes|yes|
|Channel|Numerical value based on band |
| | - 5GHz - between 7 and 196|
| | - 2.4 GHz - between 1 and 14|yes|yes|
|Channel Frequency|GHz ([https://en.wikipedia.org/wiki/List_of_WLAN_channels](https://en.wikipedia.org/wiki/List_of_WLAN_channels))|yes|yes|
|[MCS](https://netbeez.net/blog/what-is-mcs-index/)|Value between 0 and 9|no|yes|

In both cases, the Wi-Fi metrics collected by the NetBeez agent are sent in real-time to the server. The data is then displayed on the user dashboard under an agent’s details view. The data is also stored in the database for historical review and is available based on the data retention period defined by the user.

NetBeez remote worker agents also report connection and disconnection events to the dashboard. This information is valuable in many cases as it tells the network support team when the user is connected or disconnected from the wireless network. 

Via the NetBeez dashboard the user can also perform an SSID scan to verify if any wireless networks in proximity are using the same channel and causing performance issues to the remote user. Here’s an example of an SSID scan.

### Wired Tests on WiFi Agents

WiFi sensors have the ability to run real-time tests on the ethernet interface. Wired tests on WiFi are enabled on a per-target basis. If enabled on a target with WiFi sensors assigned to it, those sensors will run that target's tests on the WiFi as well as the wired interface simultaneously. This feature is only available on the Network WiFi agents.

![](https://lh3.googleusercontent.com/_mSeatPRcLGcgPAJdRCUa5DLYRHreWevN4INWSYJQgNhkwkCKfjg_chLIioGvr4S9-2Aeio177zfqia6srI9kkDkL8RqFvzbGahbZlWrv2bwjoMeQmkVENijHGOqPsrr-kphf7FvK0kIVN-6Q1s6QGY)

### Packet Capture

Packet capture is available for WiFi sensors in the ad-hoc tab of the NetBeez dashboard. During this operation, the NetBeez sensor pauses real-time and scheduled tests for the duration of the packet capture process. At the end of the packet capture, you can download the captured frames in a pcap file for further analysis (using tools like Wireshark), while the sensor resumes its regular network monitoring operations.

![](https://lh6.googleusercontent.com/JWWuPrDiDpA-S3og0N40kBgz9CdNkAJkNO2GsU1awqHE-RE59HXb_mo7DKkppOzctZGC3B-vI7rwQpsk82PhXzXl9U5X3OE4wwsruqOeHM4l1dquqJWRpBqc69dA4_K4w8or1DTNtQ24kQC8lbFdo7I)
