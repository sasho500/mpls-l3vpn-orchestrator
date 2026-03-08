# 🌐 MPLS L3VPN Orchestrator

> 🧠 Intent-based MPLS L3VPN (VRF) orchestration, compliance checks, drift detection, and automated verification with Python.

---

## 📌 Project Status

This project is still in progress.

The main goal is to build a small but realistic network automation tool that can:

- read network intent from YAML files
- validate the input
- compare intent with the current device state
- generate a change plan
- apply changes safely
- verify the final result
- save useful artifacts like backups, diffs, and reports

---

## 🚀 Why I Built This

I made this project as part of my **Automating Networks with Python** portfolio work.

I wanted to build something more useful than a simple script.  
The idea is to show a full workflow that is closer to a real automation tool used in networking:

**intent → plan → apply → verify**

The project focuses on **MPLS L3VPN / VRF provisioning**, compliance, drift detection, and post-change verification.

---

## 🧭 Main Idea

The tool reads the desired state from YAML files and compares it with the real state on the devices.

If something is missing or configured in the wrong way, it creates a plan.  
After that, it can apply the needed changes and run verification checks.

This makes the workflow safer, cleaner, and easier to review.

---

## ✨ Features

- 🛰️ VRF provisioning
- 🏷️ RD / RT configuration
- 🔄 Route leaking policy through import/export RT rules
- ✅ Intent validation with Python models
- 🔍 Drift detection and compliance checks
- 📝 Human-readable change plan
- 🛡️ Safe apply flow with pre-checks
- 💾 Backup before and after changes
- 🧪 Verification checks after apply
- 🐳 Docker-based run environment
- 🧰 Unit tests and linting

---

## 🧱 Lab Topology

This project is designed for a small Cisco-based lab:

- **R1** - IOS XE
- **R2** - IOS XR
- **R3** - IOS XE

The target workflow uses:

- **NETCONF**
- **RESTCONF**
- **YANG**
- **Netmiko**
- **NAPALM**
- **Docker**

---

## 🔁 Workflow

The project follows this flow:

1. Load inventory and intent files
2. Validate the intent
3. Collect the current state from devices
4. Compare current state vs desired state
5. Generate a plan
6. Apply changes
7. Run verification checks
8. Save artifacts

## 🛠️ Tech Stack

Python - main language

Pydantic - input validation

Netmiko - CLI access and fallback

NAPALM - state collection and config support

ncclient / NETCONF - structured device changes

RESTCONF - API-based access for IOS XE

Docker - easy and repeatable setup

pytest - unit tests

ruff / flake8 / black - code quality tools