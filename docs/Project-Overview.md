# Project Overview

## Introduction

The **Home IT Lab** is a self-hosted infrastructure project designed to simulate a small enterprise IT environment using open-source technologies. The primary objective of this project is to gain practical experience in Linux system administration, containerization, networking, monitoring, documentation, and IT support by building and maintaining a production-inspired lab from the ground up.

Unlike tutorial-based projects, this lab is developed incrementally through versioned milestones. Each milestone introduces a new technology or operational concept while documenting the design decisions, challenges encountered, troubleshooting process, and lessons learned throughout the project.

---

# Objectives

The primary goals of this project are to:

* Develop hands-on Linux administration skills.
* Gain practical experience with Docker and Docker Compose.
* Learn to deploy and manage self-hosted applications.
* Understand networking concepts including port forwarding, Docker networking, and reverse proxies.
* Build familiarity with IT support tools such as osTicket.
* Practice documenting infrastructure and operational procedures.
* Create a professional portfolio project that demonstrates practical system administration and troubleshooting skills.

---

# Project Components

The Home IT Lab currently consists of the following services:

| Component     | Purpose                                            |
| ------------- | -------------------------------------------------- |
| Debian Server | Primary server operating system                    |
| Docker Engine | Container runtime for hosting services             |
| Nginx         | Web server and future reverse proxy                |
| Uptime Kuma   | Infrastructure monitoring and service availability |
| Wiki.js       | Internal documentation and knowledge base          |
| osTicket      | Help Desk and ticket management system             |
| MariaDB       | Database backend for osTicket                      |

Additional services and automation will be added as the project progresses.

---

# Technologies Used

## Operating System

* Debian Linux

## Containerization

* Docker
* Docker Compose

## Networking

* Docker Bridge Networks
* VirtualBox NAT Port Forwarding
* SSH

## Web Services

* Nginx
* Wiki.js
* Uptime Kuma
* osTicket

## Database

* MariaDB

## Version Control

* Git
* GitHub

## Documentation

* Markdown
* Draw.io (planned)

## Scripting (Planned)

* Bash
* Cron

---

# Skills Demonstrated

This project demonstrates practical experience with:

* Linux system administration
* User and permission management
* SSH configuration
* Docker container deployment
* Multi-container application orchestration
* Docker networking
* Persistent Docker volumes
* Service monitoring
* Help Desk deployment
* Infrastructure documentation
* Configuration management
* Technical troubleshooting
* Git version control

---

# Project Philosophy

This project follows an incremental, version-based development approach. Rather than building the entire environment at once, each feature is implemented as an individual milestone, tested, documented, and committed to version control before progressing to the next stage.

This methodology provides:

* A clear development history.
* Better documentation.
* Easier troubleshooting.
* Repeatable deployments.
* Continuous learning through practical implementation.

---

# Current Progress

Completed milestones:

* ✅ v0.1 – Debian Server Installation
* ✅ v0.2 – User Management & SSH Configuration
* ✅ v0.3 – Docker Installation
* ✅ v0.4 – Nginx Deployment
* ✅ v0.5 – Uptime Kuma Deployment
* ✅ v0.6 – Wiki.js Deployment
* ✅ v0.7 – osTicket Deployment using Docker Compose

Upcoming milestones include:

* Reverse Proxy Configuration
* Backup Automation
* Security Hardening
* Infrastructure Monitoring
* Bash Automation
* Production-style Documentation
* Final Home IT Lab Release (v1.0)

---

# Learning Outcomes

The Home IT Lab serves as a long-term learning platform for developing practical infrastructure skills through real-world deployment, configuration, troubleshooting, and documentation. Each milestone strengthens understanding of Linux administration, containerized applications, networking, automation, and operational best practices while producing a portfolio that reflects continuous technical growth.
