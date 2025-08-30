# Introduction to Networking

Communication between two machines consists of:

- Protocol
- Frame

## Protocol

How to send data and interpret received data

Examples:

- SPI
- I2C
- UART
- Ethernet

## Frame

The data sent between machines organized according to the used protocol

## Internet Network Components

Communication between machines across the internet

For a client machine, communication occurs indirectly by connecting to a router, which handles communication with servers on the internet

The router sets up a **Local Area Network (LAN)** and organizes the machines connected to it. Each machine is uniquely identified by a **MAC address** and the router hands out an **IP address** to be bound to each MAC address which is derived from the **subnet address** of the LAN

# Network Stack

## Ethernet Protocol

An ethernet frame is divided as follows:

| 8B | 6B                      | 6B                 | 2B | 46 - 1500B             |
|----|-------------------------|------------------- |----|------------------------|
|    | Destination MAC Address | Source MAC Address |    | Packet data            | 

An ethernet frame is construced according to the **TCP/IP model**, which lives in the **Transport Layer** of the network stack (see the OSI model)

Let's say that an application on a client machine wants to send data to a server, it goes as follows:

1. The application requests a **TCP/UDP socket** from the kernel
2. The application writes the data to the socket + additional info like HTTPS data
3. The TCP/UDP layer writes the TCP/UDP frame data to the socket
4. The IP layer writes the IP addresses to the socket

💡 **Tip:** Use [wireshark](https://www.wireshark.org/) to inspect outgoing packets and learn how they are constructed

# Commands

- `ifconfig`: Configure network interfaces
- `nmap`: Network mapping
- `ss`: Socket investigation
- `ping`: Send and receive packets to a network address to check if there is a connection

# In-session Exercise

1. Activate network chip

```
ifconfig interface_name up
```

2. Scan all machines connected to your local network

```
nmap -sn 192.168.XXX.0/24
```

3. Ping one of these machines to see if there is a connection to it

```
ping -c 5 192.168.XXX.YYY
```

4. Access one of the machines using SSH

```
ssh machine_name@192.168.XXX.YYY
```

5. Check sockets opened through SSH

```
ss -tuln
```

6. Monitor frames using wireshark
