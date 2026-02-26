Investigation Summary:

During analysis of the BOTSv1 dataset (1–31 August 2016), evidence confirmed that the website www[.]imreallynotbatman[.]com
was compromised and defaced.

Investigation identified external reconnaissance using Acunetix Web Vulnerability Scanner, followed by brute-force authentication attempts against the Joomla administrator portal. Successful credential abuse allowed the attacker to upload a malicious executable (3791.exe) associated with the hash ec78c938d8453739ca2a370b9c275971ec46caf6e479de2b2d04e97cc47fa45d.

Primary malicious activity originated from IP 40[.]80[.]148[.]42, with additional activity from 23[.]22[.]63[.]114.

The incident demonstrates a full attack chain: reconnaissance → brute-force → file upload → defacement.

Severity: High
Impact: Website compromise and public defacement.

Key Findings

Primary Attacker IP: 40[.]80[.]148[.]42 (responsible for ~90% of related traffic).

Secondary IP: 23[.]22[.]63[.]114 (associated with brute-force attempts).
<img width="601" height="280" alt="one(1 5)" src="https://github.com/user-attachments/assets/b8bc31de-1a6f-4939-bc71-9e5561fdb463" />


Reconnaissance Activity: FortiGate signature ID 39679 identified Acunetix Web Vulnerability Scanner targeting Joomla endpoints.
<img width="200" height="200" alt="five" src="https://github.com/user-attachments/assets/7d2b3a03-40af-4099-8935-b85ef574015c" /> <img width="200" height="203" alt="six" src="https://github.com/user-attachments/assets/ad2a5da4-820c-4b0c-83e1-ca9b821a18d7" /> 


Brute-Force Window: 2016-08-10 21:45:21 – 21:48:05 (repeated POST requests to /joomla/administrator/index.php).
<img width="304" height="490" alt="seven" src="https://github.com/user-attachments/assets/e478de03-88ee-42f6-a8a8-9051fb2ac306" /> <img width="1127" height="650" alt="eleven" src="https://github.com/user-attachments/assets/3ff0cd9f-44f8-4f29-9417-23cba4fa113a" />



Successful Authentication: Valid login observed following failed attempts.

Malicious File Upload: 3791.exe uploaded to web server.

SHA256 Hash: ec78c938d8453739ca2a370b9c275971ec46caf6e479de2b2d04e97cc47fa45d

VirusTotal Analysis: File confirmed malicious.
<img width="1042" height="414" alt="thirteen" src="https://github.com/user-attachments/assets/5aefabf0-61f5-4a04-8d44-61b27d663aff" />


CMS Identified: Joomla (via URI patterns).

Impact: Website defacement confirmed.

Incident Timeline
<img width="703" height="329" alt="IncidentTimeline" src="https://github.com/user-attachments/assets/0a116af5-ee2f-4202-b303-88506968ee3f" />


Technical Analysis
Firewall logs (fgt) were analyzed within the scoped timeframe (1–31 August 2016). Statistical aggregation identified IP 40.80.148.42 as the dominant external source.

FortiGate attack ID 39679 indicated web vulnerability scanning activity. Correlation with HTTP request patterns confirmed systematic enumeration of Joomla-specific endpoints.

Subsequent analysis of authentication-related URIs revealed high-frequency POST requests to /joomla/administrator/index.php, consistent with brute-force attempts. A successful login event followed this activity.

File inspection logs (fgt_utm) identified upload of executable 3791.exe, later confirmed malicious via hash analysis.

MITRE ATT&CK Mapping

T1595 – Active Scanning: https://attack.mitre.org/techniques/T1595/

T1110 – Brute Force: https://attack.mitre.org/techniques/T1110/

T1105 – Ingress Tool Transfer: https://attack.mitre.org/techniques/T1105/

T1491 – Defacement: https://attack.mitre.org/techniques/T1491/

T1078 – Valid Accounts: https://attack.mitre.org/techniques/T1078/
