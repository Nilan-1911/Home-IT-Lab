# Architecture

## Overview

The Home IT Lab is designed to simulate a small enterprise infrastructure using virtualization, Linux, Docker, and self-hosted services. The environment is built incrementally, with each component serving a specific operational purpose while demonstrating practical system administration concepts.

The architecture separates the host operating system from the server environment by running a Debian virtual machine inside VirtualBox. All infrastructure services are deployed as Docker containers, allowing applications to remain isolated, portable, and easy to maintain.

---

# Infrastructure Architecture

```
                         Arch Linux Host
                   (Development Workstation)
      ┌─────────────────────────────────────────────┐
      │                                             │
      │  • Browser                                  │
      │  • Git                                      │
      │  • GitHub                                   │
      │  • SSH Client                               │
      │                                             │
      └─────────────────────────────────────────────┘
                         │
                         │ SSH / HTTP
                         ▼
                VirtualBox NAT Network
                         │
                         ▼
             Debian Linux Virtual Machine
      ┌─────────────────────────────────────────────┐
      │                                             │
      │             Docker Engine                   │
      │                                             │
      │  ┌───────────────┐                          │
      │  │ Uptime Kuma   │                          │
      │  └───────────────┘                          │
      │                                             │
      │  ┌───────────────┐                          │
      │  │   Wiki.js     │                          │
      │  └───────────────┘                          │
      │                                             │
      │  ┌───────────────┐                          │
      │  │   osTicket    │────────────┐             │
      │  └───────────────┘            │             │
      │                               ▼             │
      │                     ┌─────────────────┐     │
      │                     │    MariaDB      │     │
      │                     └─────────────────┘     │
      │                                             │
      └─────────────────────────────────────────────┘
```

---

# System Components

## Arch Linux Host

The Arch Linux system acts as the primary development workstation. It is used for project documentation, Git version control, GitHub integration, SSH access, and administration of the Debian virtual machine.

Responsibilities include:

* Repository management
* Documentation
* Browser access
* SSH administration
* GitHub synchronization

---

## Debian Virtual Machine

The Debian virtual machine functions as the primary server within the lab. All production services are hosted inside this environment to simulate a dedicated Linux server.

Responsibilities include:

* Docker Engine
* Container management
* Network services
* Service monitoring
* Application hosting

---

## Docker Engine

Docker provides application isolation through containers. Each service operates independently while communicating over Docker's internal bridge network.

Current containers include:

* Uptime Kuma
* Wiki.js
* osTicket
* MariaDB

This architecture simplifies deployment, maintenance, and future expansion.

---

# Network Architecture

The virtual machine operates using VirtualBox NAT networking with port forwarding enabled for externally accessible services.

Communication flow:

```
Browser
      │
      ▼
Host Port
      │
      ▼
VirtualBox Port Forwarding
      │
      ▼
Debian Virtual Machine
      │
      ▼
Docker Bridge Network
      │
      ▼
Application Container
```

Container-to-container communication is handled through Docker's internal DNS resolution, allowing services to communicate using service names rather than IP addresses.

Example:

```
osTicket
     │
     ▼
MariaDB
```

using

```
MYSQL_HOST=mariadb
```

---

# Storage Architecture

Persistent application data is stored using Docker volumes rather than inside containers.

Current persistent storage includes:

| Volume           | Purpose                   |
| ---------------- | ------------------------- |
| osticket-db-data | MariaDB database files    |
| osticket-data    | osTicket application data |

Using Docker volumes ensures application data remains available even if containers are recreated.

---

# Service Communication

The current service relationships are shown below.

```
User
 │
 ▼
Web Browser
 │
 ▼
Docker Container
 │
 ├──────────────► Uptime Kuma
 │
 ├──────────────► Wiki.js
 │
 └──────────────► osTicket
                     │
                     ▼
                  MariaDB
```

---

# Security Considerations

Current security measures include:

* SSH remote administration
* Docker container isolation
* Internal Docker networking
* Persistent storage through Docker volumes

Future improvements will include:

* Reverse proxy
* HTTPS
* Firewall configuration
* Fail2ban
* SSH key authentication
* Automated backups

---

# Scalability

The architecture is intentionally modular. New services can be integrated by deploying additional Docker containers without impacting existing applications.

Future planned services include:

* Reverse Proxy
* Backup Automation
* Monitoring Dashboard
* Security Hardening
* Bash Automation Scripts

---

# Design Philosophy

The Home IT Lab is designed around the principles of modularity, documentation, and incremental development. Every infrastructure component is deployed, tested, documented, and version-controlled before introducing additional services.

This approach provides:

* Repeatable deployments
* Easier troubleshooting
* Simplified maintenance
* Clear project history
* Practical experience with production-inspired infrastructure
