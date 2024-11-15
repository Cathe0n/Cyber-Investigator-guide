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

This can give you an idea/foundation on how to proceed with investigating the incident. Take note of how important the system is to the client, you cannot delay them too much as they are actively losing money. If there’s a time crunch the client should have a backup in place just for such an incident but if that’s not the case try to assist in setting up a backup system (technically not your job though sooo). DO NOT affect the crime scene without documentation. You either process the crime scene live and as fast as possible since it’s crucial to the client. This of course limits how many artefacts/crumbs can be gathered compared to the imaging process or also known as offline analysis. 


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

Here you can see what EML Analyzer has provided. [EML Analyzer](https://analyzer.sublime.security/) has VirusTotal API integrated into it so you can see if the attachments are malicious or not.

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

### Malware analysis! (This is big brain time d(>_< ) ).

I’m going to be honest,  this is where things are complicated and time consuming. Malware analysis is a WHOLE nother topic and I will make another guide for it soon bare with me!! >-<. 

First identify **HOW** the malware breached the systems.

- Phishing Email ?
- Bad USB/Physical infection ?
- Pirated software ?




