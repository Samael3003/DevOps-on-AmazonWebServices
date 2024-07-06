# Networking on AWS

## What is Networking?

Networking connects computers globally, allowing communication between them. AWS has developed a network using data centers, Availability Zones, and Regions.

## Know the Networking Basics

Sending a digital message is similar to sending a letter, which involves three key pieces of information:
1. The payload (letter inside the envelope).
2. The sender's address.
3. The recipient's address.

In digital terms, the address must include:
- Name of sender and recipient
- Street
- City
- State or province
- Zip, area, or postal code
- Country

This is called routing in the digital world.

## What are IP Addresses?

To route messages correctly, each computer needs an IP address. An IP address, like a home address, ensures proper message delivery. It uses a combination of bits (0s and 1s).

### IPv4 Notation

Typically, IP addresses are shown in decimal format, known as IPv4 addresses. A 32-bit binary address is divided into 8-bit groups (octets) and converted to decimal format, separated by periods.

Example of a 32-bit address in binary format:
```
11000000.10101000.00000001.00011110
```
This is converted to decimal format as:
```
192.168.1.30
```

## Use CIDR Notation

CIDR (Classless Inter-Domain Routing) notation specifies a range of IP addresses. It helps to define network sizes efficiently.

Example of CIDR notation:
```
192.168.1.0/24
```
- The starting IP address is 192.168.1.0.
- The "/24" indicates that the first 24 bits are fixed, leaving 8 bits flexible.
- 8 flexible bits provide 256 IP addresses (2^8).

The range 192.168.1.0/24 is smaller than 192.168.1.0/16, as the number after the slash indicates the number of fixed bits. The more fixed bits, the smaller the range of IP addresses.

### CIDR Ranges on AWS

- Smallest IP range: /28 (16 IP addresses)
- Largest IP range: /16 (65,536 IP addresses)

## Resources

- [Stanford: Introduction to Computer Networking](https://stanford.edu/class/cs144/)
- [Ionos: CIDR: What is classless inter-domain routing?](https://www.ionos.com/digitalguide/server/know-how/cidr-classless-inter-domain-routing/)
