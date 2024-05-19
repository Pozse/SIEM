# Creating a SIEM with Azure VM + Sentinel

## Introduction

A SIEM (Security Information and Event Management) system is a security overview tool that collects and sorts data from various sources within an organization. It is widely used in SOC (Security Operations Center) Analyst positions to issue alerts and detect incidents in real-time. This guide details the steps to set up a SIEM using Azure Virtual Machine (VM) and Microsoft Sentinel.

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
  - [Create Virtual Machine](#create-virtual-machine)
  - [Networking Configuration](#networking-configuration)
  - [Log Analytics Workspace](#log-analytics-workspace)
  - [Microsoft Defender for Cloud](#microsoft-defender-for-cloud)
  - [Connect Log Analytics Workspace to VM](#connect-log-analytics-workspace-to-vm)
  - [Custom Log in Log Analytics Workspace](#custom-log-in-log-analytics-workspace)
- [Usage](#usage)
- [Features](#features)
- [Dependencies](#dependencies)
- [Configuration](#configuration)
- [Documentation](#documentation)
- [Examples](#examples)
- [Troubleshooting](#troubleshooting)
- [Contributors](#contributors)
- [License](#license)

## Installation

### Create Virtual Machine

1. Log in or create a free trial Azure account at [Azure](https://azure.microsoft.com/en-us/free).
2. Click `Create a resource` from the top left.
3. Under `Popular Azure services`, click `Create` under `Virtual machine`.

#### Instance Details
- **Subscription:** Azure Subscription 1 (Azure for Students in this guide)
- **Resource Group:** SIEM
- **VM Name:** HoneypotLab
- **Region:** US West 3
- **Availability options:** No Infrastructure Redundancy Required
- **Security Type:** Standard
- **Image:** Windows 10 Pro Version 22 H2 Gen 1
- **Size:** Standard D2s_v3 (2 vCPUs, 8 GiB memory)

#### Administrator Credentials
- Create and remember your username and password.

#### Inbound Port Rules
- Default (Allow selected ports RDP 3389)

4. Click `Next: Disks >` and then `Next: Networking >`.

### Networking Configuration

1. Under `NIC Security Group`, change from Basic to Advanced.
2. Click `Configure network security group` and then `Create New`.
3. Add an inbound rule with the following settings:
   - **Destination port ranges:** *
   - **Priority:** 100
   - **Name:** DANGER_ANY_IN
4. Click `Add`, `OK`, `Review + Create`, and then `Create`.

### Log Analytics Workspace

1. In a new tab, search for `Log Analytics Workspace` under `Popular Azure services` and click `Create`.
2. **Subscription:** Azure Subscription 1
3. **Resource Group:** SIEM
4. **Name:** law-honeypot-1
5. **Region:** US West 2
6. Click `Review + Create` and then `Create`.

### Microsoft Defender for Cloud

1. Go to `Microsoft Defender for Cloud` on the right pane.
2. Scroll down to `Environment settings` on the left pane.
3. Click `law-honeypot-1`.
4. Turn `Foundational CSPM` and `Servers` to `On`.
5. Click `Save`.
6. Under `Data collections`, select `All Events` and Save.

### Connect Log Analytics Workspace to VM

1. Go to your Azure homepage and click on `Log Analytics Workspace (law-honeypot-1)`.
2. On the left pane, find `Virtual machines (deprecated)`.
3. Select `HoneypotLab` and click `Connect`.
4. Go to your homepage, search for `Microsoft Sentinel`, click on `law-honeypot-1`, and Add.

### Custom Log in Log Analytics Workspace

1. In Azure, go to `law-honeypot-1 Log Analytics Workspace`.
2. Click on `Tables` on the left pane, then `Create`.
3. Select `New Custom Log (MMA-based)`.
4. Select your `failed_rdp.log` file.
5. Set `Record Delimiter` to `New Line`.
6. Set the collection path type to `Windows` and the path to `C:\ProgramData\failure_rdp.log`.
7. Name the Custom Log `FAILED_RDP_LOG_GEO`.
8. Click `Create`.

## Usage

To use the SIEM, log in to your VM using Remote Desktop, configure necessary settings, and monitor security events using Microsoft Sentinel.

## Features

- Real-time incident detection and alerts.
- Integration with Microsoft Sentinel for comprehensive security monitoring.
- Customizable log analytics and data collection.

## Dependencies

- Azure account with appropriate subscription.
- Windows 10 Pro VM.
- Log Analytics Workspace.
- Microsoft Defender for Cloud.
- Microsoft Sentinel.

## Configuration

Configuration involves setting up the VM, network security, Log Analytics Workspace, and connecting these components to work with Microsoft Sentinel.

## Documentation

For more detailed instructions and advanced configurations, refer to the [official Azure documentation](https://docs.microsoft.com/en-us/azure/).

## Examples

Examples include configuring network security rules, creating and managing logs, and integrating with Microsoft Sentinel.

## Troubleshooting

Common issues involve network configurations and permissions. Ensure all settings are correctly applied and inbound rules are properly configured.

## Contributors

- Pozse, Josh Makador
