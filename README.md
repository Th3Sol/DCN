### 1. Amplitude Shift Keying (ASK) using Python

Tool: Scilab
```sci
clc;
bits = [1 0 1 1];
f = 5; fs = 1000;
t = linspace(0, 1, fs);
ask = [];

for i = 1:length(bits)
    if bits(i) == 1 then
        signal = cos(2*%pi*f*t);
    else
        signal = zeros(1, length(t));
    end
    ask = [ask, signal];
end

plot(ask); xtitle("ASK Modulated Signal");
```
output:

![image](https://github.com/user-attachments/assets/1af81a2a-27e1-4b83-aeeb-382bf4b7d4f6)

or python
```python
import numpy as np
import matplotlib.pyplot as plt

bit_stream = [1, 0, 1, 1, 0, 0, 1]
T = 1  # bit duration
fs = 1000
t = np.linspace(0, T, fs)
f = 5  # carrier frequency

ask_signal = []
for bit in bit_stream:
    if bit == 1:
        ask_signal.extend(np.cos(2 * np.pi * f * t))
    else:
        ask_signal.extend(np.zeros_like(t))

plt.plot(np.linspace(0, len(bit_stream), len(ask_signal)), ask_signal)
plt.title("ASK Modulation")
plt.xlabel("Time")
plt.ylabel("Amplitude")
plt.grid()
plt.show()
```

---



### 2. Crimping a Straight Cable (Universal Color Code)

Standard Color Order (EIA-568B – Both Ends):

1. White-Orange  
2. Orange  
3. White-Green  
4. Blue  
5. White-Blue  
6. Green  
7. White-Brown  
8. Brown

Tools: RJ-45 Connectors, Crimping Tool, Cable Tester
Steps:
Strip cable → Arrange wires in order → Insert into RJ-45 → Crimp → Test.



---



### 3. Time Division Multiplexing (TDM) – Python Simulation

Tool: MATLAB / Scilab
Concept: Combine multiple signals by allocating time slots.
```sci
clc;
t = linspace(0, 1, 500);
s1 = sin(2*%pi*5*t);
s2 = cos(2*%pi*5*t);

tdm = zeros(1, length(t));
for i = 1:length(t)
    if modulo(i, 2) == 0 then
        tdm(i) = s1(i);
    else
        tdm(i) = s2(i);
    end
end

plot(t, tdm); xtitle("Time Division Multiplexed Signal");

```
output:

![image](https://github.com/user-attachments/assets/d5da80ac-6b5e-454e-884e-2f80a224e957)

or python
```python
import numpy as np
import matplotlib.pyplot as plt

t = np.linspace(0, 1, 500)
signal1 = np.sin(2 * np.pi * 5 * t)
signal2 = np.cos(2 * np.pi * 5 * t)
tdm = []

for i in range(len(t)):
    if i % 2 == 0:
        tdm.append(signal1[i])
    else:
        tdm.append(signal2[i])

plt.plot(t, tdm)
plt.title("TDM Signal")
plt.show()
```

---



### 4. Create a Hybrid Network using Bluetooth
A hybrid network combines different types of connections – here we’ll use Bluetooth along with WiFi or Ethernet.

#### Steps:
1. **Turn on Bluetooth** on both devices (e.g., Laptop and Mobile).
2. **Pair the devices**:
   - On Windows: `Settings > Devices > Bluetooth & other devices > Add Bluetooth device`
   - On Android: `Settings > Bluetooth > Pair new device`
3. **Enable Bluetooth tethering** on the mobile (optional, for internet sharing):
   - Go to `Settings > Hotspot & Tethering > Enable Bluetooth tethering`
4. **On Laptop**:
   - Go to `Control Panel > Network and Sharing Center`
   - Enable **Bluetooth Network Connection** for internet sharing (optional)
5. **Hybrid Setup**:
   - One device (e.g., Laptop) uses **WiFi/Ethernet**
   - Other device connects via **Bluetooth** for file sharing and/or internet access
6. **File Sharing via Bluetooth**:
   - On sender device (e.g., Laptop):  
     Right-click file → `Send to > Bluetooth device` → Select paired device  
   - On receiver device: Accept the file when prompted  
   - ✅ File is transferred over Bluetooth successfully
  
<details>
    <summary></summary>
    Steps:
1. **Turn on Bluetooth** on two devices (e.g., Laptop and Mobile).
2. **Pair both devices** via Bluetooth.
   - On Windows: `Settings > Devices > Bluetooth & other devices`
3. **Enable Bluetooth tethering** on mobile:
   - Android: `Settings > Hotspot & Tethering > Bluetooth tethering`
4. **On Laptop**:
   - Go to `Control Panel > Network and Sharing Center`
   - Enable **Bluetooth Network Connection**
5. **Hybrid Setup**:
   - One device uses **WiFi/Ethernet**
   - Second connects through **Bluetooth**, sharing connection
    
---
    
Hybrid Setup Example:
Laptop connected to WiFi (Internet)
Bluetooth-connected speaker/mouse
Devices form a Hybrid (WiFi + Bluetooth) Network

No code needed. Configure in Settings → Network & Bluetooth.
</details>

---



### 5. Wireshark – Capture IP, TELNET, FTP Packets

Wireshark is a **packet sniffer** used to capture and analyze network packets.

#### Steps:
1. **Install Wireshark**
   - [Download from official site](https://www.wireshark.org/)
   - Install with **Npcap driver**

2. **Open Wireshark** and select active interface (usually WiFi or Ethernet)

3. **Start capturing packets**

4. **Filter Specific Protocols**:
   - IP Packets: `ip`
   - TELNET: `telnet`
   - FTP: `ftp`

5. **Observe Details**
   - Click a packet to view source, destination, protocol, flags, etc.

6. **Stop Capture** and optionally export the `.pcap` file

<details>
    <summary></summary>
Steps:
Open Wireshark → Start capture

Use filters:
IP: ip
TELNET: tcp.port == 23
FTP: tcp.port == 21

Use FTP/TELNET client to generate packets
</details>


---



### 6. Capture TCP and UDP Packets with Wireshark

TCP and UDP are transport layer protocols.

#### Steps:

1. **Open Wireshark** and start capturing

2. **Use Filters** to isolate packets:
   - For TCP: `tcp`
   - For UDP: `udp`

3. **Perform Sample Traffic**:
   - Open a webpage → generates **TCP**
   - Use DNS (e.g., `ping google.com`) → generates **UDP**

4. **Observe**:
   - TCP has 3-way handshake, reliable
   - UDP is faster but connectionless

5. **Analyze** the packet info: source port, dest port, flags, checksums

<details>
    <summary></summary>
Filters:
TCP: tcp
UDP: udp

Steps:

Start Wireshark
Run browser, ping, etc.
Use filters to isolate packet types
</details>

---



### 7. Install Operating System (Linux/Windows)

Steps to Install Linux (Ubuntu) in VirtualBox

1. Download Ubuntu ISO
From: https://ubuntu.com/download

2. Install VirtualBox
Download from: https://www.virtualbox.org

3. Create a New VM
Open VirtualBox → Click New
Name: Ubuntu
Type: Linux
Version: Ubuntu (64-bit)
RAM: At least 2048 MB

4. Attach ISO File
Go to Settings > Storage
Click Empty > Choose a disk file
Select the downloaded Ubuntu ISO

5. Start the VM
Click Start to boot the VM
Select "Install Ubuntu"

6. Follow Installer Prompts
Choose language, keyboard, updates
Select Erase Disk and Install (safe inside VM)
Create user credentials
Wait for installation to complete

7. Reboot the VM
Remove the ISO when prompted
Boot into your new Ubuntu system

Tutorial video: https://youtu.be/Hva8lsV2nTk?feature=shared

<details>
    <summary></summary>
Steps to Install Linux (e.g., Ubuntu)
    
1. Download ISO from ubuntu.com or any other linux distro

2. Create bootable USB using Rufus (Windows) or balenaEtcher

3. Insert USB and reboot PC

4. Enter BIOS/Boot Menu (F2, F12, Esc, or Del)

5. Select USB drive to boot from
6. Choose "Try or Install Ubuntu"
   
8. Follow on-screen instructions:
Set language, timezone
Partition disk (automatic/manual)
Create user

9. Click Install and wait for completion
10. Reboot after installation and remove USB

Steps to Install Windows Server (Optional)
1. Download ISO from microsoft.com
2. Use Rufus to make bootable USB
3. Boot via USB and follow install steps
4. Set language, disk partition, and user
5. Complete setup and reboot
</details>

---



### 8. Visit Computer Lab (Bus Topology)

a) Topology: Bus

b) Devices: Terminators (both ends), Coaxial cable backbone, Computers connected via T-connectors

c) Cables:Coaxial cable (RG-58) with BNC connectors, T-connectors and terminators


d) Applications: Chrome, VS Code, Packet Tracer

e) Layout:
Sketch a straight horizontal line representing the bus (coaxial cable).

---
OR
Visit Computer Lab (Star)

a) Topology: Star

b) Devices: Switch (D-Link), Router (TP-Link)

c) Cables: Cat5e/Cat6 – RJ-45

d) Applications: Chrome, VS Code, Packet Tracer

e) Layout: Sketch a star layout with Switch in center, PCs around

---



### 9. Implement Wireless Network
Wireless Network Setup:

1. Position Router – Place your wireless router in a central, open area for best coverage.

2. Turn Off Modem – Power off your modem before setup.

3. Connect Modem to Router – Use an Ethernet cable from modem to router’s WAN port.

4. Connect Computer to Router – Use another Ethernet cable from router's LAN port to your computer.

5. Power On Devices – Turn on modem, router, and computer in that order.

6. Access Router Settings – Open a browser and enter the router’s IP to access its settings.

7. Change Admin Login – Update the default username and password for better security.

8. Enable WPA2 Security – Choose WPA2 encryption and set a strong passphrase (8+ characters).

9. Set Network Name (SSID) – Rename your Wi-Fi to something recognizable.

10. Change Channel – Switch to a less crowded channel (1, 6, or 11) to avoid interference.

11. Install Wireless Adapter – If needed, install a wireless adapter and drivers on your computer.

12. Connect Devices – Search for your new Wi-Fi on all devices and connect.


<details>
    <summary></summary>
Steps:
Use WiFi Router → Enable DHCP
Connect laptop/phones
Check via ipconfig / ifconfig

Optional Testing:
Ping router IP
Access shared files via SMB
</details>

---



### 10. CRC Error Detection – C Code
```c
#include <stdio.h>
#include <string.h>
void xor(char *a, char *b, int n) {
  for (int i = 1; i < n; i++) a[i] = (a[i] == b[i]) ? '0' : '1';
}
void crc(char *data, char *key, char *rem) {
  char temp[50]; int k = strlen(key);
  strcpy(temp, data); strcat(temp, "000");
  strncpy(rem, temp, k);
  for (int i = 0; i < strlen(data); i++) {
    if (rem[0] == '1') xor(rem, key, k);
    memmove(rem, rem+1, k-1); rem[k-1] = temp[i+k];
  }
}
int main() {
  char data[50], key[20], rem[20];
  printf("Enter Data: "); scanf("%s", data);
  printf("Enter Key: "); scanf("%s", key);
  crc(data, key, rem); printf("CRC: %s\n", rem);
}
```
![image](https://github.com/user-attachments/assets/86912312-9d93-4cc4-b37b-2a52de335fbb)




---



### 11. Hamming Code – C Code
```c
#include <stdio.h>
int main() {
  int d[8], h[12]={0};
  printf("Enter 8 bits: ");
  for (int i=0; i<8; i++) scanf("%d", &d[i]);

  h[2]=d[0]; h[4]=d[1]; h[5]=d[2]; h[6]=d[3];
  h[8]=d[4]; h[9]=d[5]; h[10]=d[6]; h[11]=d[7];

  h[0]=h[2]^h[4]^h[6]^h[8]^h[10];
  h[1]=h[2]^h[5]^h[6]^h[9]^h[10];
  h[3]=h[4]^h[5]^h[6]^h[11];
  h[7]=h[8]^h[9]^h[10]^h[11];

  printf("Hamming: ");
  for (int i=0; i<12; i++) printf("%d", h[i]);
}
```

![image](https://github.com/user-attachments/assets/fd021d78-9445-4150-aa16-0a1ed8ac2a1c)

