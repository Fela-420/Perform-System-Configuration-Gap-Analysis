# Perform-System-Configuration-Gap-Analysis
Assisted Lab: Perform System Configuration Gap Analysis
Scenario
As a security team member of Structureality Inc, you are working to improve your organization's security stance. Often the best path to a secure IT infrastructure starts with thorough planning and analysis. You will perform a gap analysis of the current configuration of a system against a security template.

In this lab, you will use security templates to manage a Windows Server configuration, which will entail using the Microsoft Policy Analyzer to perform a security baseline template review and gap analysis.

Understand your environment

1.2 Summarize fundamental security concepts.
3.2 Given a scenario, apply security principles to secure enterprise infrastructure
4.1 Given a scenario, apply common security techniques to computing resources.
4.4 Explain security alerting and monitoring concepts and tools.
5.1 Summarize elements of effective security governance.
Perform gap analysis
Gap analysis is the act of comparing the current configuration of a system with a template, configuration file, baseline, security framework, or settings documentation. This is an essential operation to discover the differences between the intended or expected configuration of a system and its actual operating configuration. In this exercise, you will perform a gap anal

Determine the build number for the Windows Server 2019 running in thePC10 virtual machine using winver. Select Type here to search from the taskbar, type winver, then select winver from the results.
![Screenshot_2025-04-13_04_23_56](https://github.com/user-attachments/assets/0894b570-e48b-47ba-bf41-304b37ab0bac)

The About Windows window should be displayed. Look at the second line, which reads "Version 1809 (OS Build 17763.4377)".

The Windows Server 2019 version number 1809 and the OS Build number 17763 are fixed for this challenge. If you perform these operations against other systems, you will need to match the version and build numbers to the baseline template files.

Select OK to close the About Windows window.

Select Type here to search from the taskbar, type powershell, right-click Windows PowerShell from the results, then select Run as administrator.
![Screenshot_2025-04-13_04_24_58](https://github.com/user-attachments/assets/5f2f825f-01d2-42f2-a315-e5b1306c9a20)

Do not use Windows PowerShell ISE nor Windows PowerShell (X86).

Select Yes on the User Account Control window.

Enter copy D:\* c:\LABFILES

This command copies PolicyAnalyzer.zip and Windows 10 Version 1809 and Windows Server 2019 Security Baseline.zip from the read-only removable media virtual optical disc (i.e., D:) to C:\LABFILES.

If the command is successful, there will be no confirmation.

These two files are from the Microsoft Security Compliance Toolkit. The baseline file was selected based on the OS version and build number.

The Microsoft Security Compliance Toolkit includes the Policy Analyzer tool as well as numerous security configuration template files. Searching for "Microsoft Security Compliance Toolkit" will help you locate the download area on the Microsoft website where these items are hosted. They have been provided for you the Student-Resources-L01.ISO media.

Enter cd c:\LABFILES to change into the directory.
![Screenshot_2025-04-13_04_25_22](https://github.com/user-attachments/assets/228f5fe5-68b6-4184-8344-abca41b1c4a6)

Enter ls to view the contents of the directory.

You should see PolicyAnalyzer.zip and Windows 10 Version 1809 and Windows Server 2019 Security Baseline.zip in the list of files.

"ls" is a Linux command (one of many) that are supported by Windows PowerShell. The "dir" will also display the directory contents.
![Screenshot_2025-04-13_04_25_39](https://github.com/user-attachments/assets/ef7f53a7-0438-4007-b27c-9a6b315f6b87)

Enter the following commands to extract the contents of the zip files into their own sub-directories:

Expand-Archive -Path PolicyAnalyzer.zip
Expand-Archive -Path "Windows 10 Version 1809 and Windows Server 2019 Security Baseline.zip"
Enter the following command to open the Policy Analyzer application:

C:\LABFILES\PolicyAnalyzer\PolicyAnalyzer_40\PolicyAnalyzer.exe
The Policy Analyzer window should now be displayed. If needed, minimize the PowerShell window.
![Screenshot_2025-04-13_04_26_31](https://github.com/user-attachments/assets/17b0f73a-34af-4cbf-b6ae-ac36f1884cb8)

The Policy Analyzer window may appear behind the PowerShell window.

Maximize the Policy Analyzer window.
![Screenshot_2025-04-13_04_30_12](https://github.com/user-attachments/assets/7ab0ec2b-4c0f-4c53-a80e-0605deb46521)

The operation buttons on the right side of the interface may not display fully when the window is not maximized.

At the bottom of the Policy Analyzer window, select the Policy Rule sets in field.

If you do not see Policy Rules sets in and Policy Definitions in, adjust your screen to a higher resolution and relaunch the Policy Analyzer.

On the Pick the folder containing the Policy Analyzer Policy Rules files window, in left pane select Local Disk (C:), in the right pane double-click LABFILES, double-click Windows 10 Version 1809 and Windows Server 2019 Security Baseline, double-click Documentation, then select Select Folder.

The Policy Analyzer window should now show several policy rule sets.

Perform a View/Compare of MSFT-Win10-v1809-RS5-WS2019-FINAL using Policy Analyzer by marking the MSFT-Win10-v1809-RS5-WS2019-FINAL checkbox, then selecting View / Compare.
![Screenshot_2025-04-13_04_30_12](https://github.com/user-attachments/assets/3a87be78-45ea-485f-bc09-859cfccb23bd)

The Policy Viewer window will be displayed, showing the various policy settings contained in the MSFT-Win10-v1809-RS5-WS2019-FINAL policy rule set.

This feature, View/Compare, shows the settings currently in the baseline security template file.

Scroll down the list and look at a few policy setting lines.
![Screenshot_2025-04-13_04_34_01](https://github.com/user-attachments/assets/08df8a97-43fb-44e8-a0bd-cef5895ac85d)

Scroll to the bottom of the list and locate the LockoutBadCount, which is 9th from the bottom

Also near the bottom, locate MinimumPasswordLength, which is 4th from the bottom.

What is the baseline value from the security template for the policy setting item of MinimumPasswordLength?

Close the Policy Viewer window.

Perform a Compare to Effective State of MSFT-Win10-v1809-RS5-WS2019-FINAL using Policy Analyzer by marking the MSFT-Win10-v1809-RS5-WS2019-FINAL checkbox, then selecting Compare to Effective State.
![Screenshot_2025-04-13_04_35_28](https://github.com/user-attachments/assets/edbec7b6-158e-4c76-b6ca-edde8e2ebe96)

This feature, Compare to Effective State, performs a gap analysis between the baseline security template file and the current in-use values of the local operating system.

If a User Account Control window appears, select Yes.

The Policy Viewer window will be displayed, showing a comparison between the various policy settings contained in the MSFT-Win10-v1809-RS5-WS2019-FINAL policy rule set and the current operating system (labeled as "Effective state").
![Screenshot_2025-04-13_04_37_33](https://github.com/user-attachments/assets/98cc95d0-e0d8-4c55-8d52-92bcd99a72ab)

Notice that many items are highlighted in yellow. These are where there are differences between the baseline file and the current effective state of the live operating system environment of PC10.

Scroll down to the bottom of the list.

Notice the Effective state value of LockoutBadCount is 0, and MinimumPasswordLength is 7.

Is the PC10 system in compliance with the security template based on the gap analysis results?

No
Yes
Congratulations, you have answered the question correctly.

Close the Policy Viewer window.

