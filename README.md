# Windows 10 Honeypot Setup on AWS

This project outlines the steps to configure a Windows 10 honeypot in AWS, tailored for security researchers and organizations wanting to study potential threats and vulnerabilities while ensuring comprehensive logging for SIEM systems such as Wazuh and Splunk.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
  - [AWS Setup](#aws-setup)
  - [EC2 Configuration](#ec2-configuration)
  - [Windows Configuration](#windows-configuration)
- [Integration with SIEM Tools](#integration-with-siem-tools)
- [Usage](#usage)
- [Important Notes](#important-notes)
- [Contributing](#contributing)
- [License](#license)

## Introduction

A honeypot is a decoy system designed to mimic likely targets of cyber attacks to detect, deflect, or study hacking attempts. This project provides a step-by-step guide to setting up a Windows 10 honeypot inside Amazon Web Services (AWS) with the integration of SIEM tools like Wazuh and Splunk for enhanced monitoring and logging capabilities.

## Prerequisites

- AWS Account
- Basic knowledge of AWS services (EC2, IAM, VPC)
- Familiarity with Windows 10 administration
- Understanding of SIEM systems, specifically Wazuh and Splunk

## Installation

### AWS Setup

1. **Sign Up for AWS:**
   - Visit [AWS Homepage](https://aws.amazon.com/) and create or log into your AWS account.
   - Access the AWS Management Console.

### EC2 Configuration

1. **Launch an EC2 Instance:**
   - Go to the EC2 Dashboard and click "Launch Instance."
   - Select a Windows 10 Amazon Machine Image (AMI) from the marketplace.
   - Choose an instance type, e.g., `t2.micro`.
   - Configure instance details, add storage, and set up security groups.
   - Allow inbound traffic on key ports like 22 (SSH) and 3389 (RDP).
   - Review and launch the instance.

### Windows Configuration

1. **System Hardening and Vulnerability Setup:**
   - Disable protective features like Windows Defender, Firewall, and automatic updates to simulate vulnerabilities.
   - Enable Remote Desktop and configure other settings as outlined in the tutorial steps.

## Integration with SIEM Tools

### Wazuh

- **Configuration**: Set up Wazuh to monitor system logs and events. Install the Wazuh agent on the honeypot machine and connect it to the Wazuh manager.
- **Usage**: Use Wazuh to analyze behavior, detect intrusions, and receive real-time alerts on suspicious activities.

### Splunk

- **Configuration**: Configure Splunk to collect logs from the honeypot. Ensure that Splunk Forwarders are properly installed and set to send logs to your Splunk instance.
- **Usage**: Utilize Splunk for deeper log analysis, visualization, and pattern recognition to study attack techniques and origins.

## Usage

After setup, the honeypot can be used to:
- Attract attackers to understand their tactics.
- Gather data on attempted breaches.
- Aid in improving the security posture of real systems by learning from the honeypot.

## Important Notes

- **Isolation**: Keep the honeypot isolated from critical internal networks.
- **Backup**: Regularly backup your honeypot environment.
- **Monitoring**: Actively monitor interactions with your honeypot and review logs frequently.

## Contributing

Github.com/Pozse
