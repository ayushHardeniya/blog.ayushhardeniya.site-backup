---
title: "How to Install Kali Linux on a Secondary Drive without affecting Windows & WSL Performance"
seoTitle: "Install Kali on Secondary Drive: No Impact on Windows & WSL"
seoDescription: "Install Kali Linux on a secondary drive (D:/W:) using VirtualBox. Keep your Windows & WSL setup clean and save C: drive space with this 2026 guide."
datePublished: 2026-03-27T07:10:34.216Z
cuid: cmn8kawgp02q12dmmbs41dqfd
slug: how-to-install-kali-linux-on-a-secondary-drive-without-affecting-windows-wsl-performance
cover: https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/9b989028-c6b1-4f95-ac62-18da63c2fee2.jpg
ogImage: https://cdn.hashnode.com/uploads/og-images/68386d1121b9d74a4a2d7b62/ae037d80-6756-4933-9bd4-417127532441.jpg
tags: kali-linux, cybersecurity, wsl, windows-11, kali-linux-download, ayushhardeniya

---

![](https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/4666d793-ea28-4b1d-b114-c2251d656256.png align="center")

## **Current Setup (Mine):**

**4 disks**: In `PowerShell` run \[to check the statuss of disks\]

```shell
Get-PsDrive -PSProvider FileSystem
```

*   C:\\ consist of Home (Windows 11)
    
*   W:\\ consist of WSL (Ubuntu + Debian)
    
    *   Confirmation:- \[`PowerShell`\]
        

![](https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/12c5bcdc-c957-41b2-9c26-5a3707a3e015.png align="center")

## Target Set Up:

C:\\ remains untouched, for future experimental accidents, to avoid any root windows failures

And as there’s **266 GB** of space available in W:\\ (*in my case*), we will set up Kali Linux inside W:\\ only, along with WSL running in parallel but inside a VM (VirtualBox) for distributed (limited) machine load, as it operates dynamically, doesn’t immediately occupy the complete 60-80 GB required space of Kali Linux on our local machine.

* * *

### **1\. Why won't it interfere with WSL**

WSL and VirtualBox are like two different apps running on the same computer.

*   **WSL (Ubuntu/Debian):** Lives in a hidden utility VM managed by Windows.
    
*   **Kali VM:** Lives in a standard folder you created on `W:\VMs\`.
    

They use the same "engine" (the Windows Hypervisor Platform), so they can run at the exact same time without fighting for control of your hardware.

### 2\. "Will it stay in that folder?"

**Yes.** When you extract the Kali image and "Add" it to VirtualBox, everything Kali does - every tool you install, every file you save - stays inside a single large file (usually ending in `.vdi`) located in `W:\VMs\Kali-Linux\`.

*   **No Registry Bloat:** It won't scatter files across your Windows C:\\ drive.
    
*   **Portability:** If you ever get a new laptop, you can literally copy that `W:\VMs` folder to an external drive, plug it into the new PC, and your Kali setup will be exactly where you left it.
    

### 3\. Potential "Troubles" to Watch For (and how to fix them)

While they won't *break* each other, they do share your physical resources (RAM and CPU).

*   **RAM Usage:** If you give Kali 8 GB of RAM and Ubuntu is already using 4 GB, and Windows needs 4 GB... your system might slow down.
    
    *   **Fix:** Since you have a Home version of Windows 11, just make sure you don't run too many heavy apps (like **Chrome with 50 tabs**) while both Kali and WSL are active.
        
*   **Network Conflicts:** Sometimes, if you try to run a "Web Server" on Kali and a "Web Server" on WSL using the same port (like port 80), they might clash.
    
    *   **Fix:** In VirtualBox, use **"NAT"** mode for networking. This gives Kali its own private internal IP address separate from your Windows/WSL IP.
        

* * *

**Conclusion Glimpse**:

![](https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/0942b794-f825-48e7-882d-f6160c2203f3.png align="center")

## Set Up:

To ensure VirtualBox and WSL don't fight over your CPU, run this one command in your **PowerShell** (as Administrator) just to be 100% sure the required Windows feature is active:

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

o/p:

![](https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/53880b7b-bfce-4f86-b577-fafae41ec022.png align="center")

So opening PowerShell and running as an administrator:

confirm again-

![](https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/dab01e79-ef05-4447-a1c2-921c95cbf9eb.png align="center")

Now-

![](https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/bb93961a-a493-489d-baf9-ece0f9183a5d.png align="center")

\-> Click here for {[Set-Up Steps](https://ayushhardeniya.notion.site/set-up-steps-kali-linux)}

### Step-by-Step Execution:

1.  **Install VirtualBox:** Download the `.exe` and install it. If it asks for a location, just hit "Next" and let it go to C:\\ .
    
2.  **Redirect the Storage:** \* Open VirtualBox.
    
    *   Go to **File > Preferences > General**.
        
    *   Set **Default Machine Folder** to `W:\VMs`.
        
3.  **Setup Kali:**
    
    *   Manually create the folder `W:\VMs\Kali-Linux`.
        
    *   Extract your downloaded Kali `.7z` file **into** that folder.
        
    *   In the VirtualBox app, click **Machine > Add** and select the `.vbox` file from that folder on **W:**.
        

```powershell
For File > Preferences > General, you should set it to:

W:\VMs

Why not W:\VMs\Kali-Linux?

The "Default Machine Folder" is the parent folder where VirtualBox will look for all your virtual machines.

When you set it to W:\VMs, VirtualBox will treat that as the main "garage."

If you decide to install another OS later (like a Windows Server or another Linux flavor), VirtualBox will automatically create a new sub-folder for it inside W:\VMs (e.g., W:\VMs\WindowsServer).

If you pointed it directly to W:\VMs\Kali-Linux, things would get messy because VirtualBox would try to put files for other machines inside your Kali folder.
```

* * *

### The Final Folder Structure on W:\\

Once you are done, your drive will look like this:

*   `W:\WSL\` (Your existing Ubuntu/Debian)
    
*   `W:\VMs\` (The "Global" VM folder)
    
    *   `Kali-Linux\` (The specific folder where your Kali `.vbox` and `.vdi` files live)
        

* * *

### Quick Recap of the "Add" step:

1.  Set the Preference to `W:\VMs`.
    
2.  Click **Machine > Add**.
    
3.  Open **VirtualBox**.
    
4.  In the top menu, click **Machine** > **Add** (or press `Ctrl + A`).
    
5.  A file explorer window will open. Navigate to: `W:\VMs\Kali-Linux\kali-linux-2026.1-virtualbox-amd64\`
    
6.  Look for a file ending in `.vbox` (it usually has a blue cube icon and might be named `kali-linux-2026.1-virtualbox-amd64.vbox`).
    
7.  Select that file and click **Open**.
    

**Result:** Kali Linux will now appear in the left-hand sidebar of VirtualBox.

* * *

### 2\. Quick Hardware Check (For a CS Student's PC)

Before you hit Start, let's make sure it doesn't lag. Right-click the **Kali** entry in the list and select **Settings**:

*   **System > Processor:** Give it **2** or **4** cores. (Since you handle competitive programming and open-source projects, you'll want the speed).
    
*   **System > Motherboard:** Ensure it has at least **2048 MB (2 GB)** of RAM.
    
*   **Display > Video Memory:** Slide this to the max (**128 MB**). This makes the desktop environment much smoother.
    
*   **General > Advanced:** Set **Shared Clipboard** to **Bidirectional**. This is a lifesaver for copy-pasting code/commands from Windows.
    
    ![]( align="center")
    

* * *

### 3\. The "Ignition" (First Boot)

1.  Click the green **Start** arrow at the top.
    
2.  A new window will pop up. You’ll see some text scrolling - that’s the Linux kernel waking up.
    
3.  When you reach the login screen, enter the default credentials:
    
    *   **Username:** `kali` & **Password:** `kali`
        

**Result**:

![](https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/3d85dcb3-cc29-472d-ba56-ade53a70f5a3.png align="center")

* * *

![](https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/581e6a2c-25bd-4e96-a77e-fb02767bc21d.png align="center")

* * *

### Welcome to Dragon Mode {`Kali-Linux`}:

![](https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/78e2149f-54a6-4a25-bc6c-9cdb25856cd9.png align="center")

* * *

* * *

* * *

### How to Access it in future:

### 1\. The Standard Way (GUI)

Whenever you want to start hacking or practicing your CSE labs:

1.  Open **VirtualBox** from your Start Menu.
    
2.  Select **Kali-Linux** from the list on the left.
    
3.  Click the green **Start** arrow.
    
4.  **To Close it:** Don't just "X" out the window like a browser. Inside Kali, click the **Power icon** (top right) and select **Shut Down**. This ensures your virtual hard drive on **W:** doesn't get corrupted.
    

* * *

### 2\. The "Pro" Way (Save State)

If you are in the middle of a project (like a ZenYukti task or a DSA problem) and don't want to close your terminals:

1.  Click the **"X"** on the VirtualBox window i.e) close the VM window.
    
2.  Select **"Save the machine state"**.
    
3.  **Result:** VirtualBox will freeze Kali exactly where it is and save it to your **W:** drive. Next time you click Start, it will "wake up" in 2 seconds exactly where you left off.
    
    ![](https://cdn.hashnode.com/uploads/covers/68386d1121b9d74a4a2d7b62/4723355c-6fd5-4835-b2ad-4ea491aa1984.png align="center")
    

* * *

* * *

* * *