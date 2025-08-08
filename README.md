#  Task 4: Firewall Configuration Using UFW (Linux)

##  Objective

To configure and test firewall rules using **UFW (Uncomplicated Firewall)** to block insecure traffic (Telnet on port 23) and allow secure traffic (SSH on port 22). This demonstrates basic firewall management and traffic filtering on Linux.

---

##  Tools Used

- ✅ UFW (Uncomplicated Firewall)
- ✅ Netcat (nc)
- ✅ Telnet

---

## Steps Performed

### 🔹 1. Check UFW Version and Status
```bash
ufw version
sudo ufw status verbose

    Initially, the firewall was inactive.

🔹 2. Enable UFW and Allow SSH

sudo ufw enable
sudo ufw allow 22/tcp comment 'allow SSH (prevent lockout)'

    SSH allowed to prevent being locked out.

🔹 3. Block Telnet (Port 23)

sudo ufw deny 23/tcp comment 'block Telnet (insecure protocol)'

    Telnet is insecure and commonly exploited.

🔹 4. Verify Rules Applied

sudo ufw status numbered

Sample output:

[ 1] 22/tcp ALLOW IN Anywhere
[ 2] 23/tcp DENY IN Anywhere
...

🔹 5. Test Port 23 Using Netcat and Telnet

nc -vz 127.0.0.1 23
telnet 127.0.0.1 23

     Both comm#  Task 4: Firewall Configuration Using UFW (Linux)

##  Objective

The objective of this task is to set up and test firewall rules using **UFW (Uncomplicated Firewall)** on Linux to allow secure traffic (SSH on port 22) and block insecure traffic (Telnet on port 23). This ensures you understand how to filter and manage network traffic effectively.

---

##  Tools Used

-  **UFW** – Easy-to-use frontend for iptables
-  **Netcat (nc)** – Port scanning / testing tool
- **Telnet** – Used to test insecure port connection
-  **Kali Linux Terminal + Screenshots**

---

## Steps Performed (With Commands & Explanations)

### 🔹 Step 1: Check UFW Version and Initial Status

```bash
ufw version
sudo ufw status verbose

🔸 Initially, the firewall was inactive, which means the system had no active traffic filtering.
🔹 Step 2: Enable UFW and Allow SSH (Port 22)

sudo ufw enable
sudo ufw allow 22/tcp comment 'allow SSH (prevent lockout)'

Reason: SSH is crucial for remote access. Blocking this could lock us out, so we must allow it before doing anything else.
🔹 Step 3: Block Telnet (Port 23)

sudo ufw deny 23/tcp comment 'block Telnet (insecure protocol)'

Reason: Telnet transmits data in plain text and is deprecated. Blocking it is a standard hardening step.
🔹 Step 4: List All Active Rules

sudo ufw status numbered

Sample Output:

[ 1] 22/tcp                     ALLOW IN    Anywhere   # allow SSH (prevent lockout)
[ 2] 23/tcp                     DENY IN     Anywhere   # block Telnet (insecure protocol)

🔹 Step 5: Test if Port 23 is Blocked

Commands used to simulate connection attempts:

nc -vz 127.0.0.1 23
telnet 127.0.0.1 23

Output confirmed:
Connection refused — means port 23 is successfully blocked by the firewall.

See screenshot_1.png and screenshot_2.png
🔹 Step 6: Save Firewall Configuration Output

sudo ufw status verbose > ufw_rules.txt
This output file has been included in the repository.
Files Included in This Repository
File Name	Description
README.md	Detailed explanation and steps
ufw_rules.txt	Active firewall rule list
screenshot_1.png	Netcat and Telnet output showing block
screenshot_2.png	UFW status numbered rule output
