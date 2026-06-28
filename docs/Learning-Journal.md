# Learning Journal

## Introduction

The Home IT Lab is more than a collection of self-hosted applications—it is a continuous learning project focused on developing practical Linux system administration and infrastructure management skills through hands-on experience.

This journal documents the concepts learned, challenges encountered, and technical knowledge gained throughout each stage of the project. Rather than simply recording completed tasks, it reflects the progression from understanding individual technologies to integrating them into a functional, production-inspired environment.

---

# v0.1 – Debian Server Installation

## What I Learned

* Installing and configuring a Debian Linux server.
* Understanding the differences between a desktop operating system and a server environment.
* Performing package updates using APT.
* Navigating the Linux filesystem.
* Basic Linux command-line usage.

## Key Takeaways

Setting up a clean server environment provided the foundation for every service deployed later in the project. A stable operating system is the starting point for reliable infrastructure.

---

# v0.2 – SSH Configuration & User Management

## What I Learned

* Creating and managing Linux users.
* Understanding file ownership and permissions.
* Configuring SSH for remote administration.
* Accessing the server securely from another machine.
* Performing administrative tasks remotely.

## Key Takeaways

Remote administration is a fundamental skill for Linux systems. Learning SSH demonstrated how servers are commonly managed without requiring physical access.

---

# v0.3 – Docker Environment

## What I Learned

* Difference between Docker images and containers.
* Pulling images from Docker Hub.
* Running containers.
* Publishing container ports.
* Persistent storage using Docker volumes.
* Basic Docker networking concepts.

## Key Takeaways

Docker simplifies application deployment by isolating services into lightweight containers while maintaining consistent environments.

---

# v0.4 – Nginx Deployment

## What I Learned

* Deploying a web server using Docker.
* Publishing services through port mapping.
* Verifying web server functionality.
* Understanding how browsers communicate with containerized applications.

## Key Takeaways

Nginx demonstrated how containerized web services can be exposed to users while remaining isolated inside Docker.

---

# v0.5 – Uptime Kuma

## What I Learned

* Deploying monitoring software.
* Configuring uptime monitors.
* Monitoring service availability.
* Understanding the importance of proactive infrastructure monitoring.

## Key Takeaways

Monitoring provides visibility into system availability and helps identify service failures before they become larger operational issues.

---

# v0.6 – Wiki.js

## What I Learned

* Deploying documentation software.
* Managing application setup.
* Creating an internal knowledge base.
* Understanding the importance of documentation in infrastructure projects.

## Key Takeaways

Technical documentation is as important as the infrastructure itself. Well-maintained documentation improves maintainability, troubleshooting, and collaboration.

---

# v0.7 – osTicket

## What I Learned

* Deploying a multi-container application using Docker Compose.
* Connecting an application to a MariaDB database.
* Using Docker networks for container communication.
* Managing Docker volumes for persistent storage.
* Understanding environment variables used during deployment.
* Reading container logs to diagnose deployment issues.
* Troubleshooting YAML syntax and configuration errors.

## Challenges Encountered

During deployment several issues were identified and resolved, including:

* Docker Compose YAML indentation errors.
* Incorrect Docker Compose structure.
* Environment variable mismatches.
* VirtualBox port forwarding configuration.
* Container communication issues.
* Database initialization and connectivity.

Each issue required reviewing logs, identifying the root cause, modifying configurations, and verifying the solution before continuing.

## Key Takeaways

Building a multi-container application demonstrated that deployment is only part of the process. Troubleshooting, log analysis, and iterative problem solving are equally important skills in Linux administration.

---

# Overall Skills Developed

Throughout the project I have strengthened practical knowledge in:

* Linux system administration
* Docker
* Docker Compose
* Container networking
* SSH
* User management
* Service deployment
* Infrastructure monitoring
* Database integration
* Documentation
* Configuration management
* Technical troubleshooting
* Git version control

---

# Lessons Learned

One of the most valuable lessons from this project has been that building infrastructure involves much more than following installation guides. Real-world deployments require patience, careful troubleshooting, reading documentation, interpreting logs, and continuously refining configurations until services operate reliably.

The project also reinforced the importance of documenting every major decision and maintaining a structured development process. Incremental improvements, consistent version control, and clear documentation make infrastructure easier to understand, maintain, and expand over time.

---

# Future Learning Goals

The next stages of the Home IT Lab will focus on expanding operational skills through:

* Reverse proxy configuration
* Automated backups
* Bash scripting
* Infrastructure automation
* Security hardening
* HTTPS deployment
* Firewall configuration
* Monitoring enhancements
* Disaster recovery procedures

These additions will further develop practical experience with production-inspired Linux environments and strengthen the overall architecture of the Home IT Lab.
