# Cyber Investigator guide
This guide aims to assist investigators focused on cybercrime by providing guidance on incident handling, response, and thorough, methodical evidence processing. It is intended as a supplementary resource to support investigators and serve as a reminder, rather than as a standalone procedure.

<div align="center">
    <img src="https://github.com/user-attachments/assets/fdb46b41-594a-4f8e-b736-184b7df58ce4" width="300" height="300">
</div>
Cyber Investigator Experimental Detachment

# Incident handling/response

[![GitHub tag](https://img.shields.io/github/tag/Cathe0n/Cyber-Investigator-guide?include_prereleases=&sort=semver&color=purple)](https://github.com/Cathe0n/Cyber-Investigator-guide/releases/)
[![License](https://img.shields.io/badge/License-Public_Safety_Institution_-purple)](#license)
[![issues - Cyber-Investigator-guide](https://img.shields.io/github/issues/Cathe0n/Cyber-Investigator-guide)](https://github.com/Cathe0n/Cyber-Investigator-guide/issues)


# Table of contents

- [Usage](#usage)


# State of the crime scene.

When processing evidence as an investigator, preserving the crime scene is crucial. Each changes made by a person or you must be documented in order to minimise the risk of evidence tampering. If a client contacts you to report an incident, advise them to secure the area, remove all personnel from the suspected crime scene, and ensure no one interacts with the environment. Establishing an incident response plan will be necessary to accurately record and process the situation.  (One will be provided soon ^-^ / )

<div align="center">
    <img src="https://github.com/user-attachments/assets/95826c5d-d2f3-4c38-8106-38bc4d27b134" width="500" height="300">
</div>

Upon arriving at the scene, begin by interviewing the client with a few key questions to frame your investigation.

- What do you think has happened ? 
- What systems are affected ?
- How important is this system to production ?

This can give you an idea/foundation on how to proceed with investigating the incident. Take note of how important the system is to the client, you cannot delay them too much as they are actively losing money. If there’s a time crunch the client should have a backup in place just for such an incident but if that’s not the case try to assist in setting up a backup system (technically not your job though sooo). DO NOT affect the crime scene without documentation. You either process the crime scene live and as fast as possible since it’s crucial to the client. This of course limits how many artefacts/crumbs can be gathered compared to the imaging process or also known as static analysis. 

### Live analysis. 
Before you get into messing everything up let's use [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) and [Autopsy](https://www.autopsy.com/) or any artifacts collecting appilcations to analyse what has happened recently. [FTK Imager](https://www.exterro.com/ftk-product-downloads/ftk-imager-4-7-3-81) Is also another great tool and can perfom a memory analysis on a live system. Depending on the situation, [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) can suffice but using both [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) and [FTK Imager](https://www.exterro.com/ftk-product-downloads/ftk-imager-4-7-3-81) is recommended. 

Once you have everything extracted and documented, you then can get into dynamic analysis of the malware/exploit or whatever. 

### Static analysis.
If you're dealing with a live system when you arrived then **Static analysis** should be a second. Static analysis takes a lot of time and depending on the situation, a thorough live analysis of the affected machine should suffice. Anyways, first you need to remove every storage drives in the system since you don't want to deal with RAID systems and all that so better pay attention >->. You can use your own machine to conduct the imaging process, you can use [TestDisk](https://www.cgsecurity.org/wiki/TestDisk_Download) or [DMDE](https://dmde.com/). Depending on your preference you can generate an image in .dd or any other formats you prefer. 
> [!IMPORTANT]
> Depending on your hardware data imaging will take AGES!!! '-'

To do a full imaging of a system can take a long time and if it’s a server you can take a vacation and come back and it’s not finished imaging. It is also expensive, for example if a computer has a 1 TB storage device you also need a 1 TB storage device to do a full **physical imaging**. But you can also do a **Logical imaging** but it is **NOT** thorough so determine and choose wisely on how you will conduct your investigation. 


# Website incident handling (Phishing).

Let’s discuss Websites related incidents, one of the common incidents encountered is defacement of the client’s website. If the clients have set up their webserver properly they must have an SIEM system/IDS in place to deter anything malicious from happening and if that’s the case it’s just about finding the logs and reviewing them and implementing a fix so the incident doesn’t happen again. But it’s not that simple. 

<div align="center">
    <img src="https://github.com/user-attachments/assets/abc58982-595b-404b-8706-4aee1fb2b1bb" width="800" height="500">
</div>

Clients will want a thorough report and investigation done before moving into the eradication process. So this is where we go into the analysis part of the job. Assuming the client has an SIEM/IDS system implemented you must trace what machine or computer committed the malicious activity. Any remote attack MUST originate from an infected system so finding that machine is crucial if it’s a network of machines then ISOLATE them by separating them from the main network (Talk with the company’s engineer…They don’t have one ? Welp it’s now your job :P).

Once isolated, perform the identification. If it’s a network of machines it’ll take more than you alone in order to make it quick. In a team, you must command one of your members to interview the employees. While you or another member starts working to isolate the machines from the network. 
> [!NOTE]
> This is assuming it’s a medium-large company if it’s small then taking it off the grid is needed MAYBE idk what you’re working with ‘ ^ ’

- What have you done in the past 24hr ?
- Did you notice anything weird when using your computer ? A random CMD popped out of nowhere ? (Say a black box for the elderly >->)
- Downloaded anything recently ?
- Clicked on anything ? 
- Plugged a USB into this machine before ?

With these questions hopefully you can pinpoint WHEN the infection started and WHERE it originated. 
> [!TIP]
> Be FLEIXBLE!! Use these questions as a reference but ask what you need to know!!

## Email Phishing campaign scenario. 

According to Cloudfare 90% of cyber attacks came from Email Phishing campaigns. So, you shouldn’t be surprised :3.  First analyse the suspect email using EmailDossier or any other tools like EML analyzer which is awesome too. There are multiple way to check if the Email address smells fishy (see what I did there :3…No, I won’t stop), just read the results from EML analyzer. and if it looks fishy then you know this is where the infection came from…Unless there’s multiple phishing email…So uhh good luck!! ^-^. A phishing Email must have a payload and you can check to see whether the file is fishy or not. But these malicious actors are smart and sneaky so they’ll try their best to hide it >.<. Use these tools to help you analyse the payload.

- [EML Analyzer](https://analyzer.sublime.security/)
- [Email Dossier](https://centralops.net/co/EmailDossier.aspx)
- [Mx Toolbox](https://lookup.mxtoolbox.com/dmarc/dmarc-email-tools)
### Email analysis.

Alright!!, so you need to navigate through Gmail or whatever this company uses as their main Email provider and find a way to show it’s .eml file. In Gmail it is as shown in the picture. Once you click **Show original**

<br><br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/a84879ae-e7ff-4e74-af34-c9f5398f514f" width="500" height="700">
</div>

<br><br>

It should open a new tab named **Original Message**. Next we need to download the .eml file.

<br><br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/6d3beac8-2e5d-471a-a169-39df8c9eebbf" width="400" height="200">
</div>

<br><br>

Once you’ve acquired the .eml file use the EML analyzer to well uh analyse it ??? 

<br><br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/bb795a60-dad4-4921-8255-69f5ee967876" width="1000" height="500">
</div>

<br><br>

Here you can see what EML Analyzer has provided. [EML Analyzer](https://analyzer.sublime.security/) has [VirusTotal](https://www.virustotal.com/) API integrated into it so you can see if the attachments are malicious or not.

<br><br>
<div align="center">
    <img src="https://github.com/user-attachments/assets/8ef90e1e-473d-4612-9632-1dea8831f4dc" width="800" height="450">
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
    <img src="https://github.com/user-attachments/assets/a181eea5-8979-4436-9f00-33302f2b3fc5" width="500" height="800">
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
- A ransom ?
  
Try to identify the goal of this malicious actor. This can give you some sort of an idea of how to continue the investigation.
<br><br>

### Malware Static analysis.

**Windows systems**
This is going to be a bit difficult. If the system is known to have already been infected and YOU have isolated it from the network you can do a full system imaging and analyse the malware safely with the copied image. This is known as static analysis and it’s the safest way you can analyse a system. If that’s the case you can use tools such as [IDA](https://hex-rays.com/ida-pro), [PE-Explorer](https://www.pe-explorer.com/) and [OllyDbg](https://www.ollydbg.de/download.htm)...Yeah, this is reverse engineering area WHICH will not be fully covered in this guide. (btw this for Windows ^-^). 

**Linux systems.**
For Linux systems you can use [REMnux](https://docs.remnux.org/) this has everything you need to analyse malware in Linux systems.

<br><br>
### Malware Dynamic Analysis.
Another way is to dynamically analyse the malware. Each malware always ahve a goal and that goal requires processing power from the computer. You can use [Procmon](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon) from Microsoft itself to find suspicious services and processes running (Learn how to use this properly '-'). Another application called Winpatrol **did** exist but it has been sent to heaven (RIP Scotty, you were the best puppy Y-Y). [Procmon](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon) depending on the scenarios can help you understand what's the malware's goals are and can provide enough information to compile into a report. But a static analysis and reverse engineering can help you further understand better.








