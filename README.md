# Practical 01 — Ping & ICMP

## Objective

To understand **ICMP (Internet Control Message Protocol)** and use the `ping` command for basic network connectivity testing, response-time analysis, packet-loss detection, and IPv4/IPv6 testing.

---

## What is ICMP?

**ICMP** is a network-layer protocol used for network error reporting and diagnostics.

The `ping` command uses ICMP **Echo Request** and **Echo Reply** messages to test whether a destination responds to network requests.

### Basic Flow

```text
My Computer
     |
     | ICMP Echo Request
     ↓
Destination
     |
     | ICMP Echo Reply
     ↓
My Computer
```

---

## Tools Used

- Windows PowerShell
- Ping
- ICMP
- IPv4
- IPv6

---

# Practical Tests

## 1. Basic Ping Test

### Command

```bash
ping google.com
```

### Purpose

To test basic connectivity to a domain and observe response time and packet loss.

### Result

- Packets Sent: 4
- Packets Received: 4
- Packet Loss: 0%
- Average Response Time: 39 ms

### Observation

The destination responded successfully with **0% packet loss**.

![Basic Ping](screenshots/ping-google.png)

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

The destination responded successfully with **0% packet loss**.

![Public IP Ping](screenshots/ping-public-ip.png)

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

> The actual local gateway address is intentionally not included in this README for privacy.

![Gateway Ping](screenshots/ping-gateway.png)

---

## 4. Specify the Number of Ping Requests

### Command

```bash
ping -n 5 google.com
```

### Purpose

The `-n` option specifies the number of Echo Requests to send.

### Result

- Requests Sent: 5
- Replies Received: 5
- Packet Loss: 0%
- Average Response Time: 30 ms

### Observation

Five ICMP requests were sent and all five received replies.

![Ping Count](screenshots/ping-count.png)

---

## 5. Specify Packet/Data Size

### Command

```bash
ping -n 5 -l 1024 google.com
```

### Purpose

To send 5 ping requests with a specified data size of **1024 bytes**.

### Result

- Requests Sent: 5
- Replies Received: 5
- Packet Loss: 0%
- Average Response Time: 34 ms

### Observation

All five requests received replies successfully.

![Packet Size](screenshots/ping-packet-size.png)

---

## 6. Continuous Ping

### Command

```bash
ping -t google.com
```

### Purpose

The `-t` option continuously sends ping requests until manually stopped.

### Result

The test received continuous replies with **0% packet loss** during the captured test.

The command was stopped using:

```text
Ctrl + C
```

### Observation

Continuous ping can be useful for monitoring network connectivity over a period of time.

![Continuous Ping](screenshots/ping-continuous.png)

---

## 7. Force IPv4

### Command

```bash
ping -4 google.com
```

### Purpose

To force the ping command to use **IPv4**.

### Result

- Packets Sent: 4
- Packets Received: 4
- Packet Loss: 0%
- Average Response Time: 18 ms

### Observation

The destination was successfully reached using IPv4.

![IPv4 Ping](screenshots/ping-ipv4.png)

---

## 8. Force IPv6

### Command

```bash
ping -6 google.com
```

### Purpose

To force the ping command to use **IPv6**.

### Result

- Packets Sent: 4
- Packets Received: 4
- Packet Loss: 0%
- Average Response Time: 21 ms

### Observation

The destination was successfully reached using IPv6.

![IPv6 Ping](screenshots/ping-ipv6.png)

---

## 9. Test an Unreachable Host

### Command

```bash
ping <unreachable-host>
```

### Result

The test produced:

```text
Request timed out.
100% packet loss
```

### Observation

No ICMP Echo Replies were received from the tested destination.

A timeout does not automatically prove that a host does not exist. The device could be offline, unreachable, or configured to block ICMP traffic.

> The actual local IP address used during testing is intentionally not included in this README for privacy.

![Unreachable Host](screenshots/ping-unreachable.png)

---

# Important Ping Options

| Option | Meaning |
|---|---|
| `-n` | Specifies the number of Echo Requests |
| `-l` | Specifies the data size of each request |
| `-t` | Continuously sends requests |
| `-4` | Forces IPv4 |
| `-6` | Forces IPv6 |

---

# Key Concepts

### Packet Loss

The percentage of packets that were sent but did not receive a response.

```text
0% loss   → All tested packets received replies
100% loss → No tested packets received replies
```

### Round-Trip Time (RTT)

The time taken for a request to travel to the destination and for the reply to return.

It is measured in milliseconds (`ms`).

### Default Gateway

The device, usually a router, that provides a path from the local network to other networks.

### Request Timed Out

This means that the computer did not receive an ICMP reply within the expected time.

---

# What I Learned

- `ping` is a basic network diagnostic tool.
- Ping uses **ICMP Echo Request and Echo Reply** messages.
- Ping can be used to test network connectivity.
- Ping results show packet loss and round-trip response time.
- `-n` controls the number of requests.
- `-l` specifies the data size.
- `-t` performs continuous pinging.
- `-4` forces IPv4.
- `-6` forces IPv6.
- A timeout does not automatically mean that a host does not exist.

---

# Conclusion

This practical demonstrated the use of **Ping and ICMP** for basic network diagnostics.

The tests covered:

- Network connectivity
- Public IP connectivity
- Gateway connectivity
- Packet count
- Packet size
- Continuous ping
- IPv4
- IPv6
- Packet loss and timeouts

These concepts provide a foundation for further cybersecurity and networking practicals such as **Nmap, Wireshark, network reconnaissance, and troubleshooting**.
