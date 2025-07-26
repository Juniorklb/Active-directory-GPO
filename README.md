
# 🖥️ Active Directory with Group Policy (GPO)

This project demonstrates the deployment and configuration of **Active Directory Domain Services (AD DS)** and **Group Policy Objects (GPO)** in a **Windows Server 2022** environment. It simulates a small enterprise setup with multiple departments (IT, HR, Sales), each managed through Organizational Units (OUs) and secured by GPOs.

---

## 📌 Project Overview

- Setup and promotion of a domain controller (`kalomba.local`)
- Creation of Organizational Units for departmental structure
- User and group account management per department
- GPOs to enforce restrictions (e.g., disable Control Panel, set wallpaper, block CMD)
- Network configuration (static IP, DNS integration)

---

## 🛠️ Tools & Technologies

- 💻 VMware Workstation
- 🪟 Windows Server 2022
- ⚙️ Active Directory Domain Services
- 📂 Group Policy Management Console (GPMC)

---

## 🧱 Project Structure

```
kalomba.local
│
├── IT
│   └── james.it
│
├── HR
│   └── lucy.hr
│
└── Sales
    └── david.sales
```

---

## 🔧 Step-by-Step Setup

### Step 1: Set Static IP Address
1. Open **Network and Sharing Center**
2. Click **Change adapter settings**
3. Right-click Ethernet > **Properties**
4. Select **Internet Protocol Version 4 (TCP/IPv4)** > Properties
5. Configure:
   - IP: `192.168.1.10`
   - Subnet: `255.255.255.0`
   - Gateway: `192.168.1.1`
   - DNS: `192.168.1.10`

---

### Step 2: Install AD DS Role
1. Open **Server Manager**
2. Click **Add Roles and Features**
3. Select:
   - Role-based installation
   - Local server
4. Choose **Active Directory Domain Services**
5. Complete the wizard and install

---

### Step 3: Promote to Domain Controller
1. After install, click the yellow flag > **Promote this server**
2. Choose:
   - **Add new forest**
   - Domain: `kalomba.local`
3. Set DSRM password and accept defaults
4. Restart after installation

---

### Step 4: Create Organizational Units
1. Open **Active Directory Users and Computers**
2. Expand `kalomba.local`
3. Right-click > **New > Organizational Unit**
4. Create: `IT`, `HR`, `Sales`

---

### Step 5: Create Users and Groups
For each OU:
1. Right-click > **New > User**
2. Example:
   - `james.it@kalomba.local`
   - `lucy.hr@kalomba.local`
   - `david.sales@kalomba.local`
3. Set passwords and optionally enforce password change on first login

---

### Step 6: Create & Link GPOs

#### Disable Control Panel (HR)
- GPO: `Disable_ControlPanel_HR`
- Path:  
  `User Config > Policies > Admin Templates > Control Panel > Prohibit access`

#### Set Wallpaper (Sales)
- GPO: `Sales_Wallpaper`
- Path:  
  `User Config > Admin Templates > Desktop > Desktop Wallpaper`
- Use: `\\DC01\Wallpapers\company.jpg`

#### Block Command Prompt (All)
- GPO: `Disable_CMD_All`
- Path:  
  `User Config > Admin Templates > System > Prevent access to command prompt`

---

## ✅ Skills Demonstrated

- Windows Server Administration
- AD DS and DNS setup
- GPO design and deployment
- Organizational Unit hierarchy
- Security and user restrictions

---

## 📄 Documentation

👉 [View the full project PDF](Final_AD_Project_With_New_Logo.pdf)

---

## 🏁 Conclusion

This project demonstrates real-world Active Directory configuration and GPO enforcement in a structured domain environment, providing essential experience for aspiring system administrators.
