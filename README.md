# 📩 Automated Mail & DNS Lab Environment

![Ansible](https://img.shields.io/badge/Ansible-Provisioning-E00?style=for-the-badge&logo=ansible&logoColor=white) ![Vagrant](https://img.shields.io/badge/Vagrant-Environment-1563FF?style=for-the-badge&logo=vagrant&logoColor=white) ![Ubuntu](https://img.shields.io/badge/Ubuntu-20.04-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)

This repository contains a fully automated **Infrastructure-as-Code (IaC)** project. It provisions a complete email ecosystem (SMTP/IMAP) backed by a custom authoritative DNS server, designed to simulate a corporate intranet environment.

## 🗺️ System Topology

The infrastructure is isolated within a private network (`192.168.57.0/24`) and consists of two specialized nodes:

| Node | Hostname | IP Address | Service Stack | Function |
| :--- | :--- | :--- | :--- | :--- |
| **DNS Controller** | `dns-server` | **192.168.57.10** | `Bind9` | Serves as the authoritative Master for `fran.local`. Maps `smtp`, `imap`, and `pop` subdomains. |
| **Mail Gateway** | `mail-server` | **192.168.57.11** | `Postfix` + `Dovecot` | Handles mail storage (Maildir format) and transport. Configured with TLS support. |

---

## ⚡ Setup Guide

Follow these steps to spin up the lab in minutes.

### 1️⃣ Environment Preparation
Ensure you have the core virtualization tools installed. Then, clone the project:

```bash
git clone https://github.com/franmabb/Mail-stack-infrastructure.git
cd Mail-stack-infrastructure
