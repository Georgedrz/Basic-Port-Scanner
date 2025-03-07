# Basic-Port-Scanner
 A simple cybersecurity tool that helps detect open ports on a target system using Python.

# Overview

# The Basic Port Scanner is a simple yet effective Python-based tool that scans for open ports on a target system. It utilises Python's socket library to establish connections and determine which ports are accessible. This is an essential tool for ethical hacking, penetration testing, and cybersecurity enthusiasts looking to understand network vulnerabilities.

# Features

Scans common ports (21, 22, 23, 25, 53, 80, 443, 3306, 8080).

Uses TCP connection requests to check for open ports.
 Implements a timeout feature to optimise scanning speed.

Lightweight and easy to use with minimal dependencies.

Fully customisable - users can modify the script to scan additional ports.


# Installation Instructions

# Prerequisites

Ensure you have Python 3 installed. You can check by running:

python --version

If Python is not installed, download it from Python's official website.

# Usage
 Running the Port Scanner

Once inside the project directory, run the following command: 

python port_scanner.py

Example Output: Enter target IP: 192.168.1.1
Scanning 192.168.1.1 for open ports...
Port 80 is open.
Port 443 is open.

# Code Explanation

The core functionality is built around Python's socket library:
import socket

def scan_ports(target, ports):
    print(f"Scanning {target} for open ports...")
    for port in ports:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)  # Set timeout for faster scanning
        result = sock.connect_ex((target, port))
        if result == 0:
            print(f"Port {port} is open.")
        sock.close()

if __name__ == "__main__":
    target_ip = input("Enter target IP: ")
    ports_to_scan = [21, 22, 23, 25, 53, 80, 443, 3306, 8080]  # Common ports
    scan_ports(target_ip, ports_to_scan)

# How It Works

Creates a socket using socket.AF_INET (IPv4) and socket.SOCK_STREAM (TCP). Attempts to connect to the specified ports using sock.connect_ex().

Checks the response: If the result is 0, the port is open. Otherwise, the port is closed or filtered.
Prints the results of the scan.

# Customization
You can modify the list of ports to scan additional ones:

ports_to_scan = range(1, 10000)  # Scans all ports up to 10,000

Or allow users to define a custom range:

start_port = int(input("Enter start port: "))
end_port = int(input("Enter end port: "))
ports_to_scan = range(start_port, end_port + 1)

# Security Considerations

# ⚠️ Ethical Use Only!

Ensure you have permission before scanning any system.

Unauthorised scanning of networks can violate legal regulations.

Use this tool only for learning, ethical hacking, or security testing on your own network.
