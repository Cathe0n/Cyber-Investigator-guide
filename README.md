# Cyber Investigator guide. | Computer Forensics.
This guide aims to assist investigators focused on cybercrime by guiding incident handling, response, and thorough, methodical evidence processing. It is intended as a supplementary resource to support investigators and serves as a reminder rather than a standalone procedure.

<div align="center">
    <img src="https://github.com/user-attachments/assets/ca2cff81-b592-4f4e-b8ff-e6a9d9b54f03" style="width: 40%; max-width: 300; max-height: 300;">
</div>


Cyber Investigator Experimental Detachment

# Incident handling/response.


[![Guide Version](https://img.shields.io/github/tag/Cathe0n/Cyber-Investigator-guide?include_prereleases=&sort=semver&color=purple&label=Guide%20Version)](https://github.com/Cathe0n/Cyber-Investigator-guide/releases/)
[![License](https://img.shields.io/badge/License-Public_Safety_Institution_-purple)](#license)
[![Issues - Cyber-Investigator-guide](https://img.shields.io/github/issues/Cathe0n/Cyber-Investigator-guide?label=Issues)](https://github.com/Cathe0n/Cyber-Investigator-guide/issues)


# Table of contents.

- [Usage](#usage)


# State of the crime scene.

Preserving the crime scene is crucial for any investigator. Any changes made must be documented to minimize the risk of evidence tampering.
If a client reports an incident, advise them to secure the area, remove all personnel from the suspected crime scene, and ensure no one interacts with the environment.
Establishing an incident response plan will be necessary to accurately record and process the situation. (One will be provided soon ^-^ / )

<div align="center">
    <img src="https://github.com/user-attachments/assets/95826c5d-d2f3-4c38-8106-38bc4d27b134" style="width: 70%; max-width: 500; max-height: 300;">
</div>

Upon arriving at the scene, start by interviewing the client with a few key questions to set the foundation for your investigation:

- What do you think has happened?
- What systems are affected?
- How important is this system to production?

These questions will help you determine how to proceed. Keep in mind how critical the system is to the client delays might cost them significant losses. If time is of the essence, they should ideally have a backup system ready for situations like this. If not, you could assist in setting up a backup (even though it’s technically not your job sooooo '-').

Whatever you do, **DO NOT** alter the crime scene without proper documentation. If you must process the scene quickly, prioritize live analysis to address the client’s urgency. However, remember that this approach limits the number of artefacts or evidence you can gather compared to a more thorough imaging process (aka static analysis).

## Live analysis. 
Before diving into the investigation and potentially altering evidence, start by using tools like [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) and [Autopsy](https://www.autopsy.com/) or any other artifact collection applications to analyze recent activity. Another excellent option is [FTK Imager](https://www.exterro.com/ftk-product-downloads/ftk-imager-4-7-3-81) , which can also perform memory analysis on a live system. Depending on the situation, [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) may be sufficient, but for a more thorough investigation, using both [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) and [FTK Imager](https://www.exterro.com/ftk-product-downloads/ftk-imager-4-7-3-81) is recommended. 

You should start with memory analysis when performing live analysis, as RAM contains volatile evidence that cannot be replicated. Use [FTK Imager](https://www.exterro.com/ftk-product-downloads/ftk-imager-4-7-3-81)'s built-in memory acquisition feature to capture the memory or [Magnet RAM Capture Memory Acquisition](https://www.magnetforensics.com/resources/magnet-ram-capture/) , and then analyze it using [Volatility](https://github.com/volatilityfoundation/volatility).
You can use other tools if you prefer, but I personally like using these :3


### Memory acquisition using FTK Imager.
<div align="center">
    <img src="https://github.com/user-attachments/assets/605cb541-6a5f-431a-802b-19a4d01d9354" style="width: 100%; max-width: 1000; max-height: 500;">
</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/e7dfbaeb-7f27-49f5-921f-cb561a4516e1" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

### Using Volatility.

<div align="center">
    <img src="https://github.com/user-attachments/assets/bfd15450-109b-4c30-a9c3-b0f7256ad774" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<br>

### pagefile.sys analysis.

You can acquire pagefile.sys using [FTK Imager](https://www.exterro.com/ftk-product-downloads/ftk-imager-4-7-3-81) or [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) as well and extract the information using [bulk_extractor](https://github.com/simsong/bulk_extractor) OR read it through a Hex editor like 
[ImHex](https://github.com/WerWolv/ImHex) !!! ^o^. You can use [Autopsy](https://www.autopsy.com/) to read it as well but using [bulk_extractor](https://github.com/simsong/bulk_extractor) is better imo :3 as it's more conclusive.
<br>

<br>
<div align="center">
    <img src="https://github.com/user-attachments/assets/30d97539-d8f2-4e44-a4f6-1f96d94faecb" style="width: 100%; max-width: 1000; max-height: 500;">
</div>

<br>
In order to keep things simple put bulk_extractor.exe in the same folder as your pagefile.sys file and open a terminal in the folder. 
<br>

<br>
<div align="center">
    <img src="https://github.com/user-attachments/assets/d5ba5026-5b90-4406-bba5-58eab4e15a0c" style="width: 100%; max-width: 1000; max-height: 500;"> 
</div>

<br>

Run  ```./bulk_extractor64.exe -o output .\pagefile.sys```


<br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/b7baa2e0-17be-4225-9124-c1ba965b0e23" style="width: 100%; max-width: 1000; max-height: 500;">
    
</div>

<br>

Once it's finished you can analyse the output using your favourite text editor...I'm using Notepad but I know you'll use something cooler '-'

<br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/88fae686-de6a-4c0b-a2cf-08a2dac66671" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/8353a26d-6d34-466f-b650-001d1a2c8b41" style="width: 100%; max-width: 1000; max-height: 500;">
    
</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/4e67af3a-c496-4964-97e2-9dbe6b6e9a4b" style="width: 100%; max-width: 1000; max-height: 500;">
    
</div>

<br>

You'll need to analyse this closely and have a goal in mind. What is it you're looking for ? 

An application (.exe) ?
A background process/service ?
A specific thumbnail/image ?

Alternatively, you can use [Belkansoft](https://belkasoft.com/get) though I personally don’t have much experience with it. With [Belkansoft](https://belkasoft.com/get) you can easily analyze pagefile.sys and view its contents, including images and thumbnails from websites. Plus, it has a GUI, sooo... that’s poggers. BUT! the outputs from [bulk_extractor](https://github.com/simsong/bulk_extractor) are already sufficient. 

> [!IMPORTANT]
> Use whatever tools you feel comfortable with, do some scenarios with them! >.>

<br>

## gKAPE.

[gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) is a powerful tool to have in your arsenal. Think of it as a collection of tools within a tool so uhh that's convinient! :3 
This tool collects Windows event logs, registry hives, and much more. It’s also compatible with additional modules like [Magnet RAM Capture Memory Acquisition](https://www.magnetforensics.com/resources/magnet-ram-capture/) a memory acquisition tool for live analysis. These are integrated into [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape), making it even more versatile. Tools like [Hayabusa](https://github.com/Yamato-Security/hayabusa) and others are also integrated, adding even more power to this incredible toolkit!! So, this is a must have in your USB!! ^o^

<div align="center">
    <img src="https://github.com/user-attachments/assets/5a3a4b4c-1ff2-4da8-a8b7-7dac64054d4d" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

### Recommended way of using gKAPE.

One way of using [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) is selecting _BasicCollection_ and _SANS_Triage_. By choosing these options, you can grab Event logs and Windows registry hives, which are crucial for identifying what happened during the incident. These selections will also help you collect artifacts that can give insight into the system’s behavior, user activity, and potential malicious actions. Both of these modules are great for quickly gathering key data that will be essential in your investigation sooo it's poggers for live analysis. From there, you can analyze the collected data for clues to track down the malicious activity frfr.
<br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/51054dcc-0e1c-4da1-b137-e1a7bb1d951a" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/d8b79736-8bd4-4ebb-9d73-a79ab7af240f" style="width: 100%; max-width: 1000; max-height: 500;">
</div>
<br>

Here's some example of the results from [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape).
<br>


<div align="center">
    <img src="https://github.com/user-attachments/assets/c42ceedb-0977-4b01-8ff9-4524af8d4152" style="width: 100%; max-width: 1000; max-height: 500;">
</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/da77662e-76eb-4e95-8bea-90b41688afb7" style="width: 100%; max-width: 1000; max-height: 500;">
</div>

<br>

### History of launched applications from the system | PcaAppLaunchDic.txt.

<div align="center">
    <img src="https://github.com/user-attachments/assets/df83a0c3-b6fb-4ee6-819a-93f3b06974cd" style="width: 100%; max-width: 1000; max-height: 500;">

</div>
<br>

### Background application processes log | PcaGeneralDb0.txt.

<div align="center">
    <img src="https://github.com/user-attachments/assets/423339b7-a5ae-480a-a0f5-291da1082ee2" style="width: 100%; max-width: 1000; max-height: 500;">
</div>
<br>

### Windows Defender log | MPLog-69420.log (I know it's Microsoft Defender '-').
<div align="center">
    <img src="https://github.com/user-attachments/assets/6cd65a24-f8f7-44ff-9e2b-397e32a09e7a" style="width: 100%; max-width: 1000; max-height: 500;">
</div>

<br>

## Event log analysis (sorta >->)

Event log or ```winevt``` is absolutely the most useful system for you. Windows keeps logs of what happens to a system in the event manager so if the computer did something then event manager knows about it. So analysing this in details can give insights of what happened or what's happening! You should check these three logs ```Microsoft-Windows-Windows Defender%4Operational.evtx```, ```Security.evtx``` and ```System.evtx```. Now, usually you should have a laptop on site...right ? If you do, you can use [EventLogExpert](https://github.com/microsoft/EventLogExpert) by analysing the log files on your own machine using [EventLogExpert](https://github.com/microsoft/EventLogExpert) BUT! you can use the normal Event Viewer built into Windows, just keep in mind you are _using_ evidence so uhhh '-'

### Microsoft-Windows-Windows Defender%4Operational.evtx

The event log provides information about the **Windows Defender processes log**, offering an in-depth view of what Windows Defender is doing and the processes it’s handling. Essentially, it’s a more detailed look of ```MPLog```. This can come in handy if you're looking for anything suspicious like the disabling of Windows defender or any changes made by the user towards Windows Defender. It is suggested that you use ```MPLog``` as well to correlate the event :3

<div align="center">
    <img src="https://github.com/user-attachments/assets/d5ce59e2-d3c5-44f7-bc88-f2110364f95c" style="width: 100%; max-width: 1000; max-height: 500;">
</div>

### Security.evtx

This is a crucial event log to analyze... Well, I mean, all logs are important, but this one is especially handy >->.

This log provides details about administrative powers that have been granted and to whom. Think of it like those **UAC** (User Account Control) prompts asking Yes or No for elevated privileges. Using this log, you can track which applications requested admin rights and what they were trying to access.

This is why **RBAC** (Role-Based Access Control) is so important! :> in short, this event logs keeps track of security events.

<div align="center">
    <img src="https://github.com/user-attachments/assets/44c1339d-d1d5-435d-a6f0-9231a9ed08c4" style="width: 100%; max-width: 1000; max-height: 500;">
</div>

### System.evtx

System.evtx is a crucial log file that stores system event records on Windows operating systems. It’s part of the Event Viewer system, which helps you troubleshoot system operations so if anything goes wrong the error log should be stored here.

This event log provides valuable information about system processes and services, including any error codes that may help identify issues.

- Hardware Events: Logs issues or changes involving hardware, such as driver updates, device disconnections, or hardware failures.
- System Services: Tracks the startup, shutdown, and behavior of essential Windows services.
- System Errors: Records critical issues affecting the operating system's stability or functionality, such as blue screens or kernel errors.
- Startup and Shutdown: Includes details about boot processes and shutdown operations.

<div align="center">
    <img src="https://github.com/user-attachments/assets/966e3fdd-0e97-474c-b54a-6503bf0d621c" style="width: 100%; max-width: 1000; max-height: 500;">
</div>

Time to time, it’s useful to track the uptime of a system or determine when it was turned on or off. This can help narrow your investigation to a specific time window. By searching for a specific application that always starts on boot, you can identify when the machine was powered on. 
One such application is EventLog what a surprise, right? EventLog, along with many other crucial system applications, starts early in the boot process, making it a useful tool for this purpose. Orrr...Another key application to track is Explorer, as it often runs in the background and can help pinpoint system activity during startup or shutdown.
<br>

| Use case             | Order | Logfile | Source        | Level  | Event ID | Event Description                                                                 | Description                                                       |
|----------------------|-------|---------|---------------|--------|----------|----------------------------------------------------------------------------------|-------------------------------------------------------------------|
| Planned reboot       | 1     | System  | User32        | Info   | 1074     | The process Explorer.EXE has initiated the restart of computer                   | The process Explorer.EXE has initiated the restart of computer on behalf of user Administrator. |
| Planned reboot       | 2     | System  | Event Log     | Info   | 6006     | The Event log service was stopped.                                                |                                                                   |
| Planned reboot       | 3     | System  | Kernel Power  | Info   | 109      | The kernel power manager has initiated a shutdown transition.                    |                                                                   |
| Planned reboot       | 4     | System  | Kernel Boot   | Info   | 13       | The operating system is shutting down at system time 2024-11-25T08:11:45.765230100Z. |                                                                   |
| Planned reboot       | 5     | System  | Kernel General| Info   | 20       | The last shutdown's success status was true.                                      |                                                                   |
| Planned reboot       | 6     | System  | Event Log     | Info   | 12       | The operating system started at system time 2024-11-25T08:12:32.486934500Z.      |                                                                   |
| Planned reboot       | 7     | System  | Event Log     | Info   | 6005     | The Event log service was started.                                                |                                                                   |
| Planned reboot       | 8     | System  | Event Log     | Info   | 6013     | The system uptime is 10 seconds.                                                  |                                                                   |
| Planned shutdown     | 1     | System  | User32        | Info   | 1074     | The process Explorer.EXE has initiated the shutdown of computer                  | The process Explorer.EXE has initiated the shutdown of computer on behalf of user Administrator. |
| Planned shutdown     | 2     | System  | Event Log     | Info   | 6006     | The Event log service was stopped.                                                |                                                                   |
| Planned shutdown     | 3     | System  | Kernel Power  | Info   | 109      | The kernel power manager has initiated a shutdown transition.                    |                                                                   |
| Planned shutdown     | 4     | System  | Kernel Boot   | Info   | 13       | The operating system is shutting down at system time 2024-11-25T08:11:45.765230100Z. |                                                                   |
| Planned shutdown     | 5     | System  | Kernel General| Info   | 20       | The last shutdown's success status was true.                                      |                                                                   |
| Planned shutdown     | 6     | System  | Event Log     | Info   | 12       | The operating system started at system time 2024-11-25T08:12:32.486934500Z.      |                                                                   |
| Planned shutdown     | 7     | System  | Event Log     | Info   | 6005     | The Event log service was started.                                                |                                                                   |
| Planned shutdown     | 8     | System  | Event Log     | Info   | 6013     | The system uptime is 10 seconds.                                                  |                                                                   |
| Unexpected shutdown  | 1     | System  | Kernel General| Info   | 12       | The operating system started at system time 2024-11-25T08:12:32.486934500Z.      |                                                                   |
| Unexpected shutdown  | 2     | System  | Kernel General| Info   | 20       | The last shutdown's success status was false.                                     |                                                                   |
| Unexpected shutdown  | 3     | System  | Kernel General| Critical | 20   | The system has rebooted without cleanly shutting down first.                       | This error could be caused if the system shuts down unexpectedly. |
| Unexpected shutdown  | 4     | System  | Event Log     | Error  | 6008     | The previous system shutdown at 02:11:03 PM on 2024-11-25 was unexpected.          |                                                                   |
| Unexpected shutdown  | 5     | System  | Event Log     | Info   | 6005     | The Event log service was started.                                                |                                                                   |
| Unexpected shutdown  | 6     | System  | Event Log     | Info   | 6013     | The system uptime is 10 seconds.                                                  |                                                                   |
| Unexpected shutdown  | 7     | System  | User32        | Warning | 1076    | The reason supplied by user Administrator for the last unexpected shutdown of this computer is: check process name. |                     |
| LSASS process crash  | 1     | System  | User32        | Info   | 1074     | The process wininit.exe has initiated the restart of computer                     | The process wininit.exe has initiated the restart of computer on behalf of user TRFSF01. |
| LSASS process crash  | 2     | System  | Kernel General| Info   | 13       | The operating system started at system time 2024-11-25T08:12:32.486934500Z.      |                                                                   |
| LSASS process crash  | 3     | System  | Kernel General| Info   | 20       | The last shutdown's success status was true.                                      |                                                                   |
| LSASS process crash  | 4     | System  | Event Log     | Error  | 6008     | The previous system shutdown at 01:21:34 PM on 2024-11-25 was unexpected.          |                                                                   |
| LSASS process crash  | 5     | System  | Event Log     | Info   | 6005     | The Event log service was started.                                                |                                                                   |
| LSASS process crash  | 6     | System  | Event Log     | Info   | 6013     | The system uptime is 10 seconds.                                                  |                                                                   |
| LSASS process crash  | 7     | System  | User32        | Warning | 1076    | The reason supplied by user Administrator for the last unexpected shutdown of this computer is: check process name. |                     |

<br>
Use the table above to find the information you need for your investigation! You can search for more but these are the ones I find useful ^-^

This is mostly computer forensics, we're going to go web forensics now!

## Browser analysis (Live).



# Static analysis.
If you're dealing with a live system when you arrived then **Static analysis** should be a second priority. Static analysis takes a lot of time and depending on the situation, a thorough live analysis of the affected machine should suffice. Anyways, first you need to remove every storage drives in the system since you don't want to deal with RAID systems and missing a HDD and all that so better pay attention >->. You can use your own machine to conduct the imaging process, you can use [TestDisk](https://www.cgsecurity.org/wiki/TestDisk_Download) or [DMDE](https://dmde.com/).  Choose your preferred format, such as .dd or any other that fits your situation.

> [!IMPORTANT]
> Depending on your hardware data imaging will take AGES!!! '-'

To do a full imaging of a system can take a long time and if it’s a server you can take a vacation and come back and it’s not finished imaging. It is also expensive, imaging a 1 TB drive requires another 1 TB drive to store the image and this is called **Physical imaging**. That said, you have options. Physical imaging captures everything but takes the longest. **Logical imaging** is faster but less thorough. Carefully consider the situation to decide the best approach for your investigation. There's also **RAW imaging** but this for cases where you need more details or for **Corrupted data recovery**.

> [!IMPORTANT]
> Use **WRITE BLOCKER** I don't care how experienced you are, a **WRITE BLOCKER IS ESSENTIAL** '~'

# Incident handling/Response: Phishing.

Let’s talk about Phishing incidents. One common issue is the defacement of a client’s website. If the client has set up their web server properly, they should have a Security Information and Event Management (SIEM) system or an Intrusion Detection System (IDS) in place to prevent malicious activity. If that’s the case, it’s mostly about finding the logs, reviewing them, and implementing a fix to prevent the incident from happening again. But it’s not that simple. 

<div align="center">
    <img src="https://github.com/user-attachments/assets/abc58982-595b-404b-8706-4aee1fb2b1bb" style="width: 70%; max-width: 300; max-height: 300;">
</div>

Clients will want a thorough investigation and report done before moving into the eradication process. This is where the analysis part of the job comes in. Assuming the client has an SIEM/IDS system in place, your first task is to trace which machine or computer carried out the malicious activity. Any remote attack **MUST** originate from an infected machine, so identifying that machine is crucial. If it’s a network of machines involved, you’ll need to **ISOLATE** them by separating them from the main network. (Talk with the company’s engineer…They don’t have one ? Welp it’s now your job :P).

Once the machines are isolated, begin the identification process. If it's a network of infected machines, it’ll take more than just you to get it done quickly. You’ll need a team to move efficiently.

Start by commanding one of your team members to interview the employees. They may have seen something unusual or noticed any signs of the attack before it escalated. Meanwhile, you or another member should work on isolating the machines from the network and securing any potential entry points.

While the interviews are happening, keep an eye on the overall network. Once the network is contained, it’s time to dive into the forensics. Use your tools to analyze the compromised systems, check logs, and gather evidence that can point to how the attack occurred, what vulnerabilities were exploited, and what impact it had on the system.

It’s also essential to document every action taken during this phase this will be crucial for building a report and providing evidence for any legal actions down the line.

> [!NOTE]
> This is assuming it’s a medium-large company if it’s small then taking it off the grid is needed MAYBE idk what you’re working with ‘ ^ ’
> Act **SWIFTLY!!!** 'o'

- What have you done in the past 24hr ?
- Did you notice anything weird when using your computer ? A random CMD popped out of nowhere ? (Say a black box for the elderly >->)
- Downloaded anything recently ?
- Clicked on anything ? 
- Plugged a USB into this machine before ?

With these questions hopefully you can pinpoint WHEN the infection started and WHERE it originated. 
> [!TIP]
> Be **FLEXIBLE!!** Use these questions as a reference but ask what you need to know to assist you with the investigation!!

## Email Phishing campaign scenario. 

According to Cloudflare, 90% of cyber attacks come from email phishing campaigns so you shouldn’t be surprised! :3.  First, analyze the suspicious email using tools like EmailDossier or any other good options like EML Analyzer (which is awesome too). There are multiple ways to check if the email address looks fishy (see what I did there? :3… No, I won’t stop). Just read through the results from EML Analyzer, and if anything seems off, you’ll likely have your culprit. Unless, of course, there are multiple phishing emails... So, uh, good luck!! ^-^

A phishing email must have a payload, and you can check to see whether the attached file is suspicious. But remember, these malicious actors are smart and sneaky, so they’ll do their best to hide it >.<. Use these tools to help you analyze the payload and uncover what’s really lurking inside.

- [EML Analyzer](https://analyzer.sublime.security/)
- [Email Dossier](https://centralops.net/co/EmailDossier.aspx)
- [Mx Toolbox](https://lookup.mxtoolbox.com/dmarc/dmarc-email-tools)
### Email analysis.

Alright!! So, you’ll need to navigate through Gmail (or whatever email provider the company uses) and find a way to display the .eml file. In Gmail it is as shown in the picture. Once you click **Show original**

<br><br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/a84879ae-e7ff-4e74-af34-c9f5398f514f"  style="width: 70%; max-width: 500; max-height: 700;">
</div>

<br><br>

It should open a new tab named **Original Message**. Next you need to download the .eml file.

<br><br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/6d3beac8-2e5d-471a-a169-39df8c9eebbf"  style="width: 70%; max-width: 400; max-height: 200;">
</div>

<br><br>

Once you’ve acquired the .eml file use the EML analyzer to well uh analyse it ??? 

<br><br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/bb795a60-dad4-4921-8255-69f5ee967876" style="width: 70%; max-width: 1000; max-height: 500;">
</div>

<br><br>

Here you can see what EML Analyzer has provided. [EML Analyzer](https://analyzer.sublime.security/) has [VirusTotal](https://www.virustotal.com/) API integrated into it so you can see if the attachments are malicious or not.

<br><br>
<div align="center">
    <img src="https://github.com/user-attachments/assets/8ef90e1e-473d-4612-9632-1dea8831f4dc" style="width: 70%; max-width: 800; max-height: 450;">
</div>

<br><br>

[Email Dossier](https://centralops.net/co/EmailDossier.aspx) helps checks

- Owner’s contact information
- Registrar and registry information
- The company that is hosting a Web site
- Where an IP address is geographically located
- What type of server is at the address
- The upstream networks of a site
  
<br><br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/a181eea5-8979-4436-9f00-33302f2b3fc5"  style="width: 70%; max-width: 500; max-height: 800;">
</div>

<br><br>
Now, this is technically a post incident. You need to analyse what that malware does. There are multiple ways to do this of course… So let’s get into it!! ^o^

# Malware analysis! (This is big brain time d(>_< ) ).

I’m going to be honest,  this is where things are complicated and time consuming. Malware analysis is a WHOLE nother topic and I will make another guide for it soon bare with me!! >-<. 

First, identify **HOW** the malware breached the systems.

- Phishing Email ?
- Bad USB/Physical infection ?
- Pirated software ?

Secondly, identify the aftermath of the attack.

- What did the malware do to the system ?
- Is it a backdoor ?
- A ransomware ?
  
Try to identify the goal of this malicious actor. This can give you some sort of an idea of how to continue the investigation.
<br><br>

### Malware Static analysis.

**Windows systems**
This part is going to be a bit tricky. If the system is known to be infected and YOU have already isolated it from the network, you can perform a full system imaging and analyze the malware safely using the copied image. This is called static analysis, and it’s the safest way to analyze a system. If you’re going this route, you can use tools like  [IDA](https://hex-rays.com/ida-pro), [PE-Explorer](https://www.pe-explorer.com/) and [OllyDbg](https://www.ollydbg.de/download.htm).Yeah, this is reverse engineering area WHICH will not be fully covered in this guide. (I don't think you're going to analyse this deep in most cases! ^-^). 

**Linux systems.**
For Linux systems you can use [REMnux](https://docs.remnux.org/) this has everything you need to analyse malware in Linux systems.

<br><br>
### Malware Dynamic Analysis.
Another way is to dynamically analyze the malware. Every malware has a goal, and achieving that goal requires processing power from the infected machine. You can use [Procmon](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon) from Microsoft itself, to identify suspicious services and processes running on the system (make sure you learn how to use this properly '-'). There **was** also an application called **Winpatrol**, but unfortunately, it has been sent to heaven (RIP Scotty, you were the best puppy Y-Y). [Procmon](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon)  depending on the situation, can give you insights into what the malware’s goals are and provide enough data to include in your report. However, static analysis and reverse engineering can help you understand the malware in even greater detail.








