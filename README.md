# PortScanner3.0
Unleash the power of lightning-fast port scanning with PortScanner3.0! This Python-powered beast is engineered to penetrate networks deeper, faster, and smarter than ever before. Say goodbye to ordinary scanners that choke on firewalls and trip over basic defenses. PortScanner3.0 is here to expose open ports and reveal hidden services like no other tool can.

🚀 Features
Blazing Fast Multithreaded Scanning: Scans multiple ports simultaneously using threads, slicing through targets with surgical precision.
Multi-Target Capability: Input one or multiple IP addresses—why limit yourself to just one when you can conquer them all?
Extensive Port Coverage: From common ports to the obscure, no port is safe. Customize the number of ports to scan to fit your mission.
Service Detection: Identifies services running on open ports with an extensive database of common ports and their associated services.
Real-Time Logging: Outputs results to a log file with timestamps, so you can analyze your findings at your leisure.
Future Enhancements: Plans to integrate advanced OS fingerprinting, service version detection, and stealth scanning techniques to bypass even the toughest defenses.
🛠 Requirements
Python 3.x
Socket Library (included with Python by default)
📝 Usage
Run the script directly from the command line:

bash
python port_scanner.py
Enter Targets To Scan:
Single target: 192.168.0.1
Multiple targets: 192.168.0.1, 8.8.8.8, 10.0.0.1
Enter How Many Ports You Want To Scan:
Specify the number of ports to scan starting from port 1. For example, entering 1000 scans ports 1 to 1000.
🔥 Example
Scan the first 1000 ports on multiple targets:
python port_scanner.py
[*] Enter Targets To Scan (split them by ,): 192.168.0.1, 8.8.8.8
[*] Enter How Many Ports You Want To Scan: 1000
Watch as PortScanner3.0 tears through the network, revealing open ports and associated services in real-time:
[+] Port 22 (SSH) is open on 192.168.0.1
[+] Port 80 (HTTP) is open on 8.8.8.8
...
🌐 Future Functionality
We're not stopping here. Our mission is to build the next Nmap on steroids:

Advanced OS Fingerprinting: Identify the operating system behind the IP.
Service Version Detection: Determine the exact version of the services running.
Stealth Scanning Techniques: Evade intrusion detection systems and firewalls.
Cloudflare Bypass Strategies: Innovate methods to map networks protected by services like Cloudflare.
Stay tuned as we push the boundaries of port scanning technology, making it faster, leaner, and more powerful for all your Red Teaming and network reconnaissance needs.

⚠️ Disclaimer
PortScanner3.0 is provided for educational purposes and authorized network security testing only. Unauthorized scanning of networks is illegal and unethical. Always obtain proper permission before engaging in any form of network scanning.

Join us in revolutionizing network scanning. Contribute, suggest features, or report issues. Let's make PortScanner3.0 the ultimate tool for network professionals and security enthusiasts alike.

Happy scanning!

Code Overview
Here's a brief rundown of what PortScanner3.0 brings to the table:

Multithreaded Scanning: Utilizes threading to perform multiple scans concurrently, significantly reducing scan time.
Comprehensive Port Descriptions: Includes an extensive list of common ports and their associated services for quick identification.
User-Friendly Input: Prompts for target IPs and port range, making it easy to customize your scan.
Logging Capability: Automatically logs scan results with timestamps to a file for later analysis.
Exception Handling: Gracefully handles exceptions and closed ports without interrupting the scan process.
Feel free to dive into the code, tweak it, and adapt it to your needs. Your contributions are welcome!

Code Snippet
import socket
import termcolor
import threading
import time

# Extensive list of common ports and their associated services
PORT_DESCRIPTIONS = {
    20: "FTP Data Transfer",
    21: "FTP Command Control",
    22: "SSH",
    23: "Telnet",
    25: "SMTP",
    53: "DNS",
    80: "HTTP",
    110: "POP3",
    143: "IMAP",
    443: "HTTPS",
    3389: "RDP",
    3306: "MySQL",
    8080: "HTTP Proxy",
    8443: "HTTPS Alt",
    27017: "MongoDB",
}

# Function to scan a specific port on a target
def scan_port(ipaddress, port, log_file):
    try:
        # Set up socket and connection timeout (3 seconds for more network stability)
        sock = socket.socket()
        sock.settimeout(3)
        sock.connect((ipaddress, port))
        
        # Retrieve service description if available
        service = PORT_DESCRIPTIONS.get(port, "Unknown Service")
        
        # Print open port with service description
        result_message = f"[+] Port {port} ({service}) is open on {ipaddress}"
        print(termcolor.colored(result_message, 'green'))
        
        # Log the result to the file
        with open(log_file, 'a') as f:
            f.write(result_message + "\n")
        
        sock.close()
    except:
        # Ignore closed ports silently
        pass

# Function to scan a range of ports on a target
def scan(target, ports, log_file):
    print('\n' + ' Starting Scan For ' + str(target))
    
    threads = []
    for port in range(1, ports + 1):
        thread = threading.Thread(target=scan_port, args=(target, port, log_file))
        thread.start()
        threads.append(thread)
    
    # Ensure all threads finish before the main script ends
    for thread in threads:
        thread.join()

# Main execution
if __name__ == "__main__":
    # Get target IPs and port range from the user
    targets = input("[*] Enter Targets To Scan (split them by ,): ")
    ports = int(input("[*] Enter How Many Ports You Want To Scan: "))
    
    # Create a log file with a timestamp
    timestamp = time.strftime("%Y%m%d-%H%M%S")
    log_file = f"port_scan_results_{timestamp}.txt"
    
    # Log the start of the scan
    with open(log_file, 'a') as f:
        f.write(f"Scan started at {time.strftime('%Y-%m-%d %H:%M:%S')}\n")
    
    # Check if multiple targets are specified
    if ',' in targets:
        print(termcolor.colored("[*] Scanning Multiple Targets", 'green'))
        for ip_addr in targets.split(','):
            scan(ip_addr.strip(' '), ports, log_file)
    else:
        scan(targets, ports, log_file)
    
    # Log the end of the scan
    with open(log_file, 'a') as f:
        f.write(f"Scan completed at {time.strftime('%Y-%m-%d %H:%M:%S')}\n")
Note: Always ensure you have explicit permission from the network owner before scanning any network or system. Unauthorized scanning can lead to legal consequences.
