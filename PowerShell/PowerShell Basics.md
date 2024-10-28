# Part 1: Navigation and File/Folder Management

In this part of the lab, you will learn some basic cmdlets for navigating PowerShell and management files and folders.

1. On the taskbar, right-click the Start icon and select Windows PowerShell (Admin) to open a PowerShell window with admin privileges.  
    When prompted, click Yes to continue.  
      
    First, let's find out just how many cmdlets are currently available in PowerShell.  
    
2. At the PowerShell prompt, type Get-Command -Type Cmdlet | Measure-Object | Select-Object Count and press Enter.  
      
    Take note of the number of cmdlets shown.  
    The point of this exercise is to show that you simply cannot memorize all possible PowerShell cmdlets. The best way for PowerShell to stick with you is to start using it for everyday tasks.  Over time you will master the most common and useful cmdlets for your use case.  
      
    Note: For the most part, Windows is case-insensitive. You should feel free to use all lowercase if you prefer.  
    
3. At the PowerShell prompt, type Get-Help Get-Command and press Enter to view help on the Get-Command cmdlet.  
    When prompted, type Y and press Enter to continue.  
      
    Get-Help is similar to the Linux man pages. Get-Help will explain what a cmdlet does and its syntax.  
      
    Pay attention to the REMARKS section at the bottom. PowerShell is telling us that Get-Help is not up-to-date.  
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/2p2fYneSv5XJi3RrqRpFne/db8fa2ccda004e58499015cce4bd0375/psb_010.png)
    
4. At the PowerShell prompt, type Update-Help and press Enter to update Get-Help.  
      
    It will take a few minutes for Get-Help to update fully.  
      
    Note: You may see one or more errors during and after updating Get-Help. You can ignore these errors.  
    
5. At the PowerShell prompt, type Get-Help Get-Command and press Enter again.  
      
    This time you will see a full help listing for the Get-Command cmdlet.  
    
6. At the PowerShell prompt, type Get-Help Get-Command -Examples and press Enter to see examples of how to use the Get-Command cmdlet.  
      
    As busy administrators, we love to have Google show us everything. Nonetheless, Get-Help is a tremendous resource for learning PowerShell.  
    If typing is not your thing, you will be happy to learn that PowerShell supports aliases.  An alias is a shorter way to issue a cmdlet. Recall the Get-Location cmdlet shown above. Let's see if there is an alias for this.  
    
7. At the PowerShell prompt, type Get-Alias -Definition Get-Location and press Enter to display the aliases for the Get-Command cmdlet.  
    Take note of the two aliases for Get-Location.  
    
8. Is there an alias for Get-Alias? Execute Get-Alias -Definition Get-Alias to find out.  
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/1h2KxyQRMxCFN9SIWDDSRJ/71e6952ee273d6f74582ef9a58e35e21/psb_011.png)
    
    Note: Feel free to substitute the alias for any cmdlet used throughout this lab.  
    
9. At the PowerShell prompt, execute Get-Alias | More to display all of the current PowerShell aliases on the lab server.  
      
    You may need to press the Space Bar a few times to finish scrolling through the list.  
    Notice that many aliases match Linux commands like pwd, curl, mount, mv, cd, etc. Maybe Microsoft wanted Linux administrators to be more comfortable using PowerShell?  
      
    Note: Remember, the alias points to the cmdlet, not vice versa. For example, Set-Location is the command; cd is the alias. PowerShell is not a simple wrapper around legacy command line tools.  
    
10. At the PowerShell prompt, execute Set-Location C:\Users\cybrary to navigate to the Cybrary user's home directory.  
    
11. At the PowerShell prompt, execute Get-ChildItem to display a listing of the directories and files in the current directory.  
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/6MN9ILX9osYjtlzqxtWpzX/85c9ae62fdbd9b41a603edf220dbf2c4/psb_012.png)
    
12. At the PowerShell prompt, execute Get-ChildItem | Sort-Object LastWriteTime to sort the files and folders under C:\Users\cybrary by the Last Write Time.  
    
13. At the PowerShell prompt, execute Get-ChildItem C:\ to display a listing of the directories and files in the C:\ directory.  
      
    As you can see, when using Get-ChildItem, you don't have to be currently located in a specific directory to see the contents.  
    
14. Execute Get-ChildItem C:\Windows\System32 *.txt to list all text files in C:\Windows\System32.  
    
15. Execute Get-ChildItem C:\Windows\System32 *.dll to list all DLL files in C:\Windows\System32.  
    
16. Execute Get-ChildItem C:\Windows\System32 *.dll | Measure-Object to count how many DLL files there are.  
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/2aaNo3qlfMixXkzBDcwWQF/82d97e6b990a81075016b6a1b0d98114/psb_013.png)
    
17. Execute Set-Location C:\Users\cybrary\Desktop to move to the Desktop.  
    
18. Execute Set-Content Hello.txt "Hello" to create a new text file called Hello.txt on the Desktop containing the word Hello.  
      
    Note:  You may see this command written as Set-Content -Path Hello.txt -Value "Hello" in examples online. The -Path and -Value parameters are optional but add clarity for those who love to type.  
    
19. Execute Get-Content Hello.txt to read the Hello.txt file.  
    
20. Execute Add-Content Hello.txt "Goodbye" to append Goodbye to the Hello.txt text file.  
    Validate this with Get-Content.  
    
21. Execute $Hello = Get-Content Hello.txt to put the contents of Hello.txt into a variable called $Hello.  
    
22. Append the .GetType() method to $Hello to see what type of data structure $Hello is.  
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/3qxaF2cFK8x2jlmlRnQonk/acf5eb600c61765dbcb3770bfe583552/psb_014.png)
    
    Notice $Hello is an array. An array is a collection of items of the same data type stored at contiguous memory locations, which you can reference by their numerical location. Because this is an array, we should be able to access each item by its reference number (e.g., 0, 1, 2, etc.).  
    
23. Execute $Hello.Item(0) to see the first array item.  
      
    Execute $Hello.Item(1) to see the second item in the array $Hello.  
    
24. Execute New-Item File1.txt to create an empty file named File1.txt on the Desktop.  
    
25. Execute Add-Content File1.txt "This is file 1." to add text to File1.txt.  
    Use Get-Content to confirm.  
    
26. Execute Copy-Item File1.txt File2.txt to make a copy of File1.txt.  
    Use Get-Content to confirm.  
    
27. Execute Move-Item File2.txt File3.txt to rename File2.txt.  
      
    Note: You can also use the Rename-Item cmdlet.  
    
28. Execute New-Item -ItemType Directory Folder1 to create a new folder on the Desktop.  
    
29. Execute Move-Item File*.* Folder1 to move File1.txt and File3.txt to Folder1.  
    Validate with Get-ChildItem.  
    
30. Execute Test-Path Folder1 and to test if Folder1 exists.  
    Notice the output is True.  
    
31. Execute Test-Path Folder1\File1.txt to test if File1.txt exists.  
      
    Notice the output is True.  
    
32. Execute Test-Path Folder1\File2.txt to test if File2.txt exists.  
    Notice the output is False.  
    
33. Execute Remove-Item -Recurse -Force Folder1 to remove the Folder1 folder and all its contents.  
    Validate that the folder and files are gone using Test-Path.

# Part 2: Gathering Information

Now that we have learned how to move around and manage files and folders, let's see what PowerShell can do for gathering information.

1. Execute Get-ComputerInfo and Press Enter to see detailed information about your system.  
    
2. Execute Get-ComputerInfo -Property *version to see only the version numbers associated with the lab server.  
    
3. Execute Get-CimInstance -ClassName Win32_ComputerSystem to see the lab system name and domain membership.  
    
4. Execute Get-CimInstance -ClassName Win32_Processor to see CPU information.  
    
5. Execute Get-CimInstance -ClassName Win32_PhysicalMemory | Select-Object Capacity to see system memory.  
    
6. Execute Get-CimInstance -ClassName Win32_LogicalDisk to see the lab server's allocated SSD size and free space.  
    
7. Execute Get-CimInstance -ClassName Win32_UserAccount to display local users.  
    
8. Execute Get-CimInstance -ClassName Win32_Group to display local groups.  
      
    Note: You can also use the Get-LocalUser and GetLocalGroup cmdlets for listing users and groups.  
    
9. Execute Get-Process -Verbose to see a list of all running processes and the current CPU usage of each.  
      
    Note: You can stop and start processes with the Stop-Process and Start-Process cmdlets.  
    
10. Execute Get-Service | Where-Object Status -EQ Running to display all running services on the lab server.  
    
11. Execute Get-Service | Where-Object Status -EQ Stopped to display all stopped services on the lab server.  
      
    Note: The Get-Service cmdlet by itself command will show you all services running, stopped, and disabled.  
    
12. Execute Get-EventLog -LogName Application -Newest 10 to see the ten most recent Application log events.  
    
13. Execute Get-EventLog -LogName Security -EntryType FailureAudit to see all the audit failures in the Security Event log.  
    
14. Execute Get-EventLog -LogName Security -InstanceID 4625 to list the account logon failures.  
      
    Note: Trying to read individual Event Log messages via PowerShell is cumbersome. However, using PowerShell to find logs of interest (like logon failures, etc.) across many systems is an effective use of the tool.  
    What if we wanted to use PowerShell to audit other systems on the network? Connecting to each system takes time and effort. With PowerShell, all you need to add is the -ComputerName parameter to a given command to run this command on a remote system. For example, to check for login failures on a system named SuperMoo, we would use the following:  
    Get-EventLog -ComputerName SuperMoo -LogName Security -InstanceID 4625  
    What if we wanted to check login failures on several computers? Here is an example of how that could look:  
      
    First, create an array of computer names:  
    $Computers = "Server1","Server2","Server3"  
    Then create a simple loop using Foreach:  
    Foreach ($Computer in $Computers) {Get-EventLog -ComputerName $Computer -LogName Security -InstanceID 4625  
    }
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/2WLkfHnZwihae9Z1bJsQ5U/cdbf1948ef9b1d6c8dcc2e9753907d5f/psb_026.png)
    
    Note: You must have permission to run PowerShell on all the remote servers.  
      
    Feel free to try this script in the lab, but you will get failures as the remote computers do not exist.  
    Not every cmdlet has a -ComputerName parameter. In cases where -ComputerName is unavailable, you can use Invoke-Command as shown in the example below.  
    $Computers = "Server1","Server2","Server3"  
    $Command = {Get-EventLog -LogName Security -InstanceID 4625}  
    Foreach ($Computer in $Computers) {  
    Invoke-Command -ComputerName $Computer -ScriptBlock $Command  
    }
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/48JvPESPUNMnLrS6ZBsh0D/d80b5d0e21a4b809a2f565a14a329822/psb_025.png)
    
    Note: Using Invoke-Command is much faster than relying on the -ComputerName parameter in a cmdlet and is typically preferred by administrators.  
    An amazing feature of PowerShell is that it is extensible. New tools are developed every day to make administration tasks easier. PowerShell even allows us to import new features on demand. For example, what if we want to check if our lab server is fully updated? A Google search might yield the intuitively named Get-WindowsUpdate cmdlet.
15. Execute Get-WindowsUpdate to check if your lab server is fully updated.  
      
    Uh oh, we get an error.  
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/5aXi8puxAI4WC8djjB9V3F/dd00ebdfbb91a06f0f70e7ad6c4b8db9/psb_024.png)
    
    To fix this, we need to import the module that enables this cmdlet. In the case of the Get-WindowsUpdate cmdlet, the module we need is PSWindowsUpdate.  
    
16. Execute Install-Module PSWindowsUpdate to install the PSWindowsUpdate module.  
    When prompted, type Y and press Enter. The module can take up to 90 seconds to install.  
      
    Note:  Those who are security conscious may wonder about installing modules from an untrusted repository. Many honest developers are creating valid and useful tools for PowerShell administration. Ultimately you will need to decide if using something not strictly from Microsoft is worth the risk.  
    
17. Once the new module is installed, execute Get-WindowsUpdate to display available updates for the lab server.  
    
18. Close the PowerShell window.

# Part 3: PowerShell Scripting

Let's talk about scripting in PowerShell. Running scripts directly from the command line is ok for small jobs, but you will want to use an editor for most real work. Many admins simply use Notepad or the paid version of Notepad++. Microsoft provides two other environments to ease PowerShell development: ISE and Visual Studio Code.  
  
Note: ISE is depreciated as Microsoft wants to move all future PowerShell scripting into Visual Studio.

1. On the taskbar, type ise in the Search field, then select Windows PowerShell ISE from the results to open the integrated scripting environment.  
    
2. At the PowerShell prompt, execute Get- and wait.  
      
    You should see a pop-up window with cmdlet suggestions provided by Intellisense.  
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/2hk0XRclBFSVywauFsnSzc/2e0bb62463041e8644790b8bb759aa51/psb_015.png)
    
      
    Note: Sometimes, Intellisense times out on an EC2 image. Simply try again if it does not work the first time.  
    
3. Click View, then check Show Script Pane.  
      
    You should now have two open panes in ISE: a notepad-like environment for writing scripts (top) and a PowerShell terminal for viewing the results (bottom).  
      
    In the next steps, we will create a network ping utility using the ISE.  
    
4. In the Script pane (top), type the following:  
    $Websites = 'google.com', 'microsoft.com', 'cybrary.it'  
    Foreach ($Site in $Websites) {  
    Test-Connection -ComputerName $Site  
    }
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/5mBeMQ1kpVKYHymssYZpdb/952a411bd41af2979d50c2193244d740/psb_016.png)
    
    This script creates an array with three websites, then uses a simple loop (ForEach) to ping (Test-Connection) each site.
5. On the ISE toolbar, click the green Run arrow to run the script.  
      
    Observe the results in the PowerShell (bottom) pane. Notice that when a site does not respond to ICMP, there is an ugly error.  
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/5CiQcLG6WqJgPBaaWAAaYi/37ed16de9230d5b80e01a7c25bf89fd8/psb_017.png)
    
6. Modify the script to use the -Quiet parameter for the Test-Connection cmdlet.  
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/73LoJtafC461hToNcLrHDR/4a4bcc8a24e289a186066b3ee57c9377/psb_018.png)
    
    Notice the difference in output. If the site responds to a ping request, then the output is True and False when it doesn't. Also, notice that the ISE echoes the entire script before it runs.
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/7nqpVXOIIfsCFTuiQtulWO/08b04315d398d7072beee5f0b44fe7be/psb_019.png)
    
7. Click File > Save As… and name the new file ping.ps1.  
    
8. Rerun the script after saving it.  
      
    Notice that after saving the script, there is no echo.  
      
    Note: Because this echo "feature" is annoying, most admins save the script they are working on before testing.  
    
9. Modify the ping script by adding an If / Else statement, as shown below.  
    $Websites = 'google.com', 'microsoft.com', 'cybrary.it'  
      
    Foreach ($Site in $Websites) {  
    If (Test-Connection -ComputerName $Site -Quiet) {  
    Write-Host "$Site is pingable"  
    } Else {  
    Write-Host "$Site is not pingable"  
    }  
    }  
    If the output from Test-Connection is True, we write out that the host is pingable. If False, we write out that the host is not.
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/2CFGkrKDoufwv0gx9zYmbD/f008522003ae51e8b30415a8fb14b2bd/psb_020.png)
    
10. Click the Save icon, then re-run the script.  
      
    Now instead of True or False, we have informative output.  
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/4RSFXi14OSKslPs49OfrkL/fd403fcbec4140ba79c3a0fd6694b59b/psb_021.png)
    
11. Close the PowerShell ISE.  
    
12. On the Desktop, double-click the Visual Studio Code shortcut.  
      
    It may take up to 30 seconds for Visual Studio to load.  
      
    Notice that, like the ISE, there is a scripting console at the top and a terminal window at the bottom. A project called LeaningPowerShell.ps1 was created for you.  
    
13. Type the following script:  
    $Users = Get-LocalUser  
      
    ForEach ($User in $Users){  
    Write-Host "Found User: $User"  
    }
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/1Qjr00rsXG3tiKKom4mm3W/7ca1afa3e49c2572248660ddca9ce200/psb_022.png)
    
    Note: As you type, Visual Studio will pop up a list of commands it thinks you may be looking for, much like Intellisense in ISE.  
    
14. Run the script by clicking on the Run icon (top right) and observe the output in the terminal section of Visual Studio.  
    
15. What if we only want to see a list of enabled user accounts? Alter the first line of code as shown below and re-run the code. Take note of the enabled users.  
    $Users = Get-LocalUser | Where Enabled -EQ True
16. Add the following code to the script and then re-run the script.  
    $Groups = Get-LocalGroup  
      
    ForEach ($Group in $Groups) {  
    $Members = Get-LocalGroupMember $Group  
    ForEach ($Member in $Members){  
    Write-Host "$Member is in $Group"  
    }  
    }
    
    ![Embedded image](https://images.contentful.com/kvf8rpi09wgk/1o6VORyscXPGLHQFXNt9n0/efad89bcbf2e20d3255633dad6900e31/psb_023.png)
    
    Notice that we can find enabled users, groups, and group members using just a few lines of code. We could add another loop to enumerate through computer names and then send the output to a text file for audit purposes. Doing this same audit using a GUI would be very time-consuming and error-prone. This is PowerShell's power and promise for those willing to work with it every day and use it to solve administrative problems.

# Summary

In this exercise, we covered key foundational PowerShell skills, including the most common commands. We learned some important administrative commands and then applied that knowledge to a couple of small but powerful scripts.