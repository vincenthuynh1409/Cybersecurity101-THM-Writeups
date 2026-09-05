# Windows Fundamentals (Part 2)

## System Configuration & Advanced System Settings

### System Configuration

The **System Configuration** utility (`MSConfig`) is for advanced troubleshooting, and its main purpose is to help diagnose startup issues. 

Reference the following document [here (opens in new tab)](https://docs.microsoft.com/en-us/troubleshoot/windows-client/performance/system-configuration-utility-troubleshoot-configuration-errors)for more information on the System Configuration utility. 

There are several methods to launch System Configuration. One method is from the Start Menu.

![](https://assets.tryhackme.com/additional/win-fun2/msconfig-start.png)

**Note**: You need local administrator rights to open this utility. 

The utility has five tabs across the top. Below are the names for each tab. We will briefly cover each tab in this task. 

1. General
2. Boot
3. Services
4. Startup
5. Tools

![](https://assets.tryhackme.com/additional/win-fun2/msconfig1.png)

In the **General** tab, we can select what devices and services for Windows to load upon boot. The options are: **Normal**, **Diagnostic**, or **Selective**. 

In the **Boot** tab, we can define various boot options for the Operating System. 

![](https://assets.tryhackme.com/additional/win-fun2/msconfig2.png)

The **Services** tab lists all services configured for the system regardless of their state (running or stopped). A service is a special type of application that runs in the background.  

![](https://assets.tryhackme.com/additional/win-fun2/msconfig3.png)

In the **Startup** tab, you won't see anything interesting in the attached VM.  Below is a screenshot of the Startup tab for **MSConfig** from my local machine. 

![](https://assets.tryhackme.com/additional/win-fun2/msconfig4.png)

As you can see, Microsoft advises using **Task Manager (**`taskmgr`**)** to manage (enable/disable) startup items. The System Configuration utility is **NOT** a startup management program. 

If you open the Task Manager for the attached VM, you will notice that it doesn't display a Startup tab. You will also not see anything in the Startup tab inside the `msconfig` utility, as shown above. This is because the attached machine is a Windows server, and Windows servers handle startup applications differently than Windows client systems. Unlike Windows 10 or 11, you will not see startup programs in `Task Manager` or in the Startup tab of `msconfig`. On these Windows server machines, the only reliable way to view user-level startup items is through the Startup folder itself. You can access it by pressing `**Win + R**`, which opens the Run Dialog, typing **`shell:startup`**, and then pressing Enter. This will display all startup programs as shortcuts or executables that are configured to run automatically the next time a user logs in. This is where you can verify applications that are configured to launch at startup. Below is a screenshot of the startup folder from another Windows server (not from the attached VM):

![](https://cdn-images.tryhackme.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764766867993.png)

Now coming back to the `msconfig`. There is a list of various utilities (tools) in the Tools tab here that we can run to configure the operating system further. There is a brief description of each tool to provide some insight into what the tool is for. 

![](https://assets.tryhackme.com/additional/win-fun2/msconfig5.png)

Notice the **Selected command** section. The information in this textbox will change per tool.

To run a tool, we can use the command to launch the tool via the run prompt, command prompt, or by clicking the `Launch` button. 

### Advanced System Settings

Windows gives you some additional configuration settings as well, which you can use to control the performance behavior and system recovery. To access this option, you can search for `View advanced system settings` in your search bar and open it. This will open a `System Properties` panel as shown below:

![](https://cdn-images.tryhackme.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764846840046.png)

Windows uses a page file as an extra virtual memory space when the physical RAM becomes full. This helps to prevent slowdowns or application crashes when the system runs out of memory. You can view or modify the page file by navigating to the `Advanced` option at the top and clicking `Settings` under the `Performance` tab.

![](https://cdn-images.tryhackme.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764846840021.png)

So after clicking the Settings, you will get the Performance Options window, as can be seen below:

![](https://cdn-images.tryhackme.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764846840008.png)

 In this Performance tab, the **Advanced** option can also tell you about the page file size configured for the drives. In this case, it's `1048 MB`. The other settings here can give you the following information:

- The drive where the page file is stored
- The initial size (MB)
- The maximum size
- Whether Windows manages the size automatically

There is another cool configuration that you can find in the Advanced System Settings. It is known as Startup and Recovery. Windows can create a crash dump file whenever it encounters a critical error, such as a Blue Screen of Death. This crash dump helps the administrators or analysts understand what went wrong during the crash. You can view or modify the crash dump settings by navigating to the `Advanced` option at the top and then clicking `Settings` under the `Startup and Recovery` section.

![](https://cdn-images.tryhackme.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764852718826.png)

So after clicking the settings, you will see the `Startup and Recovery` window, as shown below:

![](https://cdn-images.tryhackme.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764852718742.png)

Here, you will find different settings for the startup and recovery. The `Write debugging information` dropdown tells you the type of crash dump configured for the system. Windows supports different dump types, such as:

- Automatic memory dump
- Kernel memory dump
- Small memory dump (256 KB)
- Complete memory dump
- None

This setting shows how much information Windows will save in the crash dump when a system crash occurs.

### Task 2 Questions:

*Q1) What is the name of the service that lists Systems Internals as the manufacturer?*

1.  use the app “run” and type “msconfig”.
2. click services tab

![](https://miro.medium.com/v2/resize:fit:601/1*78uquipWbNsJDiqbdfeyHw.png)

![](https://miro.medium.com/v2/resize:fit:840/1*3Cdm2w-1p_S_7K8NjdIWqw.png)

**ANSWER:** `PsShutdown`

*Q2) Whom is the Windows license registered to?*  

1. on msconfig, go to the tools tab
2. launch "About Windows"

<img width="1573" height="633" alt="image" src="https://github.com/user-attachments/assets/3c3792b6-52d7-4549-91f6-aa64a6ebda23" />


**ANSWER:** `Windows User`

*Q3) What is the command for Windows Troubleshooting?*

<img width="854" height="581" alt="image" src="https://github.com/user-attachments/assets/86b38d95-f466-4603-8401-ef3ff80b3629" />


**ANSWER:** `C:\Windows\System32\control.exe /name Microsoft.Troubleshooting`

*Q4) What command will open the Control Panel? (The answer is the name of .exe, not the full path)*

1. click "System Properties"

<img width="853" height="579" alt="image" src="https://github.com/user-attachments/assets/38cbd576-7aa0-4173-bcf0-7b847d391c64" />


**ANSWER:** `control.exe`


<br>

## Change UAC Settings

We're continuing with Tools that are available through the **System Configuration** panel.

**User Account Control** (UAC) was covered in great detail in [Windows Fundamentals 1](https://tryhackme.com/room/windowsfundamentals1xbx). 

The UAC settings can be changed or even turned off entirely (not recommended). You can move the slider to see how the setting will change the UAC settings and Microsoft's stance on the setting.

This slider has four security levels, each of which controls how Windows alerts you when apps or users try to make changes at the system level. They fall into four standard categories as explained below:

- **Always notify:** This is the highest security. Windows notifies you whenever any apps or you yourself try to make changes, and the desktop dims (Secure Desktop).
    
- **Notify for apps**: Windows notifies only when _apps_ try to make changes, but not when you change Windows settings. This option is enabled by default.
    
- **Notify without dimming:** Same as above (Notify for apps), but this time the screen does not dim. 
    
- **Never notify:** Notifications are turned off. Windows won’t warn you about any changes made by you or any apps. 
    

You can find the current level by looking at the position of the slider in the `User Account Control settings` window, as shown below:

![](https://assets.tryhackme.com/additional/win-fun2/uac.png)

### Task 3 Questions:

*Q1) What is the command to open User Account Control Settings? (The answer is the name of the .exe file, not the full path)*

**ANSWER:** `UserAccountControlSettings.exe`

<br>

## Computer Management

We're continuing with tools that are available through the System Configuration panel.

The **Computer Management** (`compmgmt`) utility has three primary sections: System Tools, Storage, and Services and Applications.

![](https://assets.tryhackme.com/additional/win-fun2/compmgmt1.png)

**System Tools**

Let's start with **Task Scheduler**. Per Microsoft, with Task Scheduler, we can create and manage common tasks that our computer will carry out automatically at the times we specify.

A task can run an application, a script, etc., and tasks can be configured to run at any point. A task can run at log in or at log off. Tasks can also be configured to run on a specific schedule, for example, every five mins.

To view the scheduled tasks that are present on the system, click `Task Scheduler Library`. This will display all the scheduled tasks of the system. You can click on any of them to view their details. The screenshot below shows a scheduled task named `SystemInfoDailyLog` configured to run `every day at 10:00 AM`. Here, you will see the program or command that will run when the task is triggered.

![](https://cdn-images.tryhackme.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764761078608.png)

It is also important to note that some scheduled tasks are not recurring and are made to run just once at a specific time. In this case, we would see something like `At 2:50 PM on 6/15/2025` as the trigger.

To create a basic task, click on `Create Basic Task` under **Actions** (right pane).

![](https://assets.tryhackme.com/additional/win-fun2/create-task.png)

Next is **Event Viewer**.

Event Viewer allows us to view events that have occurred on the computer. These records of events can be seen as an audit trail that can be used to understand the activity of the computer system. This information is often used to diagnose problems and investigate actions executed on the system. 

![](https://assets.tryhackme.com/additional/win-fun2/event-viewer.png)

Event Viewer has three panes.

1. The pane on the left provides a hierarchical tree listing of the event log providers. (as shown in the image above)
2. The pane in the middle will display a general overview and summary of the events specific to a selected provider.
3. The pane on the right is the actions pane.

There are five types of events that can be logged. Below is a table from [docs.microsoft.com(opens in new tab)](https://docs.microsoft.com/en-us/windows/win32/eventlog/event-types) providing a brief description for each.

![](https://assets.tryhackme.com/additional/win-event-logs/five-event-types.png)

The standard logs are visible under Windows Logs. Below is a table from [docs.microsoft.com(opens in new tab)](https://docs.microsoft.com/en-us/windows/win32/eventlog/eventlog-key) providing a brief description for each.

![](https://assets.tryhackme.com/additional/win-event-logs/standard-event-logs.png)

For more information about Event Viewer and Event Logs, please refer to the Windows Event Log [room](https://tryhackme.com/room/windowseventlogs). 

**Shared Folders** is where you will see a complete list of shares and folders shared that others can connect to. 

![](https://assets.tryhackme.com/additional/win-fun2/shared-folders.png)

In the above image, under Shares, are the default share of Windows, C$, and default remote administration shares created by Windows, such as ADMIN$. 

As with any object in Windows, you can right-click on a folder to view its properties, such as Permissions (who can access the shared resource). 

Under **Sessions**, you will see a list of users who are currently connected to the shares. In this VM, you won't see anybody connected to the shares.

All the folders and/or files that the connected users access will list under **Open Files**.

The **Local Users and Groups** section you should be familiar with from [Windows Fundamentals 1](https://tryhackme.com/room/windowsfundamentals1xbx) because it's `lusrmgr.msc`.

In **Performance**, you'll see a utility called **Performance Monitor** (`perfmon`).

Perfmon is used to view performance data either in real-time or from a log file. This utility is useful for troubleshooting performance issues on a computer system, whether local or remote. 

![](https://assets.tryhackme.com/additional/win-fun2/perfmon.png)

**Device Manager** allows us to view and configure the hardware, such as disabling any hardware attached to the computer.

![](https://assets.tryhackme.com/additional/win-fun2/device-mgr.png)

**Storage**  

Under Storage is **Windows Server Backup** and **Disk Management**. We'll only look at Disk Management in this room.

**Note**: Since the lab machine is a Windows Server operating system, there are utilities available that you will typically not see in Windows 10.  

![](https://assets.tryhackme.com/additional/win-fun2/disk-mgmt.png)

Disk Management is a system utility in Windows that enables you to perform advanced storage tasks.  Some tasks are:

- Set up a new drive
- Extend a partition
- Shrink a partition
- Assign or change a drive letter (ex. E:) 

**Services and Applications**

Recall from the previous task, a service is a special type of application that runs in the background. You can see all the services and their statuses by clicking the Services button given under the Services and Applications section, as shown below:

![](https://cdn-images.tryhackme.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764762861185.png)

The services shown above have their display names, status, and other values. If you want to get more information about any service, right-click on the service and click `properties`. Here, you will see additional details, such as the service name (which differs from the display name), the path to its executable, its startup type, and other relevant information.

![](https://assets.tryhackme.com/additional/win-fun2/service.png)

There is a field known as Startup type in a service’s Properties window, as shown above. It determines how and when the service is configured to start. We can set a service to `Automatic`, which means it starts every time the system boots, or `Manual`, which means it only starts when another process or user triggers this service, or `Disabled`, which means it should not run at all. The service shown in the screenshot above is set to `Automatic`.

WMI Control configures and controls the **Windows Management Instrumentation** (WMI) service.

Per Wikipedia, "_WMI allows scripting languages (such as VBScript or Windows PowerShell) to manage Microsoft Windows personal computers and servers, both locally and remotely. Microsoft also provides a command-line interface to WMI called Windows Management Instrumentation Command-line (WMIC)._"

**Note**: The WMIC tool is deprecated in Windows 10, version 21H1. Windows PowerShell supersedes this tool for WMI. 

### Task 4 Questions:

*Q1) What is the command to open Computer Management?*  
*(The answer is the name of the .msc file, not the full path)*

<img width="853" height="577" alt="image" src="https://github.com/user-attachments/assets/aec93c4f-572e-4b01-a044-eb1d5d5bf790" />


**ANSWER:** `compmgmt.msc`

*Q2) When is the `npcapwatchdog` scheduled task set to run at?*

1. use the app “run” and type “**compmgmt.msc**”. 
2. Press enter or click to view image in full size
3. go to System Tools > Task Scheduler > Task Scheduler Library.

![](https://miro.medium.com/v2/resize:fit:607/1*I9vO-izxqG6moRHuNr9eyQ.png)

<img width="1478" height="1060" alt="image" src="https://github.com/user-attachments/assets/e5eb4a40-68df-4107-a5b3-718097260f25" />


**ANSWER:** `At System Startup`

*Q3) What is the name of the hidden folder that is shared?*

**ANSWER:** `sh4r3dF0Ld3r`

<br>

## System Information

We're continuing with Tools that are available through the System Configuration panel.

What is the **System Information** (`msinfo32`) tool?

Per Microsoft, "_Windows includes a tool called Microsoft System Information (Msinfo32.exe).  This tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which you can use to diagnose computer issues._"

The  information in **System Summary** is divided into three sections:

- **Hardware Resources**
- **Components**
- **Software Environment**

System Summary will display general technical specifications for the computer, such as processor brand and model.

![](https://assets.tryhackme.com/additional/win-fun2/system-summary.png)

The information displayed in **Hardware Resources** is not for the average computer user. If you want to learn more about this section, refer to the official Microsoft [page(opens in new tab)](https://docs.microsoft.com/en-us/windows-hardware/drivers/kernel/hardware-resources#:~:text=Hardware%20resources%20are%20the%20assignable,of%20bus%2Drelative%20memory%20addresses.).

![](https://assets.tryhackme.com/additional/win-fun2/hardware-resources.png)

Under **Components**, you can see specific information about the hardware devices installed on the computer. Some sections don't show any information, but some sections do, such as **Display** and **Input**.

![](https://assets.tryhackme.com/additional/win-fun2/components.png)

In the **Software Environmen**t section, you can see information about software baked into the operating system and software you have installed. Other details are visible in this section as well, such as the **Environment Variables** and **Network Connections**. 

![](https://assets.tryhackme.com/additional/win-fun2/software-env.png)

Recall from the [Windows Fundamentals 1 room](https://tryhackme.com/room/windowsfundamentals1xbx) (The Windows\System32 Folder task) where **Environment Variables** was briefly touched on. 

Per [Microsoft(opens in new tab)](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.1), "_Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders._

_The environment variables store data that is used by the operating system and other programs. For example, the WINDIR environment variable contains the location of the Windows installation directory. Programs can query the value of this variable to determine where Windows operating system files are located_".

Click on `Environment Variables` to see the assigned values for the lab machine.

![](https://assets.tryhackme.com/additional/win-fun2/env-variables.png)

Another method to view environment variables is `Control Panel > System and Security > System > Advanced system settings > Environment Variables` **OR** `Settings > System > About > system info > Advanced system settings > Environment Variables`.

![](https://assets.tryhackme.com/additional/win-fun2/env-variables2.png)

The detour is over. Let's redirect our attention back to `msinfo32` and pick up where we left off.

Towards the very bottom of this utility, there is a search bar. Please give it a go. Select Components and search for `IP address`.

![](https://assets.tryhackme.com/additional/win-fun2/msinfo32-search.png)

### Task 5 Questions:

*Q1) What is the command to open System Information? (The answer is the name of the .exe file, not the full path)*

1. use the app "run", and type "msconfig"
2. find "System Information"

<img width="854" height="574" alt="image" src="https://github.com/user-attachments/assets/f75cd969-ff9e-48b8-8e0c-d05dacf5acfb" />


**ANSWER:** `msinfo32.exe`

*Q2) What is listed under System Name?*

1. launch "System Information"
2. find "System Name"

<img width="1742" height="974" alt="image" src="https://github.com/user-attachments/assets/34e7cb88-dc12-4b09-b37d-74f505c7224e" />


**ANSWER:** `THM-WINFUN2`

*Q3) Under Environment Variables, what is the value for ComSpec?*

1. select and click "Software Environment" folder
2. find "Environment Variables" subfolder
3. then find the value for ComSpec

<img width="1743" height="972" alt="image" src="https://github.com/user-attachments/assets/d292b747-4802-4cc4-bb47-d23f78787548" />


**ANSWER:** `%SystemRoot%\system32\cmd.exe`


<br>

## Resource Monitor

We're continuing with Tools that are available through the System Configuration panel.  

What is **Resource Monitor** (`resmon`)?

Per Microsoft, "_Resource Monitor displays per-process and aggregate CPU, memory, disk, and network usage information, in addition to providing details about which processes are using individual file handles and modules. Advanced filtering allows users to isolate the data related to one or more processes (either applications or services), start, stop, pause, and resume services, and close unresponsive applications from the user interface. It also includes a process analysis feature that can help identify deadlocked processes and file locking conflicts so that the user can attempt to resolve the conflict instead of closing an application and potentially losing data._"

As some of the other tools mentioned in this room, this utility is geared primarily to advanced users who need to perform advanced troubleshooting on the computer system.  

In the Overview tab, Resmon has four sections:

- **CPU**
- **Disk**
- **Network**
- **Memory**

![](https://assets.tryhackme.com/additional/win-fun2/resmon1.png)  

The same four sections have corresponding tabs across the top. See below.

![](https://assets.tryhackme.com/additional/win-fun2/resmon2.png)  

Note that each tab has additional information for each. An image is shown below for each tab. 

**CPU**

![](https://assets.tryhackme.com/additional/win-fun2/resmon-cpu.png)  

**Memory**

![](https://assets.tryhackme.com/additional/win-fun2/resmon-mem.png)  

**Disk**

![](https://assets.tryhackme.com/additional/win-fun2/resmon-disk.png)  

**Network**

![](https://assets.tryhackme.com/additional/win-fun2/resmon-network.png)  

Although not captured in any of the images above, Resource Monitor has a pane at the far right. This pane shows a graphical view in real-time for each section. 

**Note**: The information displayed in Resource Monitor will be different for you compared to the images above.  

### Task 6 Questions:

*Q1) What is the command to open Resource Monitor? (The answer is the name of the .exe file, not the full path)*

<img width="849" height="576" alt="image" src="https://github.com/user-attachments/assets/15ef8650-3567-4148-93c9-176a37880fa4" />


**ANSWER:** `resmon.exe`

<br>

## Command Prompt

We're continuing with Tools that are available through the System Configuration panel.  

The command prompt (`cmd`) can seem daunting at first, but it's really not that bad once you understand how to interact with it. 

In early operating systems, the command line was the sole way to interact with the operating system.

When the GUI (graphical user interface) was introduced, it allowed users to perform complex tasks with a few clicks of a button instead of entering commands in the command prompt. 

Even though the GUI is the primary way to interact with the operating system, a computer user can still interact via the command prompt. 

In this task, we'll only cover a few commands that a computer user can run in the command prompt to obtain information about the computer system.

Let's start with a few simple commands, such as `hostname` and `whoami`.

The command **hostname** will output the computer name.

![](https://assets.tryhackme.com/additional/win-fun2/hostname.png)  

The command **whoami** will output the name of the logged-in user.

![](https://assets.tryhackme.com/additional/win-fun2/whoami.png)  

Next, let's look at some commands that are useful when troubleshooting.

A command used often is `ipconfig`. This command will show the network address settings for the computer.

![](https://assets.tryhackme.com/additional/win-fun2/ipconfig.png)  

Each command will have a help manual to explain the expected syntax to execute the command properly, along with any additional parameters that can be added to the command to expand its execution.

A  command to retrieve the help manual for a command is `/?`.

For example, to see the help manual for **ipconfig**, you can use the following command: `ipconfig /?`

![](https://assets.tryhackme.com/additional/win-fun2/ipconfig-help.png)  

**Note**: To clear the command prompt screen, the command is `cls`. 

The next command is `netstat`. Per the help manual, this command will display protocol statistics and current TCP/IP network connections. 

![](https://assets.tryhackme.com/additional/win-fun2/netstat.png)  

In the above image, the line within the red box shows us an example syntax for the command. 

The structure tells us the **netstat** command can be run alone or with parameters, such as `-a`,  `-b`,  `-e`, etc. 

When any of the parameters are appended to the root command, **netstat** in this case, the output changes. Play with a few to see for yourself. 

The `net` command is primarily used to manage network resources. This command supports sub-commands.

If you type **net** without a sub-command, the output will show the syntax for the root command showing a few of the sub-commands you can use.

![](https://assets.tryhackme.com/additional/win-fun2/net.png)  

For the net command, to display the help manual `/?` will not work. In this case, you need to use different syntax, which is `net help`.

![](https://assets.tryhackme.com/additional/win-fun2/net-help.png)  

So, if you wish to see the help information for `net user` , the command is `net help user`. 

![](https://assets.tryhackme.com/additional/win-fun2/net-help-user2.png)

You can use the same command to view the help information for other useful **net** sub-commands, such as **localgroup**, **use**, **share**, and **session**. 

Refer to the following link to see a comprehensive list of commands you can execute in the command prompt [here(opens in new tab)](https://ss64.com/nt/).   

### Task 7 Questions:

*Q1) In System Configuration, what is the full command for Internet Protocol Configuration?*

<img width="851" height="575" alt="image" src="https://github.com/user-attachments/assets/b9f15f18-70d4-4072-b33a-70eec71b82c1" />


**ANSWER:** `C:\Windows\System32\cmd.exe /k %windir%\system32\ipconfig.exe`

*Q2) For the ipconfig command, how do you show detailed information?*

1. launch "Internet Protocol Configuration" (opens terminal)
2. type `ipconfig /all`

<img width="1322" height="722" alt="image" src="https://github.com/user-attachments/assets/e35eea2b-6f20-4d77-a0fc-58a74ef6c76a" />


**ANSWER:** `ipconfig /all`

<br>

## Registry Editor

We're continuing with Tools that are available through the System Configuration panel.  

The **Windows Registry** (per Microsoft) is a central hierarchical database used to store information necessary to configure the system for one or more users, applications, and hardware devices.

The registry contains information that Windows continually references during operation, such as:

- Profiles for each user
- Applications installed on the computer and the types of documents that each can create
- Property sheet settings for folders and application icons
- What hardware exists on the system
- The ports that are being used.

**Warning**: The registry is for advanced computer users. Making changes to the registry can affect normal computer operations. 

There are various ways to view/edit the registry. One way is to use the **Registry Editor** (`regedit`).

![](https://assets.tryhackme.com/additional/win-fun2/regedit.png)  

Refer to the following Microsoft documentation [here(opens in new tab)](https://docs.microsoft.com/en-us/troubleshoot/windows-server/performance/windows-registry-advanced-users) to learn more about the Windows Registry. 

### Task 8 Questions:

*Q1) What is the command to open the Registry Editor? (The answer is the name of  the .exe file, not the full path)*

<img width="856" height="571" alt="image" src="https://github.com/user-attachments/assets/06c8577f-0ebb-41cb-80ce-bdaf0aaa836c" />


**ANSWER:** `regedt32.exe`

