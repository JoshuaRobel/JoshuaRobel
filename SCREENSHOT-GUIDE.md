# Screenshot Guide for SOC Portfolio

**Visual Evidence Documentation**

This guide provides detailed instructions for capturing screenshots to enhance your portfolio investigations with visual evidence.

---

## Why Screenshots Matter

**Hiring Manager Perspective:**
> "Anyone can write about investigations. Screenshots prove you've actually used the tools. I want to see Splunk dashboards, Wireshark captures, and EDR consoles. It demonstrates practical experience, not just theoretical knowledge."

---

## Required Screenshots by Repository

### 01-SIEM-Triage-and-Investigation

#### Screenshot 1: Splunk Search Query
**File:** `screenshots/splunk-brute-force-search.png`  
**Location in case:** SOC-2026-001  

**What to capture:**
```
- Splunk search bar showing: index=wineventlog EventCode=4625
- Search results showing failed logon events
- Interesting Fields panel showing src_ip, Account_Name
- Time range picker showing 24-hour view
- Statistics tab showing event count
```

**How to capture:**
1. Run the SPL query in your Splunk instance
2. Use Snipping Tool (Windows) or Screenshot (Mac)
3. Save as PNG with descriptive filename
4. Redact any sensitive internal IP addresses if needed

---

#### Screenshot 2: Splunk Dashboard
**File:** `screenshots/splunk-failed-auth-dashboard.png`  

**What to capture:**
```
- Dashboard with multiple panels:
  - Timechart of failed logins over time
  - Pie chart of logon types
  - Table of top source IPs
  - Map of geolocated IPs
- Title: "Failed Authentication Analysis"
- Time range: Last 24 hours
```

**How to create:**
1. Save your search as a dashboard panel
2. Add visualizations (timechart, stats, etc.)
3. Use Splunk's dashboard editor to arrange
4. Screenshot the complete dashboard

---

### 03-Network-Traffic-and-Alert-Analysis

#### Screenshot 1: Snort Alert in Console
**File:** `screenshots/snort-alert-console.png`  
**Location in case:** NET-2026-001

**What to capture:**
```
- Snort alert output showing:
  [Classification: ET MALWARE Possible malicious file download]
  [Priority: 1]
  02/10-09:14:33.123456  [**] [1:1000001:1] 
  ET MALWARE Possible malicious file download [**]
  [Classification: Attempted User Privilege Gain] 
  [Priority: 1] {TCP} 192.168.45.102:49152 -> 185.234.72.19:80
```

**How to capture:**
1. Run Snort with your rules
2. Trigger or wait for alert
3. Screenshot the console/terminal output
4. Or use Snorby/Sguil web interface

---

#### Screenshot 2: Wireshark Packet List
**File:** `screenshots/wireshark-malicious-download.png`  
**Location in case:** NET-2026-001

**What to capture:**
```
- Wireshark main window showing:
  - Packet list (top pane):
    No.  Time    Source          Destination     Protocol  Info
    1255 9:14:26 192.168.45.102  185.234.72.19   HTTP      GET /download/system-update.exe HTTP/1.1
    1289 9:14:28 185.234.72.19   192.168.45.102  HTTP      HTTP/1.1 200 OK (application/x-msdownload)
  - Display filter bar: ip.addr == 192.168.45.102 && http
  - Status bar: Showing 47 packets
```

**How to capture:**
1. Open your PCAP in Wireshark
2. Apply display filter
3. Navigate to relevant packets
4. Screenshot showing packet numbers and details

---

#### Screenshot 3: Wireshark Protocol Analysis
**File:** `screenshots/wireshark-http-analysis.png`

**What to capture:**
```
- Middle pane: Packet Details expanded
  - Frame
  - Ethernet II
  - Internet Protocol Version 4
  - Transmission Control Protocol
  - Hypertext Transfer Protocol
    - Request Method: GET
    - Request URI: /download/system-update.exe
    - Host: updates-service.net
    - User-Agent: Mozilla/5.0...
```

---

#### Screenshot 4: TCP Stream Reconstruction
**File:** `screenshots/wireshark-tcp-stream.png`

**What to capture:**
```
- Right-click packet → Follow → TCP Stream
- Stream content showing:
  - HTTP request headers
  - HTTP response headers
  - Binary data indicator (non-printable characters)
- Show in ASCII mode
```

---

### 04-SOC-Detections-and-Sigma

#### Screenshot 1: Sigma Rule in VS Code
**File:** `screenshots/sigma-rule-vscode.png`  
**Location in case:** SIGMA-001

**What to capture:**
```
- VS Code window showing:
  - File explorer: detections/SIGMA-001.md
  - Editor: YAML content with syntax highlighting
  - YAML structure visible:
    title:
    status:
    logsource:
    detection:
    condition:
```

**How to create:**
1. Open Sigma rule in VS Code
2. Install YAML extension for syntax highlighting
3. Screenshot showing clean formatting

---

#### Screenshot 2: Splunk Search Results from Sigma
**File:** `screenshots/splunk-sigma-results.png`

**What to capture:**
```
- Splunk search using converted SPL
- Results showing:
  - _time, Account_Name, src_ip columns
  - Multiple rows of failed logon events
  - Event count: 47 results
- Search bar showing SPL query
```

---

### 05-SOC-Incident-Reports

#### Screenshot 1: EDR Host Isolation
**File:** `screenshots/edr-host-isolation.png`  
**Location in case:** CASE-001

**What to capture:**
```
- SentinelOne/CrowdStrike console showing:
  - Host list with WS-HR-047
  - Status: Isolated (red icon)
  - Last seen: 2 minutes ago
  - Agent status: Online (isolated)
  - User: sarah.chen
- Action log showing isolation timestamp
```

**How to capture:**
1. Use EDR demo/trial environment
2. Isolate test endpoint
3. Screenshot the console
4. Or use DetectionLab with built-in EDR

---

#### Screenshot 2: VirusTotal Results
**File:** `screenshots/virustotal-file-analysis.png`

**What to capture:**
```
- VirusTotal file report showing:
  - Detection ratio: 28/72 engines
  - Community score: -100
  - File type: Win32 EXE
  - First seen: 2026-02-08
  - Detection tab: List of AV detections
    - Microsoft: Trojan:Win32/TrickBot
    - Kaspersky: Trojan.Win32.TrickBot
    - etc.
```

---

### 06-Phishing-Triage-and-Email-Analysis

#### Screenshot 1: Email Header Analysis
**File:** `screenshots/email-header-analysis.png`  
**Location in case:** PHISH-001

**What to capture:**
```
- Message Header Analyzer output:
  Authentication Results:
  - SPF: FAIL
  - DKIM: None
  - DMARC: FAIL
  
  Routing:
  - Originating IP: 203.0.113.89 (Bulgaria)
  - Mail server: mail.micros0ft-security.net
  
  Security Checks:
  - Domain age: 3 days (suspicious)
  - Blacklist status: Listed on Spamhaus
```

**How to capture:**
1. Use mxtoolbox.com/EmailHeaders.aspx
2. Paste email headers
3. Screenshot the analysis results
4. Or use built-in email client header view

---

#### Screenshot 2: URLScan.io Results
**File:** `screenshots/urlscan-phishing-page.png`

**What to capture:**
```
- URLScan.io report showing:
  - Screenshot of phishing page (Microsoft login replica)
  - Domain: microsoft-365-verify.com
  - IP: 45.77.123.45
  - Server: Apache
  - Country: Bulgaria
  - Malicious: Yes (15/72 detections)
  - Categories: Phishing
```

---

## Screenshot Best Practices

### DO:
- ✅ Use PNG format for clarity
- ✅ Redact sensitive internal IPs (use 192.168.x.x or 10.x.x.x)
- ✅ Ensure text is readable (at least 12pt equivalent)
- ✅ Highlight/annotate key areas with arrows or boxes
- ✅ Use consistent naming: `tool-case-description.png`

### DON'T:
- ❌ Include real company data or customer information
- ❌ Use screenshots from your actual employer without permission
- ❌ Make screenshots too small to read
- ❌ Include personal information

---

## Tools for Home Lab Screenshots

Don't have access to enterprise tools? Use these free alternatives:

### SIEM (Splunk)
- **Splunk Free** (500MB/day): splunk.com/en_us/download.html
- **DetectionLab**: DetectionLab.network (pre-built with Splunk)
- **Splunk Attack Range**: Attack range with sample data

### Network Analysis (Wireshark)
- **Wireshark**: Free, works with any PCAP
- **PCAP files**: malware-traffic-analysis.net (free samples)
- **DetectionLab**: Includes malicious traffic captures

### EDR
- **OSQuery**: Free endpoint visibility
- **Velociraptor**: Free DFIR tool
- **Wazuh**: Free SIEM with endpoint agents

### Email Analysis
- **Email samples**: https://github.com/eldondev/gophish-templates
- **Fake SMTP**: Mailtrap.io (free tier)

---

## Screenshot Workflow

1. **Set up your lab environment**
   - Install Splunk Free or DetectionLab
   - Load sample data or generate your own

2. **Recreate the investigation**
   - Follow your written case steps
   - Execute the same queries/commands

3. **Capture evidence**
   - Screenshot each key step
   - Save with descriptive filenames

4. **Review and redact**
   - Blur/obscure any sensitive info
   - Ensure consistency across screenshots

5. **Add to repository**
   - Create `screenshots/` folder
   - Update markdown with image references
   - Commit and push

---

## Quick Reference: Screenshot Checklist

### Per Investigation:
- [ ] Tool console/dashboard showing the alert/query
- [ ] Evidence/results of the investigation
- [ ] Analysis/decision documentation

### Recommended Minimum:
| Repository | Minimum Screenshots |
|------------|-------------------|
| 01-SIEM | 2 (search query, dashboard) |
| 03-Network | 3 (Wireshark capture, stream, VT) |
| 04-Sigma | 2 (rule code, search results) |
| 05-Incidents | 2 (EDR isolation, timeline) |
| 06-Phishing | 2 (header analysis, URL scan) |

**Total: ~11 screenshots across portfolio**

---

## Example: Adding Screenshot to Markdown

```markdown
### Screenshot: Splunk Failed Authentication Query

![Splunk Search Results](./screenshots/splunk-brute-force-search.png)

**Analysis:** The search identified 47 failed authentication attempts 
from a single source IP (203.0.113.45) over a 5-minute period, 
triggering the brute force detection threshold.
```

---

**Note:** Screenshots significantly strengthen your portfolio by providing 
visual proof of hands-on experience. Take the time to create quality screenshots 
— they're worth more than pages of text to hiring managers.

---

**Last Updated:** February 2026  
**Author:** Joshua Robel
