# Phishing-Email
First Phishing Email Project

Here is a comprehensive, professional README.md report tailored for your GitHub repository. It emphasizes the authorized, educational nature of your project while detailing the technical architecture you built.

My First Phishing: Controlled Security Awareness Simulation

📝 Project Overview:

This repository documents my first hands-on cybersecurity project: an authorized, fully isolated phishing simulation campaign. The objective of this project was to understand the underlying mechanics of social engineering attacks, study tracking metrics, and explore defensive mitigation strategies.

To maintain complete safety, ethical boundaries, and compliance, this project was executed entirely in a localized loop. The simulated emails never left the host machine and were intercepted locally, ensuring no real-world infrastructure or unintended users were impacted.

🛠️ System Architecture & Tools:
The project environment was built on a Windows 11 host utilizing an offline, sandboxed architecture:

* GoPhish (v0.12+): An open-source phishing framework used to compile user groups, design baseline email templates, host landing pages, and track interaction timelines.MailHog: A local, developer-focused SMTP testing tool. 

* MailHog acted as an internal mail server that intercepted and held all outgoing messages, preventing them from routing to the live internet.

* Windows Defender Configurations: Tailored exclusion paths were implemented to host the simulation binaries securely without interrupting local OS firewalls.


[ GoPhish Engine ] 
       │
       ▼ (Sends Test Email via SMTP Port 1025)
[ MailHog Server ] <── Intercepts & Keeps Traffic Local (Port 8025 Web UI)
       │
       ▼ (User Clicks tracked {{.URL}})
[ Local Landing Page ] (Hosted securely at http://127.0.0.1)

🛠️ Setup
* Windows Defender Configurations: Tailored exclusion paths were implemented to host the simulation binaries securely without interrupting local OS firewalls.

Since I am using Windows 11 and targeting my own test email addresses, I easily configure Windows Defender (the default Windows 11 antivirus) to let GoPhish run safely.

Here is the exact step-by-step process to set up  folder exclusion and safely handle test emails.

Step 1: Set Up the Windows 11 Antivirus Exclusion
- Press the Windows Key, type Windows Security, and press Enter.
- Click on Virus & threat protection.
- Under Virus & threat protection settings, click Manage settings.
- Scroll down to the bottom of the page and click Add or remove exclusions (under the Exclusions header).
- Click the Add an exclusion button and select Folder.
- Browse to and select the specific folder where you downloaded or extracted GoPhish.
Windows Defender will now completely ignore this folder, allowing GoPhish to run without being blocked or deleted.


Using GoPhish together with MailHog is the absolute best and safest way to run this project.
MailHog acts as a "fake" local email server. It catches every email GoPhish sends and displays it in a local web dashboard. This means your test emails never leave your computer and will never be blocked by real spam filters, making it 100% secure.
Here is the exact step-by-step guide to linking GoPhish and MailHog on your Windows 11 machine.

Step 1: Download and Run MailHog

- Go to the official MailHog GitHub Releases page.
- Download the Windows executable file (usually named MailHog_windows_amd64.exe).
- <img width="1515" height="836" alt="image" src="https://github.com/user-attachments/assets/9a4bf886-578c-4d46-beb0-3d8b63e00454" />

- Move this file into your Windows Defender exclusion folder alongside GoPhish.
- Double-click the MailHog file to run it. A black command prompt window will open. Leave this window open.
- <img width="1106" height="842" alt="image" src="https://github.com/user-attachments/assets/6dc80525-958e-428e-ad9d-2bb0fcb413d6" />

- MailHog is now running in the background. It uses port 1025 to receive emails and port 8025 to show you the inbox.
- <img width="1468" height="195" alt="image" src="https://github.com/user-attachments/assets/7f2f62c7-cea1-40db-9c44-c227b74a9004" />


Step 2: Configure GoPhish to use MailHog
- Download GoPhish: Get the official software from the GoPhish GitHub repository.
- <img width="1577" height="890" alt="image" src="https://github.com/user-attachments/assets/721e5ea1-ff2d-4568-b5f2-5cb4841942eb" />
- <img width="1633" height="540" alt="image" src="https://github.com/user-attachments/assets/3706e0e7-55aa-4069-af4a-3ef466e1b56e" />


- Launch the Tool: Run the executable file and log into the local admin dashboard (usually https://127.0.0.1:3333).
- Open your browser and log into your GoPhish dashboard (https://127.0.0.1:3333).
- Click on Sending Profiles in the left menu, then click New Profile.Fill out the fields exactly like this:Name: MailHog ServerFrom: IT Security <security@simulation.local> (You can make up any fake address here)Host: 127.0.0.1:1025 (This tells GoPhish to send emails directly into MailHog)Leave the Username, Password, and Ignore Certificate Errors fields completely blank.Click Save Profile.

