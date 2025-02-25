![OSTicket](https://github.com/user-attachments/assets/41ff652a-befe-4f99-a1b3-e86b7955eeb9)
# Os-Ticket
This repository documents my hands-on experience setting up and using OS Ticket, an open-source help desk ticketing system.

## 🛠️ Lab Objectives  
✔ Deploy a Virtual Machine (VM) in **Microsoft Azure**  
✔ Install and configure **OS Ticket** on the VM  
✔ Set up **IIS (Windows)** for web hosting  
✔ Configure **MySQL** for database management  
✔ Create and manage tickets within OS Ticket  
✔ Explore **help desk workflows** in a cloud-hosted environment  

## 🔧 Technologies Used  
- **Microsoft Azure** (Cloud hosting)  
- **Windows Server** (Deployed OS Ticket on a VM)  
- **OS Ticket** (Help desk ticketing system)  
- **IIS** (Web hosting for OS Ticket)  
- **MySQL** (Database backend)  
- **Remote Desktop Protocol (RDP) / SSH** (For VM access)  

## ☁️ Azure overall Deployment Steps  
1. **Created a Virtual Machine (VM)** in Azure   
2. **Configured networking** (Allowed HTTP, HTTPS, RDP, and MySQL ports)  
3. **Installed OS Ticket** and its required dependencies  
4. **Set up IIS (Windows)** for web access  
5. **Configured MySQL database** and linked it to OS Ticket  
6. **Tested ticket submission and resolution workflows**  

## ## ☁️ Deployment Steps walkthrough 

### **Step 1: Create Virtual Machines in Azure**  
1. Log into **Microsoft Azure** and go to **Virtual Machines**  
2. Click **Create > Azure Virtual Machine**  
3. Choose **Windows 10**  
4. Select an appropriate **VM size**  
5. Configure **Networking**:  
   - Allow **RDP (3389)** for Windows or **SSH (22)** for Linux  
   - Allow **HTTP (80)** and **MySQL (3306)**
6. Make sure to also create the Resource group as well 

 ![Virtual Machine](https://github.com/user-attachments/assets/1ab19549-9ef9-43c9-b5ac-65aecf9e4fa5)

 ### **Step 2: Connect to the Virtual Machine**  
1. If using **Windows Server**, connect via **Remote Desktop (RDP)**

![Remote Desktop Connection 2_25_2025 9_37_42 AM](https://github.com/user-attachments/assets/0b703273-a7f2-4fac-aa56-a1f70d5fddd0)

### **Step 3: Install OS Ticket and Dependencies**

1. Download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
   - We will use the files in this folder to install osTicket and some dependencies.
2. Install / Enable IIS in Windows WITH CGI
   - World Wide Web Services -> Application Development Features -> [X] CGI

  ![IIS](https://github.com/user-attachments/assets/c5261853-1701-44dc-916b-065672278d93)

3. From the “osTicket-Installation-Files” folder, install PHP Manager for IIS
4. From the “osTicket-Installation-Files” folder install the Rewrite Module
5. Create the directory C:\PHP and from the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
6. From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.
7. From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
   - Typical Setup
   - Launch Configuration Wizard
   - Standard Configuration
  
   ![My SQL](https://github.com/user-attachments/assets/32f48c4b-4835-4740-99e8-7baf9baa15c3)

8. Open IIS as an Admin and Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)
9. Reload IIS (Open IIS, Stop and Start the server)
10. Install osTicket v1.15.8
    - From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
    - Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”.
11. Reload IIS (Open IIS, Stop and Start the server)
12. Go to sites -> Default -> osTicket
    - On the right, click “Browse *:80”

      ![Os Ticket Installer](https://github.com/user-attachments/assets/a479d541-2c67-43a6-9fd5-6182be269e2c)

13. Some extensions are not enabled
    - Go back to IIS, sites -> Default -> osTicket
    - Double-click PHP Manager
    - Click “Enable or disable an extension
      - Enable: php_imap.dll
      - Enable: php_intl.dll
      - Enable: php_opcache.dll
    - Refresh the osTicket site in your browser, observe the changes
14. Rename: ost-config.php
    - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
    - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
15. Assign Permissions: ost-config.php
    - Disable inheritance -> Remove All
    - New Permissions -> Everyone -> All
16. Continue Setting up osTicket in the browser

    ![Os Ticket install page](https://github.com/user-attachments/assets/9e780570-90e7-487e-88f6-606ec409a282)

17. From the “osTicket-Installation-Files” folder, install HeidiSQL.
    - Create a database called “osTicket”
18. Once you finish Setting up osTicket in the browser we are done.
19. Browse to your help desk login page: http://localhost/osTicket/scp/login.php

    ![Os ticket login page](https://github.com/user-attachments/assets/55a241aa-b3c5-42cd-9d2d-d0fbc1ff59ee)









   



## 📚 Key Takeaways  
📌 Hands-on experience with **Microsoft Azure Virtual Machines**  
📌 Understanding of **help desk ticketing systems**  
📌 Practical skills in **server administration & cloud deployment**  
📌 Improved **troubleshooting and IT support** skills 
