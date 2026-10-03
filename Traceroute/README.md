# Practical 02 — Traceroute / Tracert

## Objective

To understand how network traffic travels from a source to a destination by using the `tracert` command to observe intermediate network hops.

---

## What is Traceroute?

**Traceroute** is a network diagnostic tool used to identify the path taken by network traffic from a source to a destination.

On different operating systems:

- **Windows:** `tracert`
- **Linux/macOS:** `traceroute`

Each device encountered along the path is called a **hop**.

### Basic Flow

```text
Source
  ↓
Hop 1
  ↓
Hop 2
  ↓
Hop 3
  ↓
  ...
  ↓
Destination
```

---

## Traceroute vs Ping

| Tool | Purpose |
|---|---|
| `ping` | Tests connectivity and measures response time |
| `tracert` | Shows the path and intermediate hops to a destination |

### Easy way to remember

```text
Ping       → Can I reach it?
Traceroute → What path does it take?
```

---

## Tools Used

- Windows PowerShell
- `tracert`
- Network diagnostic concepts
- IPv4 networking
- IPv6 networking

---

# Practical Tests

## 1. Trace Route to a Domain

### Command

```powershell
tracert google.com
```

### Purpose

To observe the network path from the computer to a destination domain.

### Observation

The trace completed successfully and displayed multiple network hops.

Some intermediate hops did not return a response, while later hops continued to respond.

---

## 2. Trace Route to a Public IP Address

### Command

```powershell
tracert 8.8.8.8
```

### Purpose

To observe the network path to a public IP address.

### Observation

The trace passed through multiple network hops before reaching the destination.

Some intermediate hops did not return responses, but the trace continued successfully to the destination.

---

## 3. Trace Route to the Local Computer

### Command

```powershell
tracert 127.0.0.1
```

### Purpose

To trace the route to the local computer using the IPv4 loopback address.

### Observation

The destination was reached directly with a single hop and a response time of less than one millisecond.

`127.0.0.1` is the standard IPv4 loopback address and refers to the local computer.

---

# Understanding a Tracert Result

A typical `tracert` result follows this format:

```text
Hop    Probe 1    Probe 2    Probe 3    Address
```

### Components

| Component | Meaning |
|---|---|
| Hop number | Position of the device in the route |
| Probe times | Response times for the probes |
| Address/hostname | Device responding at that hop |

---

# What is a Probe?

A **probe** is a test packet sent to a network device to check whether it responds and to measure its response time.

Traceroute uses multiple probes for each hop.

Example:

```text
1    2 ms    2 ms    2 ms
```

The three time values represent responses from three probes.

---

# What Does `ms` Mean?

`ms` means **milliseconds**.

```text
1 second = 1000 milliseconds
```

Network response times are commonly measured in milliseconds.

---

# What Does `* * *` Mean?

Example:

```text
*    *    *    Request timed out.
```

This means that the hop did not return a response to the traceroute probes.

A timeout does **not automatically mean that the network is broken**.

Possible reasons include:

- The device does not respond to traceroute probes.
- Network traffic may be filtered.
- The device may be configured not to respond.
- A temporary network condition may prevent a response.

If later hops respond and the destination is reached, a missing response at an intermediate hop does not necessarily indicate a routing failure.

---

# Important Commands

### Trace a Domain

```powershell
tracert google.com
```

### Trace a Public IP

```powershell
tracert 8.8.8.8
```

### Trace the Local Computer

```powershell
tracert 127.0.0.1
```

### Stop a Running Trace

```text
Ctrl + C
```

---

# Key Concepts

## Hop

A **hop** represents a network device encountered along the path to a destination.

## Probe

A **probe** is a test packet used to check a hop's response and measure its response time.

## Response Time

The time taken to receive a response from a probe, measured in milliseconds (`ms`).

## Loopback Address

`127.0.0.1` is the standard IPv4 loopback address and refers to the local computer.

## Timeout

A timeout means that no response was received from a hop within the expected time.

---

# What I Learned

- `tracert` is a Windows network diagnostic tool.
- Traceroute shows the path taken toward a destination.
- Each numbered entry represents a hop.
- Multiple probes are used to measure response times.
- Response time is measured in milliseconds.
- `* * *` indicates that a probe did not receive a response.
- A timeout at one hop does not necessarily mean that the entire route is broken.
- `127.0.0.1` represents the local computer.
- Traceroute can help with network troubleshooting and understanding network paths.

---

# Practical Evidence

The `screenshots` folder contains evidence of the traceroute exercises performed during this practical.

The screenshots have been redacted to avoid exposing personal information and local network details.

---

# Conclusion

This practical demonstrated how `tracert` can be used to examine the network path between a computer and different destinations.

The exercises covered:

- Network hops
- Probes
- Response time
- Timeouts
- Loopback networking
- Public network connectivity
- Basic network troubleshooting

Traceroute provides a foundation for further networking and cybersecurity topics such as **Nmap, Wireshark, network reconnaissance, and troubleshooting**.
