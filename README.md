   
# Installing Splunk on Ubuntu Server in a Home Lab

## Introduction  
Splunk is a powerful tool for analyzing and visualizing machine-generated data. It provides real-time insights, making it ideal for monitoring network activity and security.  
In this guide, I’ll explain how to install and configure Splunk in my home lab. I’ll be forwarding logs from my Dream Machine router to analyze Intrusion Prevention System (IPS) logs and login activity.  

## Why Ubuntu Server?  
Ubuntu Server is lightweight and efficient, designed specifically for server environments. It comes without a GUI, minimizing resource usage, which is ideal for applications like Splunk that don’t require a graphical interface to run it.  

---

## Step 1: Create a Virtual Machine in VirtualBox  
1. Open VirtualBox and click **New**.  
2. Name your virtual machine, choose a storage folder, and select the Ubuntu Server ISO file.  
3. Skip the **Unattended Installation**.  
4. Allocate resources based on your system:  
   - **RAM**: 6-8 GB  
   - **CPU Cores**: 2-4  
   - **Storage**: 100 GB  

---

## Step 2: Install Ubuntu Server  
1. Start the VM, and from the **GNU GRUB** screen, select **Install Ubuntu Server**.  
2. Set up your username and password.  
3. For SSH configuration, you can skip or enable it based on your preference.  
4. Select **Done** and then **Reboot Now**.  
5. If prompted with a failed message, press **Enter** to continue.  

---

## Step 3: Update and Upgrade the System  
1. Log in with your username and password.  
2. Run the following commands:  
   ```bash
   sudo apt update && sudo apt upgrade -y
## 
Here’s a well-structured format for your README file in Markdown:

markdown
Copy code
# Installing Splunk on Ubuntu Server in a Home Lab

## Introduction  
Splunk is a powerful tool for analyzing and visualizing machine-generated data. It provides real-time insights, making it ideal for monitoring network activity and security.  
In this guide, I’ll explain how to install and configure Splunk in my home lab. I’ll be forwarding logs from my Dream Machine router to analyze Intrusion Prevention System (IPS) logs and login activity.  

## Why Ubuntu Server?  
Ubuntu Server is lightweight and efficient, designed specifically for server environments. It comes without a GUI, minimizing resource usage, which is ideal for applications like Splunk that don’t require a graphical interface.  

---

## Step 1: Create a Virtual Machine in VirtualBox  
1. Open VirtualBox and click **New**.  
2. Name your virtual machine, choose a storage folder, and select the Ubuntu Server ISO file.  
3. Skip the **Unattended Installation**.  
4. Allocate resources based on your system:  
   - **RAM**: 6-8 GB  
   - **CPU Cores**: 2-4  
   - **Storage**: 100 GB  

---

## Step 2: Install Ubuntu Server  
1. Start the VM, and from the **GNU GRUB** screen, select **Install Ubuntu Server**.  
2. Set up your username and password.  
3. For SSH configuration, you can skip or enable it based on your preference.  
4. Select **Done** and then **Reboot Now**.  
5. If prompted with a failed message, press **Enter** to continue.  

---

## Step 3: Update and Upgrade the System  
1. Log in with your username and password.  
2. Run the following commands:  
   ```bash
   sudo apt update && sudo apt upgrade -y
   
## Step 4: Configure a Static IP 

1. Run the following command to check your network interface and IP:
  
   ip a

   If you’re using a Bridged Adapter, the network should match your host. If you prefer isolation, you can use NAT.
   
2. Edit the Netplan configuration file:
   ```bash
   sudo nano /etc/netplan/00-installer-config.yaml
3. Add the following configuration changing the x:
```bash
network:
  ethernets:
    eth0:
      dhcp4: no
      addresses:
        - 192.168.x.x/24
      gateway4: 192.168.x.1
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4
  version: 2

