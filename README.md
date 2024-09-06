# Ticket-Reservation-System-Vuln
This is a repo for disclosure of a vulnerability in Ticket Reservation System
# Stored XSS Vulnerability in itsourcecode Ticket Reservation System 1.0
## Overview

A stored Cross-Site Scripting (XSS) vulnerability has been identified in itsourcecode Ticket Reservation System 1.0. This issue occurs when an authenticated attacker can add an event with an unsanitized name, leading to the execution of arbitrary JavaScript in the context of other users.

## Description

In itsourcecode Ticket Reservation System 1.0, users with authenticated access can create events. The event name field does not perform adequate sanitization or validation, allowing an attacker to inject malicious scripts. When other users view these events, the injected script is executed in their browsers, potentially leading to data theft, session hijacking, or other malicious actions.

## Impact

Type: Stored XSS
Affected Users: Any user who views the event with the injected script
Potential Impact:
Data theft (e.g., cookies, local storage)
Session hijacking
Phishing attacks
Any actions that can be performed by the script

## Steps to Reproduce
1. Login: Log in to itsourcecode Ticket Reservation System 1.0 with an authenticated account.
2. Add Event: Navigate to the event creation page.
3. Inject Script: In the event name field, enter the following payload
<script>alert(document.cookie);</script>
4. Save Event: Save the event.
5. View Event: Log out and view the event as a different user or have another user view it.

## Mitigation
To prevent this vulnerability, the following measures should be taken:

Sanitize Input: Ensure that all user input, especially in fields like event names, is properly sanitized and escaped before rendering on the page.
Validate Input: Implement input validation to only allow safe characters and formats.
Use a CSP: Consider implementing Content Security Policy (CSP) headers to reduce the impact of any potential XSS.

![image](https://github.com/user-attachments/assets/dfeb255f-8c33-4e3b-a25e-b7207f84efaa)
