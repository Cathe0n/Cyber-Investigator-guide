# Cyber Investigator guide. | Mobile Forensics. | MD-Next
This guide aims to assist investigators focused on cybercrime by guiding incident handling, response, and thorough, methodical evidence processing. It is intended as a supplementary resource to support investigators and serves as a reminder rather than a standalone procedure.

<div align="center">
    <img src="https://github.com/user-attachments/assets/03b6eb47-e661-459d-88c8-4f915f63058e" style="width: 40%; max-width: 300; max-height: 300;">
</div>

# Introduction.

For this guide, we will focus on using MD-NEXT (not a download link btw >->). This tool is incredibly advanced and challenging to acquire, typically reserved for National agencies, companies, or specialised organisations. If you're lucky enough to have access to this bad boy, you're pretty pog! ^-^

Before diving in, ensure you have physical access to the mobile device. Obtaining passwords and login information is needed to do your investigation. Remember, as forensic investigators, consent is key we’re not hackers here. Our role is to operate within legal and ethical boundaries, respecting privacy while carrying out necessary investigations. Don't do anything that'll get you fired!! >_>



# Prepping the Mobile Handphone for analysis.
The first step in any mobile device investigation is to switch the phone to **Airplane Mode**. This prevents the device from accessing the internet, ensuring that no remote commands can trigger a data wipe or altering any information. It's a standard operating procedure to protect evidence integrity and prevent potential tampering. OR!!! Use a Faraday cage room thingy just to be safe! :3

<br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/65855ad7-c0f3-4081-b489-a68b27f0b2df" style="width: 70%; max-width: 1000; max-height: 500;">
</div>

<br>

### Developer option prepping procedure.

The password or login information is essential because it allows you to enable Developer mode! Many tools used in forensic investigations, like MD-NEXT or Cellebrite UFED, require USB Debugging or similar settings to be active the settings only accessible through Developer Options.

Find your device model and search for the steps specific to it. Most Android devices follow this general method:

- Go to Settings > About Phone.
- Tap on Build Number 7 times until a message says, "You are now a developer!"
- Access Developer Options from the main settings menu.
- Enable USB Debugging and any additional settings required by your forensic tool.

Don't forget to enable Stay awake mode in Andorid Developer option. Also turn off any sleep function within the phone! You don't want it to interfere with the imaging process! >-> Also also, allow USB debugging for computer with RSA key thingy say **Allow** you'll see it! :3

### iOS device prepping procedure.

For iOS devices, the situation is different. You need to press Yes for any prompt that pops up on the device and it'll be boring, yes but it is what is '-' you need to continue this process until MD-Next or Cellebrite UFED can do it's magic! :3

<br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/964b292d-cb9e-41b6-9bd5-edd974fa2e04" style="width: 70%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/7742296b-075a-4dd2-b850-a55967dc181c" style="width: 70%; max-width: 1000; max-height: 500;">!

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/88d1614f-18ac-46b1-9261-5b271d137c9c" style="width: 70%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/3786b7ef-3b95-4599-8517-4ea204220ec0" style="width: 70%; max-width: 1000; max-height: 500;"> 

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/d6d325ed-a1d0-4907-9314-9aa339285db0" style="width: 70%; max-width: 1000; max-height: 500;"> 

</div>


<div align="center">
    <img src="https://github.com/user-attachments/assets/2b85751f-7e8a-490e-b314-acb9ee407d49" style="width: 70%; max-width: 1000; max-height: 500;"> 

</div>

# MD-Next procedure.

MD-NEXT is a powerful forensic tool designed for comprehensive mobile device analysis. It includes detailed, step-by-step instructions embedded within the application to guide users through various processes. Make sure you follow them and check the documentation or contract support if you have any issues! :3 

<div align="center">
    <img src="https://github.com/user-attachments/assets/772ac8ac-d22d-4a5c-9a92-20c18fc87f76" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/24f1b1c7-8f6a-4b1f-8384-40efad7491be" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/eee69315-22df-4a9a-909f-49a6cb92874d" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/a7f4f738-4c47-46ba-aca4-c73fbffb945c" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/47b8b825-5620-466d-86bb-c9dea23f6db9" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/a3634f8b-0769-48f0-afea-5bd85a4b5324" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/845776b1-6129-4931-a551-9ecd8eb32b28" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/04fedd1f-2091-4d0f-b4b9-86a92331412b" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<br>

# MD-RED extraction result analysis.
I usually use MD-RED ad MD-Explorer to analyse the results. You can see almost everything, including WhatsApp, Discord and whatever messaging app that is installed in the phone. Now, some deleted messages will not be available unfortunately so be mindful! >->


<div align="center">
    <img src="https://github.com/user-attachments/assets/8a15a6fc-09e0-4d3c-abe9-5a7a42d67bd1" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/150f443f-df30-475f-84e9-fdecafa77903" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/29768eba-03b5-4950-ae6e-2aa9a05b0b6f" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/53f3082e-886c-4273-b64a-c0bb385de947" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/bb124add-4aaf-494a-b6ca-5ace84af78f9" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/6efa8967-9df7-46df-9f07-bf76d693fb11" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<div align="center">
    <img src="https://github.com/user-attachments/assets/8cb0c69b-6476-4439-af70-f21190c40eac" style="width: 100%; max-width: 1000; max-height: 500;"> ![389830329-8cb0c69b-6476-4439-af70-f21190c40eac](h)


</div>

<br>

# Downgrade application for more thorough analysis.
In certain cases, newer application patches may prevent Cellebrite or MD-Next from conducting a full analysis. To address this, these tools often provide an option to downgrade the application to a version compatible with thorough analysis. However, **Becareful!** >->. Downgrading an application can potentially lead to data loss or corruption. For example, WhatsApp messages might disappear, or errors could occur when attempting to restore the app to its latest version after analysis. Always weigh the risks and document to avoid complications.

<br>

<div align="center">
    <img src="https://github.com/user-attachments/assets/72f4c79d-8d61-4c36-a430-99302f1e83c0" style="width: 100%; max-width: 1000; max-height: 500;">

</div>

<br>

# Final words.

I understand this guide is short af, mobile phone forensic is a complex and expansive subject. I plan to update this guide with more open-source tools and techniques when I have the time to compile and write them down. Currently, this guide focuses primarily on using MD-NEXT, and I apologise if you were expecting more information about publicly available tools '-'.

If you wish to improve or expand this guide, feel free to fork it, and I'll gladly review and merge contributions into the main repository! :3

Thank you for your understanding, and I apologise ' ^ '

