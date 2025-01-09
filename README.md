# Brute Force Attack Analysis with Splunk

This project demonstrates how to analyze and detect a brute force attack using a sample `auth.log` file in Splunk. It showcases the skills of log analysis, threat detection, and creating visualizations to highlight attacker activity.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Dataset](#dataset)
- [Questions](#questions)
- [Splunk Queries](#splunk-queries)
- [Dashboard](#dashboard)
- [How to Use](#how-to-use)
- [Results](#results)
- [Future Improvements](#future-improvements)
- [License](#license)

## Overview
Brute force attacks are common and dangerous. This project:
- Detects brute force attempts in `auth.log`.
- Identifies the attacker, targeted accounts, and successful breaches.
- Visualizes attack patterns.

This project is part of my journey as a SOC analyst and penetration tester.

## Features
1. Identify repeated failed login attempts (brute force).
2. Detect successful logins after failed attempts.
3. Locate attacker IP addresses.
4. Visualize attack patterns with time charts and dashboards.
5. Provide insights to mitigate future attacks.

## Dataset
The analysis uses a sample Linux `auth.log` file. The data is anonymized to protect sensitive information.

- File: `Dataset/auth.log`

## Questions
Below are questions that can be used for analysis 
1. Analyzing the auth.log, can you identify the IP address used by the attacker to carry out a brute force attack?.
2. The brute force attempts were successful, and the attacker gained access to an account on the server. What is the username of this account?
3. Can you identify the timestamp when the attacker manually logged in to the server to carry out their objectives?
4. SSH login sessions are tracked and assigned a session number upon login. What is the session number assigned to the attacker's session for the user account from Question 2?
5. The attacker added a new user as part of their persistence strategy on the server and gave this new user account higher privileges. What is the name of this account?
6. What time did the attacker's first SSH session end according to auth.log?
7. The attacker logged into their backdoor account and utilized their higher privileges to download a script. What is the full command executed using sudo?

## Splunk Queries
The following Splunk queries are included:
- **Failed Login Attempts**: Analyze IPs with the most failed login attempts.
- **Successful Logins After Failure**: Detect successful logins post-failure.
- **Attacker IP address**: Use to identify attacker locations.
- **Attack Timeline**: Visualize attack patterns over time.

Queries are available in the [`queries/`](queries/) folder.

## Dashboard
A pre-built Splunk dashboard is included to visualize:
1. Failed login attempts by IP and username.
2. Successful logins after failed attempts.
3. Attack trends over time.

Dashboard XML: [`dashboard/brute_force_dashboard.xml`](dashboard/brute_force_dashboard.xml)

## How to Use
1. Upload the `auth.log` file into Splunk.
2. Use the queries from the [`queries/`](queries/) folder to analyze the data.
3. Import the dashboard XML file into Splunk:
   - Go to **Settings > Dashboards**.
   - Click **Import** and upload `brute_force_dashboard.xml`.
4. Explore the visualizations and insights.

## Results
- **Attack Summary**:
  - Attackers IP Address: `X`
  - Targeted User Account: `192.168.1.100`
  - Timestamp when the attacker manually logged: `admin, root`
  - SSH login sessions number:
  - New User added by attacker:
  - Time the attacker's first SSH session ended:
  - Full command executed by attacker using sudo: 


- **Mitigation Recommendations**:
  - Enforce account lockout policies.
  - Implement multi-factor authentication (MFA).
  - Monitor and block suspicious IPs.

## Future Improvements
- Automate detection using alerts.
- Integrate threat intelligence to flag malicious IPs.
- Include other log sources (e.g., web, application).

## License
This project is licensed under the [MIT License](LICENSE).
