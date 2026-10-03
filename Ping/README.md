# Practical 01 — Ping & ICMP

## Objective

To understand **ICMP (Internet Control Message Protocol)** and use the `ping` command for basic network connectivity testing, response-time analysis, packet-loss detection, and IPv4/IPv6 testing.

---

## What is ICMP?

**ICMP (Internet Control Message Protocol)** is a network-layer protocol used for network error reporting and network diagnostics.

The `ping` command uses ICMP **Echo Request** and **Echo Reply** messages to test whether a destination responds.

### Basic Flow

```text
Computer
   |
   | ICMP Echo Request
   ↓
Destination
   |
   | ICMP Echo Reply
   ↓
Computer
```

---

## Tools Used

- Windows PowerShell
- Ping
- ICMP
- IPv4
- IPv6

---

# Practical Exercises

## 1. Basic Ping

### Command

```bash
ping google.com
```

### Purpose

To test connectivity to a domain and observe response time and packet loss.

### Result

- Packets Sent: 4
- Packets Received: 4
- Packet Loss: 0%
- Average Response Time: 39 ms

### Observation

The destination responded successfully with 0% packet loss.

---

## 2. Ping a Public IP Address

### Command

```bash
ping 8.8.8.8
```

### Purpose

To test connectivity to a public IP address.

### Result

- Packets Sent: 4
- Packets Received: 4
- Packet Loss: 0%
- Average Response Time: 18 ms

### Observation

The destination responded successfully with 0% packet loss.

---

## 3. Ping the Default Gateway

### Command

```bash
ping <default-gateway>
```

### Purpose

To test connectivity between the computer and the local network gateway.

### Result

- Packets Sent: 4
- Packets Received: 4
- Packet Loss: 0%

### Observation

The local gateway responded successfully to the ICMP requests.

> The actual local gateway address is not included in this documentation for privacy.

---

## 4. Specify the Number of Requests

### Command

```bash
ping -n 5 google.com
```

### Purpose

The `-n` option specifies the number of Echo Requests to send.

### Result

- Packets Sent: 5
- Packets Received: 5
- Packet Loss: 0%
- Average Response Time: 30 ms

### Observation

Five ICMP requests were sent and all five received replies.

---

## 5. Specify Packet Size

### Command

```bash
ping -n 5 -l 1024 google.com
```

### Purpose

To send five ping requests with a data size of 1024 bytes.

### Result

- Packets Sent: 5
- Packets Received: 5
- Packet Loss: 0%
- Average Response Time: 34 ms

### Observation

All five requests received replies successfully.

---

## 6. Continuous Ping

### Command

```bash
ping -t google.com
```

### Purpose

The `-t` option continuously sends ping requests until manually stopped.

### Result

The test received continuous replies with 0% packet loss during the captured test.

The test was stopped using:

```text
Ctrl + C
```

### Observation

Continuous ping can be useful for monitoring network connectivity over a period of time.

---

## 7. Force IPv4

### Command

```bash
ping -4 google.com
```

### Purpose

To force the ping command to use IPv4.

### Result

- Packets Sent: 4
- Packets Received: 4
- Packet Loss: 0%
- Average Response Time: 18 ms

### Observation

The destination was successfully reached using IPv4.

---

## 8. Force IPv6

### Command

```bash
ping -6 google.com
```

### Purpose

To force the ping command to use IPv6.

### Result

- Packets Sent: 4
- Packets Received: 4
- Packet Loss: 0%
- Average Response Time: 21 ms

### Observation

The destination was successfully reached using IPv6.

---

## 9. Test an Unreachable Host

### Command

```bash
ping <unreachable-host>
```

### Result

```text
Request timed out.
100% packet loss
```

### Observation

No ICMP Echo Replies were received from the tested destination.

A timeout does not automatically mean that a host does not exist. The device could be offline, unreachable, or configured to block ICMP traffic.

> The actual local IP address used during testing is not included in this documentation for privacy.

---

# Important Ping Options

| Option | Purpose |
|---|---|
| `-n` | Specifies the number of Echo Requests |
| `-l` | Specifies the data size of each request |
| `-t` | Continuously sends requests |
| `-4` | Forces IPv4 |
| `-6` | Forces IPv6 |

---

# Key Concepts

## Packet Loss

Packet loss is the percentage of packets that were sent but did not receive a response.

```text
0% loss   → All tested packets received replies
100% loss → No tested packets received replies
```

## Round-Trip Time

Round-trip time (RTT) is the time taken for a request to travel to the destination and for the reply to return.

It is measured in milliseconds (`ms`).

## Default Gateway

A default gateway is usually a router that provides a path from the local network to other networks.

## Request Timed Out

A timeout means that the computer did not receive an ICMP reply within the expected time.

---

# What I Learned

- Ping is a basic network diagnostic tool.
- Ping uses ICMP Echo Request and Echo Reply messages.
- Ping can be used to test network connectivity.
- Ping results provide packet-loss and response-time information.
- `-n` controls the number of requests.
- `-l` specifies the data size.
- `-t` performs continuous pinging.
- `-4` forces IPv4.
- `-6` forces IPv6.
- A timeout does not automatically mean that a host does not exist.

---

# Practical Evidence

Screenshots of the practical tests are stored in the repository as supporting evidence.

The evidence includes:

- Basic Ping
- Public IP Ping
- Gateway Ping
- Specified request count
- Custom packet size
- Continuous Ping
- IPv4 Ping
- IPv6 Ping
- Unreachable host test

---

# Conclusion

This practical demonstrated the use of **Ping and ICMP** for basic network diagnostics.

The exercises covered connectivity testing, packet loss, response time, packet size, continuous communication, IPv4, IPv6, and unreachable hosts.

These concepts provide a foundation for further cybersecurity and networking practicals such as **Nmap, Wireshark, network reconnaissance, and network troubleshooting**.

