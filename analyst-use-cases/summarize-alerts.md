# 🧠 Use Case: Summarize Security Alerts with a Local LLM

Analysts often receive alerts filled with raw data, metadata, and cluttered formatting — making it hard to quickly see the *real issue*. This guide shows how to use a local LLM (e.g., Mistral via Ollama) to summarize an alert into a few clear, actionable bullet points — fully offline and private.

---

## 🔧 Requirements

- [Ollama](https://ollama.com/) installed and running locally
- A downloaded model like `mistral`, `llama3`, or `codellama`
- A sample alert to summarize

---

## 📝 Sample Alert Input

Below is a sample security alert that we want to summarize:

Alert ID: 43812
Rule: Excessive Failed Logon Attempts
Detected on: WIN-HOST-21
User: admin
Time: 2024-07-18T13:22:00Z
Source IP: 192.168.100.45

Details:

- 25 failed logon attempts using "admin"
- Logons occurred over 90 seconds
- Attempts made via RDP (port 3389)
- Alert triggered by rule: RDP Bruteforce Detector (v2.1)
---
## 🧪 Example Prompt to Paste into Ollama
```text
You are a cybersecurity analyst. Summarize the following security alert into 3 short bullet points, focusing on the key threat and what should be reviewed next:

Alert ID: 43812
Rule: Excessive Failed Logon Attempts
Host: WIN-HOST-21
User: admin
Time: 2024-07-18T13:22:00Z
IP: 192.168.100.45
25 failed logon attempts over 90 seconds via RDP (port 3389)
Triggered by rule: RDP Bruteforce Detector (v2.1)
```
Sample expected output:
```text
> • Multiple failed RDP logon attempts (25 in 90s) on WIN-HOST-21
> • Username "admin" targeted from 192.168.100.45
> • Possible brute force attempt — review logs, block IP if untrusted
```

---

## 💡 Why This Matters

- Reduces analyst fatigue from verbose alerts  
- Helps junior analysts get to the point quickly
- Leads to better questions 
- Encourages faster triage decisions  
- Works fully offline with no risk to sensitive data

---

## 🛠 Tips for Better Summaries

- Remove unrelated metadata before prompting  
- Use clear and consistent formatting for each alert  
- Test different models for style and tone  
- Always verify the LLM’s summary before acting on it

---

## 📊 Optional: Ask for a Table Format

If you want the LLM to return information in a structured way — like a Markdown table — you can prompt it clearly to do so.

### 🔹 Example Prompt (Request Table Format)
```text
You are a cybersecurity analyst. Summarize the following alert in a 3-row Markdown table with the following columns:
• Key Finding
• Reason for Concern
• Recommended Action

Alert:
25 failed logon attempts using "admin" over 90 seconds via RDP (port 3389)
Host: WIN-HOST-21
IP: 192.168.100.45
Rule Triggered: RDP Bruteforce Detector (v2.1)
```
An example expected output:
```text
| Key Finding                 | Reason for Concern                        | Recommended Action                |
| --------------------------- | ----------------------------------------- | --------------------------------- |
| Multiple failed RDP logons  | Indicates possible brute force attempt    | Review host logs, block IP        |
| Admin account targeted      | High-value account at risk                | Enforce lockout policy, MFA       |
| Fast repetition (25 in 90s) | Consistent with automated attack patterns | Consider alert tuning, escalation |
```
This format makes summaries easier to copy into reports, dashboards, or emails.

> 💡 If the LLM doesn’t return the correct format on the first try, rephrase the prompt slightly or ask it to “reformat the same answer as a table.”
---
## 🧩 Ideas to Expand This

- Build a small tool or script to paste in alerts and return summaries  
- Use Streamlit or Flask to create a local summarization interface  
- Make it part of your daily SOC workflow

---

