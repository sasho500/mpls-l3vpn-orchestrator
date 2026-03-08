# MPLS L3VPN Orchestrator

Intent-based MPLS L3VPN (VRF) orchestration, compliance checks, drift detection, and automated verification with Python.

## Project Status

This project is still in progress.  
The main goal is to build a small but realistic network automation tool that can:

- read network intent from YAML files
- validate the input
- compare intent with the current device state
- generate a change plan
- apply changes safely
- verify the final result
- save useful artifacts like backups, diffs, and reports

## Why I Built This

I made this project as part of my **Automating Networks with Python** portfolio work.

I wanted to build something more practical than a simple script.  
The idea is to show a full workflow that looks closer to a real automation tool:

**intent -> plan -> apply -> verify**

The project focuses on MPLS L3VPN / VRF provisioning and compliance. It also includes drift detection, backups, and rollback-friendly artifacts.

## Main Idea

The tool reads the desired state from YAML files and compares it with the real state on the devices.

If something is missing or wrong, it creates a plan.  
After that, it can apply the needed changes and run verification checks.

This makes the workflow safer and easier to understand.

## Features

- VRF provisioning
- RD / RT configuration
- Route leaking policy through import/export RT rules
- Intent validation with Python models
- Drift detection and compliance checks
- Human-readable change plan
- Safe apply flow with pre-checks
- Backup before and after changes
- Verification checks after apply
- Docker-based run environment
- Unit tests and linting

## Lab Topology

This project is designed for a small Cisco lab:

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

## Workflow

The project follows this flow:

1. Load inventory and intent files
2. Validate the intent
3. Collect the current state from devices
4. Compare current state vs desired state
5. Generate a plan
6. Apply changes
7. Run verification checks
8. Save artifacts

## Repository Structure

```text
mpls-l3vpn-orchestrator/
│
├── intent/
│   ├── vrfs.yml
│   ├── devices.yml
│   └── policy.yml
│
├── netauto/
│   ├── cli.py
│   ├── inventory.py
│   ├── intent_models.py
│   ├── compliance.py
│   ├── verify.py
│   └── drivers/
│       ├── iosxe_restconf.py
│       ├── iosxe_netconf.py
│       ├── iosxr_netconf.py
│       └── cli_netmiko.py
│
├── artifacts/
│   ├── backups/
│   ├── plans/
│   └── reports/
│
├── tests/
├── docker/
├── docker-compose.yml
├── requirements.txt
└── README.md