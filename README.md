# **Project: Setting Up Remote Access**

## **Introduction**
Remote access is a fundamental feature in modern IT environments, allowing users to connect to computers and manage them from a different location. This capability enhances efficiency, facilitates troubleshooting, and supports remote work. In this project, we will configure and use two primary remote access methods:
1. **Windows Remote Desktop Protocol (RDP)** - Connecting two Windows systems.
2. **Secure Shell (SSH)** - Establishing a remote session between Windows and Kali Linux.

By the end of this lab, you will understand the importance of remote access and the steps required to establish secure connections between systems.

---

## **Part 1: Setting Up Windows Remote Desktop**

### **Objective**
To enable, configure, and establish a remote desktop connection between two Windows machines.

### **Steps**
![My Image](https://mywebsite.com/image.png)


#### **1. Enabling Remote Desktop on PC10**
- **Sign in to PC10** using the credentials:
  - Username: Jaime
  - Password: `Pa$$w0rd`
- Open the **Windows Search Bar**, type `settings: system`, and select **System**.
- In the left panel, click **Remote settings**.
- In the **System Properties** window, under the **Remote** tab:
  - Check **Allow remote connections to this computer**.
  - Click **Select Users** → **Add**.
  - In **Enter the object names to select**, type **Rene**, then click **OK**.
  - Confirm that Rene is now listed and click **OK**.
  - Click **OK** to close the System Properties window.
- Close all open windows and **sign out of PC10**.

#### **Why This Is Important**
- Remote Desktop allows users to access their system remotely as if they were physically present.
- Adding authorized users ensures security by restricting access to specific individuals.

#### **2. Connecting to PC10 from DC10**
- **Sign in to DC10**:
  - Username: `Structureality\Administrator`
  - Password: `Pa$$w0rd`
- Open the **Windows Search Bar**, type `remote desktop`, and select **Remote Desktop Connection**.
- In the **Computer** field, enter `PC10` and click **Connect**.
- In the **Windows Security** window:
  - Click **More choices** → **Use a different account**.
  - Enter **Rene** as the username and `Pa$$w0rd` as the password.
  - Click **OK**.
- If prompted about another user being signed in, click **Yes** to confirm the connection.
- Minimize the Remote Desktop window to observe the local and remote desktops.
- Restore the Remote Desktop window and verify the **Computer Name** under **Settings → System**.
- Close the **System** window and **disconnect the Remote Desktop session**.

#### **Why This Is Important**
- Remote Desktop enables administrators to manage systems without being physically present.
- The verification step ensures the correct computer is being accessed.

---

## **Part 2: Configuring SSH on Kali Linux**

### **Objective**
To verify, configure, and establish an SSH connection between a Windows system and a Kali Linux system.

### **Steps**

#### **1. Verify SSH Installation on Kali**
- **Sign in to Kali** as root:
  - Username: `root`
  - Password: `Pa$$w0rd`
- Open a **Terminal Emulator**.
- Run the following command to check if SSH is installed:
  ```bash
  apt list openssh-server
  ```
- Ensure the output contains `[installed, automatic]`.
- Check SSH authentication settings:
  ```bash
  cat /etc/ssh/sshd_config | grep PasswordAuthentication
  ```
  - If `#PasswordAuthentication yes` appears, password authentication is enabled by default.
- Verify the SSH service is running:
  ```bash
  systemctl status ssh
  ```
  - Look for `Active: active (running)` in the output.
- Identify the IP address of Kali by running:
  ```bash
  ip a s eth0
  ```

#### **Why This Is Important**
- SSH allows secure remote access to Linux systems.
- Knowing the system's IP address is essential for remote connections.
- Verifying SSH settings ensures a successful connection attempt.

---

## **Part 3: Establishing an SSH Connection**

### **Objective**
To use SSH for remote access via both a GUI (PuTTY) and a CLI (Command Prompt) on Windows.

### **Steps**

#### **1. Connect Using PuTTY**
- **Sign in to PC10** as Jaime.
- Open **PuTTY** from the Desktop.
- In the **Host Name (or IP address)** field, enter `10.1.16.66`.
- Ensure the **Port** is set to `22` and click **Open**.
- If a security alert appears, click **Accept**.
- In the PuTTY window:
  - At `login as:`, enter `root`.
  - At `root@10.1.16.66's password:`, enter `Pa$$w0rd`.
  - Run `hostname` to verify you are connected to Kali.
  - Run `mkdir remote` to create a directory.
  - Run `exit` to disconnect.

#### **2. Connect Using Command Prompt**
- Open **Command Prompt** on PC10.
- Run:
  ```bash
  ssh root@10.1.16.66
  ```
- If prompted, enter `yes` to continue connecting.
- Enter `Pa$$w0rd` when prompted.
- Disable the welcome message:
  ```bash
  touch ~/.hushlogin
  ```
- Run `exit` to disconnect.
- Reconnect with SSH:
  ```bash
  ssh root@10.1.16.66
  ```
- Enter `Pa$$w0rd` and note that the welcome message is suppressed.
- Run `exit` to disconnect.

#### **Why This Is Important**
- PuTTY provides a user-friendly GUI for SSH connections.
- Command Prompt allows direct SSH access without extra software.
- Creating a folder remotely verifies the successful connection.
- Disabling the welcome message enhances efficiency by removing unnecessary login text.

---

## **Conclusion**
By completing this project, we have successfully:
- **Enabled and configured Windows Remote Desktop** for remote system management.
- **Verified and secured SSH on Kali Linux**, ensuring password authentication is enabled.
- **Established SSH connections using both GUI (PuTTY) and CLI (Command Prompt)** on Windows.

  Link to the Full walkthrough video :

  [![Watch the Video](https://img.youtube.com/vi/xEJt8DjmCxQ/0.jpg)](https://youtu.be/xEJt8DjmCxQ?si=tXO7ZtlFbagHFWMc)


These remote access methods provide a secure and efficient way to manage systems, troubleshoot issues, and perform administrative tasks remotely, which is essential for IT professionals. Understanding these techniques is crucial for maintaining secure and accessible computer networks in modern organizations.

