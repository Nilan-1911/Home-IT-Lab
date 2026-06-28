# Troubleshooting Guide

## Overview

Building the Home IT Lab involved deploying multiple self-hosted services across a Debian virtual machine using Docker and Docker Compose. During development, several configuration, networking, and deployment issues were encountered and resolved.

This document records the most significant problems, their root causes, and the solutions that were implemented. The objective is to provide a reference for future troubleshooting while demonstrating a structured problem-solving approach.

---

# Docker Compose YAML Validation Error

## Problem

Docker Compose failed to validate the configuration file with the following error:

```text
did not find expected key
```

## Cause

The `docker-compose.yml` file contained incorrect indentation. YAML is indentation-sensitive, and sections such as `volumes` and `networks` were incorrectly nested under the `services` section.

## Resolution

* Corrected the YAML indentation.
* Moved `volumes` and `networks` to the root level of the Compose file.
* Validated the configuration using:

```bash
docker compose config
```

## Lesson Learned

YAML formatting is whitespace-sensitive. Configuration files should always be validated before deployment.

---

# Docker Compose Network Configuration Error

## Problem

Docker Compose returned:

```text
services.networks Additional property osticket-network is not allowed
```

## Cause

The network definition was mistakenly declared inside the `services` block.

## Resolution

Moved the following section to the root level of the Compose file:

```yaml
networks:
  osticket-network:
    driver: bridge
```

## Lesson Learned

Docker Compose separates services, volumes, and networks into independent top-level sections.

---

# osTicket Database Connection Failure

## Problem

The osTicket container repeatedly restarted and failed to initialize.

Container logs reported:

```text
Missing required environmental variable MYSQL_HOST
```

## Cause

The deployment initially used generic database environment variables:

* DB_HOST
* DB_NAME
* DB_USER
* DB_PASS

However, the selected Docker image expected MySQL-specific environment variables.

## Resolution

Updated the environment variables to:

```text
MYSQL_HOST
MYSQL_DATABASE
MYSQL_USER
MYSQL_PASSWORD
```

The application successfully connected to MariaDB after redeployment.

## Lesson Learned

Always verify the required environment variables for a container image instead of assuming a standard naming convention.

---

# Container Log Analysis

## Problem

The application failed without displaying errors in the web interface.

## Resolution

Container logs were inspected using:

```bash
docker compose logs
```

and

```bash
docker logs <container-name>
```

The logs identified missing configuration variables and startup failures.

## Lesson Learned

Container logs are often the primary source of diagnostic information during application deployment.

---

# VirtualBox Port Forwarding

## Problem

Applications running inside the Debian virtual machine could not be accessed from the Arch Linux host.

## Cause

The virtual machine was configured using NAT networking without port forwarding.

## Resolution

Created TCP port forwarding rules inside VirtualBox for each required service.

Example:

| Host Port | Guest Port | Service     |
| --------- | ---------- | ----------- |
| 3001      | 3001       | Uptime Kuma |
| 3000      | 3000       | Wiki.js     |
| 8082      | 8082       | osTicket    |

## Lesson Learned

NAT networking isolates the guest operating system. Port forwarding is required to expose selected services to the host.

---

# Docker Networking

## Problem

Application containers required communication with their database containers.

## Resolution

Docker Compose bridge networking was used to provide internal service discovery.

Instead of referencing database IP addresses, services communicated using Docker service names.

Example:

```text
MYSQL_HOST=mariadb
```

Docker automatically resolved the hostname.

## Lesson Learned

Docker's internal DNS simplifies communication between containers while avoiding hard-coded IP addresses.

---

# Persistent Data Storage

## Problem

Container recreation can remove application data if no persistent storage is configured.

## Resolution

Docker volumes were created for persistent application data.

Examples:

* osticket-db-data
* osticket-data

## Lesson Learned

Application data should always be stored in Docker volumes rather than inside the container filesystem.

---

# Deployment Verification

The following commands were frequently used to verify infrastructure health.

Check running containers:

```bash
docker ps
```

Validate Docker Compose configuration:

```bash
docker compose config
```

Start services:

```bash
docker compose up -d
```

View logs:

```bash
docker compose logs
```

Stop services:

```bash
docker compose down
```

Inspect Docker networks:

```bash
docker network ls
```

Inspect Docker volumes:

```bash
docker volume ls
```

---

# Troubleshooting Workflow

The following troubleshooting methodology was adopted throughout the project:

1. Reproduce the issue.
2. Read the complete error message.
3. Inspect container logs.
4. Verify configuration files.
5. Confirm networking and connectivity.
6. Apply a single configuration change.
7. Redeploy the affected service.
8. Verify successful operation before proceeding.

This structured approach reduced unnecessary changes and simplified root cause identification.

---

# Key Takeaways

One of the most important lessons learned during this project was that infrastructure deployment is an iterative process. Successfully operating self-hosted services requires more than installation—it demands careful observation, log analysis, configuration management, and systematic troubleshooting.

Each issue encountered strengthened practical understanding of Linux administration, Docker, networking, and service management while reinforcing the importance of diagnosing problems methodically rather than relying on trial and error.
