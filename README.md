# azure-passwordless-ssh-demo
Step-by-step setup of passwordless SSH between two Azure Linux VMs with one PuTTY session
# 🚀 Passwordless SSH Between Two Azure Linux VMs (One PuTTY Session)

## 📌 Overview
In this project, I demonstrate how to configure **passwordless SSH** from **VM1 to VM2** in Azure using **only one PuTTY login**.

🔹 **Scenario**  
- You create two Linux VMs in the same VNet/Subnet.
- You login to VM1 using PuTTY with password authentication.
- From VM1, you connect to VM2 **without entering any password or using a `.pem` file manually**.
- You configure SSH keys for secure internal communication.

---
## ✅ Step 1 — Create the VMs

- Provision two Ubuntu VMs in Azure.
- Same VNet/Subnet to allow internal IP communication.
- Use **username + password** authentication for both VMs.
- Note the **private IP** of VM2.

**Screenshot:**  
step1_create_vms.png
---

## ✅ Step 2 — Login to VM1

- Open PuTTY on your local machine.
- Enter the **public IP** of VM1.
- Connect using your username and password.

**Screenshot:** 
step2_login_vm1.png
---

## ✅ Step 3 — Generate SSH Key on VM1

Run this command in VM1’s terminal:
# ➡️ ssh-keygen -t rsa -b 2048
- Press Enter to accept the default location /home/<username>/.ssh/id_rsa
- Press Enter twice for empty passphrase.
This creates:
Private key: ~/.ssh/id_rsa
Public key: ~/.ssh/id_rsa.pub

**Screenshot:**
step3_ssh_keygen.png
---
## ✅ Step 4 - Copy the SSH Public Key to VM2
Run this command from VM1:
# ➡️ ssh-copy-id <username>@<VM2_Private_IP>
- Enter VM2’s password when prompted.
- This copies the public key to VM2’s ~/.ssh/authorized_keys.
  
**Screenshot:**
step4_ssh_copy_id.png
---
## ✅ Step 5 — Test Passwordless SSH
Now test SSH from VM1 → VM2:
# ➡️ssh <username>@<VM2_Private_IP>
✅ This time you should connect without a password prompt.

**Screenshot:**
step5_passwordless_ssh.png
---

🎉 **Result**
- You used only one PuTTY session to VM1.
- From VM1, you connected to VM2 securely and passwordlessly.
- This is useful for internal automation, scripts, or admin tasks across multiple servers.
  

**https://www.linkedin.com/in/nandini-ellapu-49aa81239**

