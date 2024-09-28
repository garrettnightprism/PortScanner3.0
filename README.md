# **PortScanner3.0**

Unleash the power of lightning-fast port scanning with **PortScanner3.0**! This Python-powered tool is engineered for network reconnaissance—deeper, faster, and smarter than ever. Say goodbye to ordinary scanners that choke on firewalls. **PortScanner3.0** exposes open ports and reveals hidden services like no other.

## 🚀 **Features**

- **Blazing Fast Multithreaded Scanning**: Scans multiple ports simultaneously for surgical precision.
- **Multi-Target Capability**: Scan one or more IP addresses—because why limit yourself?
- **Extensive Port Coverage**: Customize your scan range to fit your mission, from the most common ports to the obscure.
- **Service Detection**: Maps open ports to common services, helping you identify what's running.
- **Real-Time Logging**: Automatically logs scan results with timestamps for later analysis.

## 🛠 **Requirements**

- **Python 3.x**
- **Socket Library** (included with Python by default)
- **termcolor** (install via `pip install termcolor`)

## 📝 **Usage**

Run the script from the command line:

```bash
python port_scanner.py
Enter Targets: Single or multiple IP addresses, e.g., 192.168.0.1 or 192.168.0.1, 8.8.8.8, 10.0.0.1.
Enter Number of Ports to Scan: Specify the number of ports to scan, starting from port 1. For example, entering 1000 scans ports 1-1000.

🔥 Example

python port_scanner.py
[*] Enter Targets To Scan (split by ,): 192.168.0.1, 8.8.8.8
[*] Enter How Many Ports You Want To Scan: 1000

PortScanner3.0 will reveal open ports and the associated services in real-time:
[+] Port 22 (SSH) is open on 192.168.0.1
[+] Port 80 (HTTP) is open on 8.8.8.8

🌐 Future Functionality

Our goal is to build the next Nmap on steroids:

Advanced OS Fingerprinting: Identify the operating system behind the IP.
Service Version Detection: Find out what version of services are running.
Stealth Scanning: Evade firewalls and intrusion detection systems.
Cloudflare Bypass Strategies: Map networks protected by services like Cloudflare.

⚠️ Disclaimer

Unauthorized scanning of networks is illegal. Always obtain permission before scanning any system. 




