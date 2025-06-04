# Ubuntu Linux VM Unauthenticated vs Authenticated Scanning

This project documents the vulnerability scanning of an **Ubuntu Linux Virtual Machine (VM)** deployed in Azure, using **Tenable.io** for both unauthenticated and authenticated scans. The project highlights the significant differences in vulnerability detection when using authenticated credentials for scanning.

---

## ⚙️ Technology Utilized
- **Microsoft Azure** – Deployment of Ubuntu Linux VM.
- **Tenable.io (Nessus Scanner)** – Vulnerability scanning platform.
- **OpenSSH** – Secure login to the Ubuntu server.
- **Ubuntu 22.04.5 LTS** – Target operating system.

---

## 📁 Project Structure

---

## 📝 Phase 1: VM Creation and Environment Setup
✅ **Created a Ubuntu VM in Azure:**  
![1- Created a Ubuntu Virtual Machine](https://github.com/user-attachments/assets/3db2a8c1-af82-4ec9-a2f3-230200c5e418)

✅ **Verified network connectivity (ping):**  
![2- Make sure IP address is pinging](https://github.com/user-attachments/assets/ad9252c6-5a45-4a6e-a69f-80c04f5e5626)

✅ **Logged into the VM using SSH as user `LABUSERLINUX`:**  
![3- Logging into the Ubuntu Server from Terminal](https://github.com/user-attachments/assets/9fcce176-fce0-47af-a7e1-e5d4ab17c887)

✅ **Escalated privileges to root for full administrative access:**  
![Root Access](https://github.com/user-attachments/assets/J8STY87XGNqfkhoA2fWcvk)  

---

## 📝 Phase 2: Unauthenticated Scan
✅ **Created a Basic Network Scan in Tenable:**  
![Creating Scan in Tenable](https://github.com/user-attachments/assets/4- Creating a Basic Scan in Tenable.png)  
![Configuring the Scan](https://github.com/user-attachments/assets/M9pyT426eXuXhx8DfiQuiK)  
✅ **Set the target as the VM's private IP:**  
![Putting Target IP](https://github.com/user-attachments/assets/WrypRqyZFWgxAX5o5NrfB8)  

✅ **Edited Discovery settings for custom and fast scanning:**  
![Editing Discovery Page](https://github.com/user-attachments/assets/AMG9kyYRnLEHgf1n828x97)  

✅ **Unauthenticated Scan Results:**  
- Summary of vulnerabilities (1 critical, 2 high, 3 medium, 2 low, 57 informational)  
![Unauthenticated Scan Summary](https://github.com/user-attachments/assets/AUkCpn2iHHNxz7X37LLnku)  
- Exported results for better analysis:  
![Exported Results](https://github.com/user-attachments/assets/9- Exported Unauthenticated Scan Results.png)  

---

## 📝 Phase 3: Enabling Root SSH for Authenticated Scanning
✅ **Reset root password and enable remote login:**  
![Reset Root Password](https://github.com/user-attachments/assets/3qsEjZnNPmfobBDKSpo5Yh)  
![Permit Root Login](https://github.com/user-attachments/assets/5y3YRr9GUrvTYuvsCsHskR)  

✅ **Verified SSH login as root:**  
![SSH as Root](https://github.com/user-attachments/assets/YZgRotcbJNDC8vNacJyA35)  

---

## 📝 Phase 4: Authenticated Scan
✅ **Edited the scan settings to include SSH root credentials:**  
![Editing SSH Credentials in Tenable](https://github.com/user-attachments/assets/MMhRzZpf1W6GamcXDNuyEq)  

✅ **Ran the authenticated scan:**  
![Authenticated Scan Completion](https://github.com/user-attachments/assets/15- Authenticated Scan completed.png)  
✅ **Exported results for better analysis:**  
![Exported Authenticated Scan Results](https://github.com/user-attachments/assets/16- Exported Results for better evaluation.png)  

---

## 🔍 Comparison of Results

| Metric                       | Unauthenticated Scan | Authenticated Scan |
|------------------------------|----------------------|--------------------|
| Critical Vulnerabilities     | 1                    | 1                  |
| High Vulnerabilities         | 2                    | 2                  |
| Medium Vulnerabilities       | 3                    | 3                  |
| Low Vulnerabilities          | 2                    | 2                  |
| Informational                | 57                   | 20                 |
| **Total Vulnerabilities**    | 65                   | 28                 |

Authenticated scans provide more precise and accurate vulnerability data by using privileged access to probe deeper within the system.

---

## 💬 Group Meeting Chat (Example)
> **Felipe (Linux Admin):** Ran the unauthenticated scan. Found basic issues like ICMP exposure and SSH settings.  
> **Anna (Security Analyst):** Those are good, but deeper OS-level findings are only exposed with credentials.  
> **Felipe:** Absolutely. Authenticated scans confirmed vulnerabilities in GLib, Kerberos, and more.  
> **Anna:** Let’s focus on critical and high vulnerabilities first.  
> **Felipe:** I’ll build a remediation plan for them.

---

## 🚀 Final Takeaways
- Unauthenticated scans are helpful for external exposure but miss critical system-level vulnerabilities.  
- Authenticated scans reveal deeper issues, leveraging privileged access.  
- Always prioritize securing critical and high vulnerabilities first!
