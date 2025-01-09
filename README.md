# Brute Force Attack Analysis with Splunk

```bash
   index="your_index" sourcetype="linux_auth" "Failed password"
   | stats count by src_ip user
   | sort -count




This project demonstrates how to analyze and detect a brute force attack using a sample `auth.log` file in Splunk. It showcases the skills of log analysis, threat detection, and creating visualizations to highlight attacker activity.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Dataset](#dataset)
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
- Visualizes attack patterns and geolocates attackers.

This project is part of my journey as a SOC analyst and penetration tester.

## Features
1. Identify repeated failed login attempts (brute force).
2. Detect successful logins after failed attempts.
3. Geolocate attacker IP addresses.
4. Visualize attack patterns with time charts and dashboards.
5. Provide insights to mitigate future attacks.

## Dataset
The analysis uses a sample Linux `auth.log` file. The data is anonymized to protect sensitive information.

- File: `datasets/auth.log`

## Splunk Queries
The following Splunk queries are included:
- **Failed Login Attempts**: Analyze IPs with the most failed login attempts.
- **Successful Logins After Failure**: Detect successful logins post-failure.
- **Geolocation of Attacker IPs**: Use `iplocation` to identify attacker locations.
- **Attack Timeline**: Visualize attack patterns over time.

Queries are available in the [`queries/`](queries/) folder.

## Dashboard
A pre-built Splunk dashboard is included to visualize:
1. Failed login attempts by IP and username.
2. Successful logins after failed attempts.
3. Geographical locations of attackers.
4. Attack trends over time.

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
  - Total Failed Login Attempts: `X`
  - Attacker IP Address: `192.168.1.100`
  - Targeted User Accounts: `admin, root`
  - Geolocation: `City: Lagos, Country: Nigeria`
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
