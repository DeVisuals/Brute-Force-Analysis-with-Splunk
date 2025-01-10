# Analyzing Auth.Log Files Using Splunk SIEM

## Introduction
Authentication logs (auth.log) are crucial for understanding user access patterns and identifying potential security threats. Splunk SIEM (Security Information and Event Management) provides powerful capabilities for analyzing authentication logs to detect unauthorized access attempts, failed logins, or other suspicious activities.

## Prerequisites
Before analyzing Auth logs in Splunk, ensure the following:
- Splunk instance is installed and configured.
- Auth log data sources are configured to forward logs to Splunk.

## Steps to Upload Sample Auth.Log Files to Splunk SIEM

### 1. Use the auth.log Sample Log File provided in the dataset folder 
- You can also use anyother Log files you want to analyze

### 2. Upload Log Files to Splunk
- Log in to the Splunk web interface.
- Navigate to **Settings** > **Add Data**.
- Select **Upload** as the data input method.

### 3. Choose File
- Click on **Select File** and choose the sample auth log file you prepared earlier.

### 4. Set Source Type
- In the **Set Source Type** section, specify the source type for the uploaded log file.
- Choose the appropriate source type for Auth logs (e.g., `auth.logs` or a custom source type if applicable).

### 5. Review Settings
- Review other settings such as index, host, and sourcetype.
- Ensure the settings are configured correctly to match the sample auth log file.

### 6. Click Upload
- Once all settings are configured, click on the **Review** button.
- Review the settings one final time to ensure accuracy.
- Click **Submit** to upload the sample Auth.log file to Splunk.

### 7. Verify Upload
- After uploading, navigate to the search bar in the Splunk interface.
- Run a search query to verify that the uploaded Auth events are visible.
  
  ```spl
  index=_* OR index=* sourcetype=Auth.logs


## Steps to Analyze AUTH Log Files in Splunk SIEM

### 1. Search for Auth.log Events   
- Open Splunk interface and navigate to the search bar.   
- Enter the following search query to retrieve DNS events   
```
index=* sourcetype=Auth.logs
```

### 2. Extract Relevant Fields
- Identify key fields in AUTH logs such as Host IP/ Domain name, destination IP, Failed password, Accepted password etc.
- 
index=_* OR index=* sourcetype=Auth.logs failed_password="Failed password"
```

### 3. Identify Anomalies
- Look for unusual patterns or anomalies in DNS activity.
- Example query to identify spikes
```
index=_* OR index=* sourcetype=dns_sample  | stats count by fqdn
```

### 4. Find the top DNS sources
- Use the top command to count the occurrences of each query type:   
```
index=* sourcetype=dns_sample | top fqdn, src_ip
```



### 5. Investigate Suspicious Domains
- Search for domains associated with known malicious activity or suspicious behavior.
- Utilize threat intelligence feeds or reputation databases to identify malicious domains such virustotal.com
- Example search for known malicious domains:
```
index=* sourcetype=dns_sample fqdn="maliciousdomain.com"
```

## Conclusion
Analyzing DNS log files using Splunk SIEM enables security professionals to detect and respond to potential security incidents effectively. By understanding DNS activity and identifying anomalies, organizations can enhance their overall security posture and protect against various cyber threats.

Feel free to customize these steps according to your specific use case and requirements. 

Happy analyzing!



