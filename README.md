# Cyber Investigator guide
This guide aims to assist investigators focused on cybercrime by guiding incident handling, response, and thorough, methodical evidence processing. It is intended as a supplementary resource to support investigators and serves as a reminder rather than a standalone procedure.

<div align="center">
    <img src="https://github.com/user-attachments/assets/59ce240c-1679-459f-b8e4-3615f58dfd4e" width="300" height="300">

</div>
Cyber Investigator Experimental Detachment

# Incident handling/response

[![GitHub tag](https://img.shields.io/github/tag/Cathe0n/Cyber-Investigator-guide?include_prereleases=&sort=semver&color=purple)](https://github.com/Cathe0n/Cyber-Investigator-guide/releases/)
[![License](https://img.shields.io/badge/License-Public_Safety_Institution_-purple)](#license)
[![issues - Cyber-Investigator-guide](https://img.shields.io/github/issues/Cathe0n/Cyber-Investigator-guide)](https://github.com/Cathe0n/Cyber-Investigator-guide/issues)


# Table of contents

- [Usage](#usage)


# State of the crime scene.

Preserving the crime scene is crucial for any investigator. Any changes made must be documented to minimize the risk of evidence tampering.
If a client reports an incident, advise them to secure the area, remove all personnel from the suspected crime scene, and ensure no one interacts with the environment.
Establishing an incident response plan will be necessary to accurately record and process the situation. (One will be provided soon ^-^ / )

<div align="center">
    <img src="https://github.com/user-attachments/assets/95826c5d-d2f3-4c38-8106-38bc4d27b134" width="500" height="300">
</div>

Upon arriving at the scene, start by interviewing the client with a few key questions to set the foundation for your investigation:

- What do you think has happened?
- What systems are affected?
- How important is this system to production?

These questions will help you determine how to proceed. Keep in mind how critical the system is to the client—delays might cost them significant losses. If time is of the essence, they should ideally have a backup system ready for situations like this. If not, you could assist in setting up a backup (even though it’s technically outside your scope).

Whatever you do, DO NOT alter the crime scene without proper documentation. If you must process the scene quickly, prioritize live analysis to address the client’s urgency. However, remember that this approach limits the number of artefacts or evidence you can gather compared to a more thorough imaging process (aka static analysis).

### Live analysis. 
Before diving into the investigation and potentially altering evidence, start by using tools like [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) and [Autopsy](https://www.autopsy.com/) or any other artifact collection applications to analyze recent activity. Another excellent option is [FTK Imager](https://www.exterro.com/ftk-product-downloads/ftk-imager-4-7-3-81) , which can also perform memory analysis on a live system. Depending on the situation, [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) may be sufficient, but for a more thorough investigation, using both [gKAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) and [FTK Imager](https://www.exterro.com/ftk-product-downloads/ftk-imager-4-7-3-81) is recommended. 

Once you have everything extracted and documented, you then can get into dynamic analysis of the malware/exploit or whatever. 

### Static analysis.
If you're dealing with a live system when you arrived then **Static analysis** should be a second priority. Static analysis takes a lot of time and depending on the situation, a thorough live analysis of the affected machine should suffice. Anyways, first you need to remove every storage drives in the system since you don't want to deal with RAID systems and missing a HDD and all that so better pay attention >->. You can use your own machine to conduct the imaging process, you can use [TestDisk](https://www.cgsecurity.org/wiki/TestDisk_Download) or [DMDE](https://dmde.com/).  Choose your preferred format, such as .dd or any other that fits your situation.

> [!IMPORTANT]
> Depending on your hardware data imaging will take AGES!!! '-'

To do a full imaging of a system can take a long time and if it’s a server you can take a vacation and come back and it’s not finished imaging. It is also expensive, imaging a 1 TB drive requires another 1 TB drive to store the image and this is called **Physical imaging**. That said, you have options. Physical imaging captures everything but takes the longest. **Logical imaging** is faster but less thorough. Carefully consider the situation to decide the best approach for your investigation. There's also **RAW imaging** but this for cases where you need more details or for **Corrupted data recovery**.

> [!IMPORTANT]
> Use **WRITE BLOCKER** I don't care how experienced you are a **WRITE BLOCKER IS ESSENTIAL** '~'

# Website incident handling (Phishing).

Let’s talk about website-related incidents. One common issue is the defacement of a client’s website. If the client has set up their web server properly, they should have a Security Information and Event Management (SIEM) system or an Intrusion Detection System (IDS) in place to prevent malicious activity. If that’s the case, it’s mostly about finding the logs, reviewing them, and implementing a fix to prevent the incident from happening again. But it’s not that simple. 

<div align="center">
    <img src="https://github.com/user-attachments/assets/abc58982-595b-404b-8706-4aee1fb2b1bb" width="800" height="500">
</div>

Clients will want a thorough report and investigation done before moving into the eradication process. This is where the analysis part of the job comes in. Assuming the client has an SIEM/IDS system in place, your first task is to trace which machine or computer carried out the malicious activity.Any remote attack **MUST** originate from an infected machine, so identifying that machine is crucial. If it’s a network of machines involved, you’ll need to **ISOLATE** them by separating them from the main network. (Talk with the company’s engineer…They don’t have one ? Welp it’s now your job :P).

Once the machines are isolated, begin the identification process. If it's a network of infected machines, it’ll take more than just you to get it done quickly. You’ll need a team to move efficiently.

Start by commanding one of your team members to interview the employees. They may have seen something unusual or noticed any signs of the attack before it escalated. Meanwhile, you or another member should work on isolating the machines from the network and securing any potential entry points.

While the interviews are happening, keep an eye on the overall network.Once the network is contained, it’s time to dive into the forensics. Use your tools to analyze the compromised systems, check logs, and gather evidence that can point to how the attack occurred, what vulnerabilities were exploited, and what impact it had on the system.

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
    <img src="https://github.com/user-attachments/assets/a84879ae-e7ff-4e74-af34-c9f5398f514f" width="500" height="700">
</div>

<br><br>

It should open a new tab named **Original Message**. Next you need to download the .eml file.

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
Another way is to dynamically analyze the malware. Every piece of malware has a goal, and achieving that goal requires processing power from the infected machine. You can use [Procmon](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon) from Microsoft itself, to identify suspicious services and processes running on the system (make sure you learn how to use this properly '-'). There **was** also an application called **Winpatrol**, but unfortunately, it has been sent to heaven (RIP Scotty, you were the best puppy Y-Y). [Procmon](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon)  depending on the situation, can give you insights into what the malware’s goals are and provide enough data to include in your report. However, static analysis and reverse engineering can help you understand the malware in even greater detail.








