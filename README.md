*This project has been created as part of the 42 curriculum by erocha--.*

# NetPractice

## Description

NetPractice is a networking exercise that introduces the fundamentals of TCP/IP
addressing. The goal is to make several non-functioning small-scale networks work
correctly by configuring IP addresses, subnet masks, default gateways and routing
tables through a web-based training interface.

The project consists of 10 levels of increasing difficulty. Each level presents a
network diagram with one or more objectives (for example, "host A needs to communicate
with host C"). The task is to modify the editable (unshaded) fields until every
objective reports a successful status, meaning each packet reaches its intended
destination in both directions.

## Instructions

### Running the training interface

1. Download the archive attached to the project's page and extract it into any folder.
2. From that folder, run the launch script:

   ```
   ./run.sh
   ```

   This starts a local web server and opens the training interface in the default
   web browser.

3. If `run.sh` does not work, start the server manually and open the page yourself:

   ```
   python3 -m http.server 49242
   ```

   Then navigate to `http://localhost:49242` in the browser (the port number can be
   changed if needed).

A local web server is required because browser security constraints prevent the pages
from being served directly from the filesystem.

### Using the interface

- Enter your intranet login in the field on the welcome page so the configuration is
  generated for your account. Entering the login is required.
- Alternatively, the "Evaluation" tab generates a random configuration.
- For each level, modify the unshaded fields so the network functions correctly.
- Use **Check again** to verify whether the current configuration is valid.
- Use **Get my config** to export the configuration of the current level.
- When a level is solved, a **Next level** button appears to move on.

### Exporting configurations

Before moving to the next level, export the configuration with the **Get my config**
button. Each export produces one configuration file corresponding to that level.

### Submission requirements

- All work is evaluated from the Git repository.
- The 10 exported configuration files (one per level) must be placed at the root of the
  repository.
- File names must be checked carefully to ensure they are correct.
- During the defense, three random levels must be solved within a limited time, without
  external tools (a simple calculator such as `bc` is tolerated as the only exception).

## Resources

### Networking concepts studied

The project relies on understanding how addressing works in a network containing routers
and switches. The concepts involved are:

- **TCP/IP addressing** — the addressing system used across Internet and most networks,
  based on the Internet Protocol (IP) for addressing and routing, complemented by the
  Transmission Control Protocol (TCP) for reliable transport.
- **IP addresses** — 32-bit IPv4 addresses written as four octets (each 0–255).
- **Subnet masks** — the value that splits an address into a network part and a host
  part; the network address is obtained by a bitwise AND between the IP and the mask.
  Understanding CIDR notation (`/24`, `/25`, `/26`, etc.) and block sizes is central.
- **Network and broadcast addresses** — the first address of a block (all host bits 0)
  and the last (all host bits 1) are reserved and cannot be assigned to an interface.
- **Default gateways** — the exit point a host uses to reach destinations outside its
  own network; a gateway must belong to the same network as the interface using it.
- **Routers and switches** — a router operates at the network layer (OSI layer 3) and
  forwards packets between different networks; a switch operates at the data link layer
  (OSI layer 2) and connects machines within a single network.
- **Routing tables** — the set of `destination => gateway` entries that tell a device
  where to send packets, including the default route `0.0.0.0/0`.
- **OSI layers** — the seven-layer Open Systems Interconnection reference model; this
  project focuses on layer 3 (Network) addressing and routing.

### References

- TCP/IP model and IP addressing documentation.
- Subnetting and CIDR notation guides.
- OSI model reference (seven layers).
- Documentation on the role of routers, switches and default gateways.

### Use of AI

AI was used as a support tool during this project. Its use is documented here for
transparency:

- **Concept explanation** — clarifying subnet masks, the AND operation, block
  calculations for non-`/24` masks, the distinction between routers and switches, and
  the logic of routing tables and default gateways.
- **Log interpretation** — understanding the meaning of the training interface logs
  (for example `destination does not match any route`, `packet not for me`,
  `multiple interface match`, `no interface for gateway`, `invalid IP address`) in order
  to locate configuration errors.
- **Verification of reasoning** — checking calculations of network addresses, host
  ranges and gateway reachability.

All configurations were understood and validated personally. AI-generated explanations
were reviewed and, where relevant, confirmed with peers, in line with the project's
guidance on responsible AI use.