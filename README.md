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
![4- Logged In](https://github.com/user-attachments/assets/e6f796a3-f11c-42f2-aadb-9737930a62b9)

---

## 📝 Phase 2: Unauthenticated Scan
✅ **Created a Basic Network Scan in Tenable:**  
![5- Opened Tenable and creating a Basic Network Scan](https://github.com/user-attachments/assets/c2ab1d71-3ffb-46a6-a7b7-0c1f349f2085)
 
✅ **Configuring the Unauthenticated Scan and setting the private IP address as the only target:**  
![6- Configuring the Basic Network Scan](https://github.com/user-attachments/assets/84470b24-d882-4bed-bf74-4c3b9fa281a6)
![6- Putting the private IP from the VM as a target](https://github.com/user-attachments/assets/fa466918-9985-4cc4-b8e2-259ff286ac69)

✅ **Edited Discovery settings for custom and fast scanning:**  
  ![7- Editing the Discovery page to Custom, and enabling a fast network discovery](https://github.com/user-attachments/assets/145c244f-fb7f-43d8-b249-410e07331cf9)

✅ **Unauthenticated Scan Completion and Results:**  
![8- Unauthenticated Scan Completed](https://github.com/user-attachments/assets/36411adc-01a3-4d49-8029-6d941d867458)
![9- Results in from Unauthenticated Scan](https://github.com/user-attachments/assets/68d8b327-5699-4baa-ad13-4ee33a5b8c0d)

✅ **Exported Results for better analysis:**
![9- Exported Unauthenticated Scan Results](https://github.com/user-attachments/assets/7649c484-bc53-43e4-8718-acdc851e86b4)

---

## 📝 Phase 3: Enabling Root SSH for Authenticated Scanning
✅ **Reset root password and enable remote login:**  
![10- Reset the root passwd to default](https://github.com/user-attachments/assets/5254d5b5-b0c2-4d84-b036-a35548f218b5)
![11- Command allow the root to be used to login remotely](https://github.com/user-attachments/assets/959849dd-8ece-4df3-9812-dffcf0dbf7e5)

✅ **Verified SSH login as root:**  
![12- Logged back to the VM as root](https://github.com/user-attachments/assets/eae81b5e-304d-4864-a1cd-5387601e6555)
![13- Logged in successfully](https://github.com/user-attachments/assets/07676c5c-7b51-44c6-8524-99d582af6e5f)

---

## 📝 Phase 4: Authenticated Scan
✅ **Edited the scan for an Authenticated Scan and went to Credentials to include SSH root credentials:**  
![14- Edited the last scan for a Authenticated Scan Setting up the ssh credentials](https://github.com/user-attachments/assets/4cf9da49-b4d1-40cd-a0a5-efa812f531bc)

✅ **Ran the authenticated scan:**  
![15- Authenticated Scan completed](https://github.com/user-attachments/assets/d9377a93-0584-4826-ae0c-9928f676a745)
![16- Results in Tenable](https://github.com/user-attachments/assets/bd530b0a-6d16-4e4e-ab35-a7f46b0110b5)

✅ **Exported results for better analysis:**  
![16- Exported Results for better evaluation](https://github.com/user-attachments/assets/9b973e5b-19d8-4872-9346-b2433c03d0a2)

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
