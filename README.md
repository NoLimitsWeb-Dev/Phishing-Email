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
- <img width="1605" height="817" alt="image" src="https://github.com/user-attachments/assets/af5fa683-64d8-4dfc-a075-8ec7d4fe59f4" />
- Click on Sending Profiles in the left menu, then click New Profile.
- <img width="1910" height="947" alt="image" src="https://github.com/user-attachments/assets/eef05cad-d4d4-4a76-a8c5-4d6ebb111735" />

- Fill out the fields exactly like this: Name: MailHog ServerFrom: IT Security <security@simulation.local> (You can make up any fake address here)Host: 127.0.0.1:1025 (This tells GoPhish to send emails directly into MailHog)Leave the Username, Password, and Ignore Certificate Errors fields completely blank.
<img width="1902" height="891" alt="image" src="https://github.com/user-attachments/assets/93e2ec47-35c0-4480-bd89-21649953555f" />
Click Save Profile.


Step 3: Set Up Your 2 Target Emails
- Click on Users & Groups in the left menu.
- <img width="1896" height="901" alt="image" src="https://github.com/user-attachments/assets/090a1586-369a-4c06-a53c-eb341942e911" />

- Click New Group and name it My Targets.
- Add your two or more test email addresses.(Note: Because MailHog catches all outgoing emails locally, you can actually type any email address here, but using your real ones is great for practicing the exact workflow).
- <img width="1881" height="906" alt="image" src="https://github.com/user-attachments/assets/1af4110b-469e-4314-91a6-535b36211e77" />

- Click Save Changes.


Step 4: Draft the Email Template
- In the GoPhish dashboard, navigate to Email Templates and click New Template. A beginner-friendly simulation should focus on a standard, recognizable corporate notification.
- <img width="1860" height="881" alt="image" src="https://github.com/user-attachments/assets/b657185d-018b-4b13-a16b-42a7c1a1180d" />

- Envelope Sender: Set the "From" field to look realistic but slightly off, such as IT Support <support@yourcompany-securitytest.com>.
- Subject Line: Use a clear, action-oriented subject like Action Required: Password Expiration Notice.
- The Body Text: Write a short, professional message. State that the user's password expires in 24 hours and provide a link to resolve it.
- Insert the Tracking Link: Highlight your call-to-action text (e.g., "Click Here to Reset"), click the link icon, and enter {{.URL}}. GoPhish automatically replaces this placeholder with a unique tracking link for each recipient. <img width="858" height="737" alt="image" src="https://github.com/user-attachments/assets/e7db4716-bc7d-4827-8f45-1cd8d461395f" />

<img width="1896" height="890" alt="image" src="https://github.com/user-attachments/assets/819eb1a0-f5a5-44ed-8b35-881d3957b649" />
              <img width="1575" height="762" alt="image" src="https://github.com/user-attachments/assets/ab655e51-6cff-4d27-b125-f223cd2e4e13" />




Step 5: Build the Landing Page
Navigate to Landing Pages and click New Page. This is where users land if they click your link.
<img width="1888" height="855" alt="image" src="https://github.com/user-attachments/assets/a755c14c-9d2d-4219-808f-11d8a12493e1" />

- Design the Page: You can use simple HTML to create a basic page that says "This is a security simulation."Do Not Collect Data: Ensure the "Capture Submitted Credentials" option is turned off. For a beginner project, you only want to track who clicks, not harvest actual passwords.
<img width="1892" height="925" alt="image" src="https://github.com/user-attachments/assets/6619b2bb-5e06-4851-b8bc-3e3336d6e5ee" />


Step 6: Create the User Group and Launch
- Users & Groups: Click New Group and manually enter 2 or 3 of your own test email addresses. Never target external users or people who have not given explicit, written permission.
- <img width="1906" height="906" alt="image" src="https://github.com/user-attachments/assets/d875eb38-2ae2-44ae-8ff3-9daf7bcb5d64" />



Now have all the individual puzzle pieces ready:
1. Windows 11 Exclusion is active.
2. MailHog is ready to catch emails.
3. Sending Profile points to MailHog (127.0.0.1:1025).
4. Users & Groups contains your 2 target emails.
5. Email Template is saved with {{.URL}}.
6. Landing Page is saved.


Let's launch your project! This is where we tie GoPhish and MailHog together to see your tracking metrics work in real-time.


Step 1: Open the Campaign Menu
- Log into your GoPhish dashboard (https://127.0.0.1:3333).
- Click on Campaigns in the left sidebar menu.
- Click the blue New Campaign button at the top right.
<img width="1890" height="821" alt="image" src="https://github.com/user-attachments/assets/0d6d4f05-dbaf-4a6d-9531-21a3066f9e6a" />

Step 2: Fill Out the Campaign Details
Configure the fields exactly like this to ensure the traffic routes correctly on your Windows 11 machine:
- Name: Give it a name (e.g., My First Phishing Test).
- Template: Select the email template you just created from the dropdown menu.
- Landing Page: Select the landing page you just saved.
- URL: Type exactly http://127.0.0.1 (This tells GoPhish to host the landing page on your local computer).
- Sending Profile: Select MailHog Server (the one pointing to 127.0.0.1:1025).
- Groups: Select your target group containing your 3 email addresses.

Step 3: Launch the Campaign
- Scroll down to the bottom of the page.
- Click the blue Launch Campaign button.
- GoPhish will immediately push the two emails through MailHog.
<img width="1868" height="905" alt="image" src="https://github.com/user-attachments/assets/3930b8ee-fe56-4dec-a1fa-843dc30a2f4e" />
<img width="1885" height="898" alt="image" src="https://github.com/user-attachments/assets/8a911ec6-23c9-4696-bdff-d888909f9163" />

Step 4: Now Watch it Work (The Fun Part!)
Now, let's trigger the tracking metrics manually:
1. Open MailHog: Open a new browser tab and go to http://127.0.0.1:8025.
2. View the Emails: You will see your three simulated emails sitting in the MailHog inbox. Click on one of them to read it.
<img width="1907" height="355" alt="image" src="https://github.com/user-attachments/assets/dadf1a05-1b97-47b7-934a-86d159ee8baf" />

3. Click the Tracking Link: Inside the email body, click your blue "Click on the link". It will open your custom "Security Simulation Notice" landing page.
   <img width="1905" height="865" alt="image" src="https://github.com/user-attachments/assets/9d90380d-eaff-469f-9158-35f3551d05ea" />
   <img width="1917" height="512" alt="image" src="https://github.com/user-attachments/assets/170e7210-aa60-4faf-8cfa-68b656ceac71" />


4. Check the GoPhish Dashboard: Switch back to your GoPhish tab (https://127.0.0.1:3333) and look at your campaign. Refresh the page if needed.
<img width="1320" height="680" alt="image" src="https://github.com/user-attachments/assets/f97ad858-7582-41a0-abbf-a90338bb586c" />
Simulating user behavior, the test emails were opened, and the tracking links were interacted with.
The GoPhish dashboard immediately registered the webhook callbacks, populating real-time timeline charts for Sent, Opened, and Clicked actions.
You will see the timeline update instantly, showing the exact second the email was Sent, Opened, and Clicked!


📊 Project Findings & Key Metrics
Total Targets: 3 Delivery Success 
Rate: 100% (Local interception successful)
Email Open Rate: 100%
Link Click-Through Rate: 100%

Defensive Takeaways
1. Urgency as a Weapon: The "24-hour expiration" urgency indicator is highly effective at forcing split-second decisions before a user reviews technical anomalies.
2. Slight Domain Mismatches: Spoofed sender envelopes (e.g., support@internal-it-update.local) can easily deceive an untrained eye if they mirror corporate naming conventions.
3. The Importance of Reporting: Technical controls (like local filters) are a solid line of defense, but user education and clear "Report Phishing" pipelines are vital to stop active campaigns early.


⚠️ Ethical Standards & Compliance Disclaimer
This project was conducted strictly for educational, defensive, and research purposes.
* No real user credentials or sensitive pieces of information were harvested, logged, or stored.
* All test targets were personal accounts under direct ownership of the author.
* No emails were routed across public networks, ensuring complete alignment with standard authorization regulations and white-hat methodologies.
