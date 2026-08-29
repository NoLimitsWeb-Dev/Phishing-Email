# Phishing-Email
First Phishing Email Project

Here is a comprehensive, professional README.md report tailored for your GitHub repository. It emphasizes the authorized, educational nature of your project while detailing the technical architecture you built.

My First Phishing: Controlled Security Awareness Simulation

📝 Project Overview:
This repository documents my first hands-on cybersecurity project: an authorized, fully isolated phishing simulation campaign. The objective of this project was to understand the underlying mechanics of social engineering attacks, study tracking metrics, and explore defensive mitigation strategies.
To maintain complete safety, ethical boundaries, and compliance, this project was executed entirely in a localized loop. The simulated emails never left the host machine and were intercepted locally, ensuring no real-world infrastructure or unintended users were impacted.

🛠️ System Architecture & Tools:
The project environment was built on a Windows 11 host utilizing an offline, sandboxed architecture:
GoPhish (v0.12+): An open-source phishing framework used to compile user groups, design baseline email templates, host landing pages, and track interaction timelines.MailHog: A local, developer-focused SMTP testing tool. 
MailHog acted as an internal mail server that intercepted and held all outgoing messages, preventing them from routing to the live internet.
Windows Defender Configurations: Tailored exclusion paths were implemented to host the simulation binaries securely without interrupting local OS firewalls.
