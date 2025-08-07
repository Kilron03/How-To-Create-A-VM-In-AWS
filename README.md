

This focuses entirely on **creating and connecting to a Windows Server VM in AWS**.

---

````markdown
 How to Create a Windows Virtual Machine (VM) in AWS (EC2) — Step by Step

This guide walks you through creating a Windows Server EC2 instance in AWS, connecting via RDP, and performing basic configuration.

---

 What You’ll Build
- A Windows Server EC2 instance (2019 or 2022)
- Secure inbound access via RDP (3389) from your IP
- Ready for Active Directory, IIS, or other Windows roles

---

 Prerequisites
- AWS account with billing enabled
- RDP client installed (Windows has this by default; Mac/Linux can use Microsoft Remote Desktop app)
- AWS key pair (`.pem` file) for decrypting Administrator password


---

PART A — Create a Windows VM via AWS Console

 1) Launch the Instance
1. Log in to the [AWS Management Console](https://aws.amazon.com/console/).
2. Go to EC2 → Launch Instance.
3. Name: `Windows-Server-VM`.
4. Amazon Machine Image (AMI):
   - Choose **Microsoft Windows Server 2022 Base** or Windows Server 2019 Base.
5. Instance type: `t2.medium` (recommended for Windows; `t2.micro` is Free Tier but slower).
6. **Key pair**: Create/select a key pair (`.pem`) — download and store securely.
7. Network settings:
   - Create or select a Security Group.
   - Add inbound rule for RDP (port 3389)** from My IP.
8. Storage: Default 30 GB gp3 (Windows needs more than Linux).
9. Click Launch instance.

---

 2) Wait for Initialization
- In EC2 → Instances, watch until Status checks show 2/2 passed.
- Select your instance and note:
  - Public IPv4 address
  - Instance ID

---

 3) Get the Administrator Password
1. Select your instance in the EC2 console.
2. Click Connect → RDP Client.
3. Under Get password, choose your `.pem` file and click Decrypt password.
4. Copy the decrypted Administrator password.

---

 4) Connect via Remote Desktop (RDP)
On Windows:
1. Open Remote Desktop Connection (`mstsc` in Start menu).
2. Enter the Public IPv4 address.
3. Username: `Administrator`
4. Password: paste the decrypted password.
5. Accept any certificate warning.

On Mac:
- Install Microsoft Remote Desktop from the App Store.
- Add a new PC connection with the Public IP and Administrator credentials.

---


🛠 Initial Windows Server Setup

Once connected:

1. Open Server Manager (default on login).
2. Rename the computer (Local Server → Computer name → Change) and reboot.
3. Install updates via Windows Update.
4. Optionally, add server roles:

   Active Directory Domain Services (AD DS)
   Web Server (IIS)
   File Server

---

Cleanup

When done:

1. Terminate the instance from the EC2 console.
2. Delete unused security groups and key pairs.
3. Release any allocated Elastic IPs.

---

