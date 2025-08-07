
# ☁️ How to Create a Virtual Machine (VM) in AWS (EC2)

Spin up and connect to an EC2 instance using the AWS Console **or** AWS CLI. Perfect for first-time AWS users and quick labs.

---

## Table of Contents
- [Prerequisites](#prerequisites)
- [Part A — AWS Console](#part-a--aws-console)
- [Part B — AWS CLI](#part-b--aws-cli)
- [Connect to Your VM](#connect-to-your-vm)
- [Security Tips](#security-tips)
- [Troubleshooting](#troubleshooting)
- [Cleanup](#cleanup)

---

## Prerequisites
- AWS account (Free Tier eligible)
- For Linux: SSH client. For Windows: Remote Desktop client.
- (Optional) AWS CLI v2 installed and configured:
  ```bash
  aws configure   # enter Access Key, Secret, region (e.g., us-east-1), output json
