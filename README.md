!/bin/bash

# Check Nmap is installed or not
if ! command -v nmap &> /dev/null
then
    echo "Nmap is not installed. Please install it and run the script again."
    exit 1
fi

# Check Nikto is installed or not
if ! command -v nikto &> /dev/null
then
    echo "Nikto is not installed. Please install it and run the script again."
    exit 1
fi

# Prompt for IP address
read -p "Enter the IP address to scan: " ip_address

# Perform Nmap scan
echo "Performing Nmap scan on $ip_address..."
nmap_scan_output=$(nmap -sV $ip_address)
echo "$nmap_scan_output"

# Perform Nikto scan
echo "Performing Nikto scan on $ip_address..."
nikto_scan_output=$(nikto -h $ip_address)
echo "$nikto_scan_output"

echo "All scans completed successfully."
