
# Unified Kill Chain - TryHackMe

## Objective
The objective is to understand an attacker's “Kill Chain” so that defensive measures can be put in place to either pre-emptively protect a system or disrupt an attacker's attempt.

## Tools Used
- Event Viewer
- Sysmon
- Splunk (via THM)

## Summary
- Detected brute-force login attempts
- Traced back to IP 192.168.0.50
- Identified attacker used PowerShell after access

## Steps Taken
1. Queried failed logon attempts (Event ID 4625)
2. Filtered by IP, found repeated failures
3. Investigated success (Event ID 4624) and follow-up commands

## Outcome
Attack identified, source confirmed, recommendation to block IP and reset credentials.

## Screenshot
![login-event](./images/login-failures.png)
