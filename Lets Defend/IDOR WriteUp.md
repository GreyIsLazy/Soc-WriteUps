# Alert Analysis: [Possible IDOR Attack]

**Date:** [2022-02-28T22:48:05+03:00]
**Platform:** LetsDefend
**Severity:** Medium
**Category:** Web Attack.

---

## 1. Alert Overview

"Meduim-severity alert was trigerred by a webServer. Alert Flaged as
consecutive requests to the same page".
---

## 2. Investigation Steps

### Step 1: [Search for the IP in virusTotal]
"i Searched in virusTotal for that IP. and it was flagged as Criminal IP".

### Step 2: [Read Logs in Log Management (WebServer001)]
"after reading some logs in the alert time. i found 5 'POST' requests to
https://172.16.17.15/get_user_info/?user_id=1-5. http response code was '200 OK'".

### Step 3: [Making my Verdict + Report + Escalation]
"i made my verdict "True Positive" depend on what i found in the investigation step.
endpoint was isolated. required blocking the ip and notify dev team with the vulnerability in the webServer.
and Escalate the alert after typing my Report on the incident."

---

## 3. Artifacts Found

| Type       | Value              | Notes                        |
|------------|--------------------|------------------------------|
| IP Address | 134.209.118.137    | Flagged on VirusTotal (02/90)|
| user Agent | MISE 6.0           | outdated UserAgent           |

---

## 4. Verdict

**TRUE POSITIVE ✓**
On 2022-02-28 between 19:45 and 19:48 UTC, external IP 134.209.118.137
(flagged malicious on VirusTotal) sent consecutive POST requests to
https://172.16.17.15/get_user_info/ on WebServer1005, incrementing
user_id from 1 to 5. The User-Agent (MSIE 6.0) is outdated and
suspicious. All requests returned 200 OK and were allowed by the
device; response content shows data of different users returned.

---

## 5. Recommended Actions
- Escalate to L2/IR
- Block the IP address at the firewall level
- Quarantine the affected endpoint
- Notify the dev Team with the Vulnerability

---

## 6. Lessons Learned
1. i learned that 'Response code' Shows if Server Allowed the Attack request or block it.
2. and 'Rsponse Size' can tell if data actually returned and if data leaked successflly.

---

## 7.. Mistakes , Something i missed
this user agent is outdated so its very suspicious flag i missed"
- Lesson :  Check the User Agent as Well (it can be an artifact)
