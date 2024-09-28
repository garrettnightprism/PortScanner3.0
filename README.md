PortScanner3.0 — Unleashing the Next Level of Network Reconnaissance
PortScanner3.0 is your lightweight, yet incredibly powerful Python tool designed to scan open ports across single or multiple targets. Built with precision and speed in mind, this script is perfect for anyone who needs to map network defenses in real-time. And don’t get comfortable—it’s only getting better from here. Future versions are planned to rival Nmap, with advanced techniques that push port scanning to the next level.

Requirements
To run this script, you need the following:

Python 3.x
The socket library (included with Python by default)
termcolor for colored terminal output (install via pip install termcolor)
Usage
Execute the script directly from the command line:

bash
python port_scanner.py

The script will prompt you for the following:

Targets: You can input a single target or multiple targets separated by commas, like so:

Single target: 192.168.0.1
Multiple targets: 192.168.0.1, 8.8.8.8, 10.0.0.1
Number of Ports to Scan: Input the number of ports to scan, and it will scan ports from 1 to the specified number.
