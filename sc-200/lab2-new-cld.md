---
lab:
  title: Explore Microsoft Security Copilot Use Cases
  description: In this exercise, you explore how Microsoft Security Copilot supports incident investigation, alert analysis, and advanced security investigation in Microsoft Defender XDR.
  level: 200
  islab: true
---

## Lab scenario

Your organization wants to improve the efficiency of its security operations team and strengthen its incident response capabilities. The office of the CISO has identified Microsoft Security Copilot as a tool that can help analysts investigate incidents, summarize alerts, analyze affected entities, and recommend response actions.

In this lab, you will explore two common Microsoft Security Copilot use cases:

1. Investigating the context and activity associated with a security incident.
2. Analyzing security artifacts and performing an advanced investigation.

> **Important**
>
> The original interactive simulations are no longer available. This lab instead uses your live CloudLabs environment. A freshly deployed tenant has no incidents yet, so **Part 1** below has you onboard your device and generate a real one — a genuine multi-stage attack simulation, not a canned example. Parts 2 and 3 then investigate that real incident.

## Learning objectives

By the end of this lab, you should be able to:

* Explain how Microsoft Security Copilot supports incident investigation.
* Identify important information in an incident summary.
* Review alerts, devices, users, and other related entities.
* Describe how Security Copilot can support advanced investigation.
* Recommend appropriate investigation and response actions.

> **Note:** Devices and user accounts in this environment are limited (a single **WIN1** device and one admin account), so "affected device" and "affected user" throughout this lab refer to that device/account rather than a wider fleet. That's expected here.

## Part 1: Onboard your device and generate an incident

### Task 1: Verify device onboarding

1. Sign in to the **WIN1** virtual machine as **Admin** with the password provided in your CloudLabs environment.

2. Start the Microsoft Edge browser and go to the Microsoft Defender XDR portal at <https://security.microsoft.com>.

3. Sign in with the admin account and password provided in your CloudLabs environment.

4. From the navigation menu, under **Assets**, select **Devices**. Wait until **WIN1** appears in the Devices list before continuing.

    > **Note:** If WIN1 doesn't appear after about an hour, that indicates an onboarding or connectivity problem — check with your instructor before continuing.

### Task 2: Simulate an attack to generate a real incident

> **Warning:** Only run this simulated attack in the course-provided CloudLabs environment.

1. On the WIN1 virtual machine, search for **PowerShell**, right-click **Windows PowerShell**, and choose **Run as Administrator**. Select **Yes** on the User Account Control prompt.

2. In the elevated PowerShell window, navigate to the **Allfiles** folder on the desktop and run the attack simulation script:

    ```powershell
    cd C:\Users\Admin\Desktop\Allfiles
    .\AttackScript.ps1
    ```

3. If PowerShell shows a security warning that the script is from an untrusted publisher (because it was downloaded), type **R** and press **Enter** to **Run Once**.

4. The script produces a few lines of output ending with a message that it *Failed to resolve Domain Controllers in the domain* — this is expected. A few seconds later, **Notepad** opens automatically with simulated attack code injected into it, which attempts to contact an external IP address (simulating a command-and-control server). Leave this Notepad window open.

5. In the Microsoft Defender XDR portal, expand **Investigation & response**, expand **Incidents & alerts**, and select **Incidents**.

    > **Note:** On newer versions of the portal, *Incidents & alerts* is found directly under *Investigation & response*. If the incident doesn't appear yet, wait a few minutes and refresh, or clear the *Alert severity* filter.

6. Confirm a new incident named **"Multi-stage incident involving Defense evasion & Discovery on one endpoint"** appears. This is the incident you'll investigate for the rest of this lab.

    > **Note:** This can take several minutes after step 4 to show up, since Defender for Endpoint needs time to detect and correlate the activity into an incident. If it still hasn't appeared after 15 minutes, verify Defender for Endpoint onboarding completed (Task 1) before retrying Task 2.

## Part 2: Investigate incident context and activity

### Task 1: Review the incident overview

1. In the Microsoft Defender XDR portal, from the navigation menu, select **Incidents & alerts**.

2. Select **Incidents**.

3. Open the incident named **"Multi-stage incident involving Defense evasion & Discovery on one endpoint"** — the incident you generated in Part 1.

4. Review the following information:

   * Incident title
   * Incident severity
   * Incident status
   * Assigned analyst
   * Number of alerts
   * Affected devices
   * Affected users
   * Incident start time
   * Most recent activity

6. Record the incident title, severity, and status in your lab report.

### Task 2: Review the incident summary

1. On the open incident page, select the **Summary** tab (and the **Attack story** tab, if shown). If Microsoft Security Copilot is enabled for your tenant, an AI-generated narrative summary appears at the top of the Attack story tab — this is the "Security Copilot summary." If it isn't shown, use the Summary tab's built-in incident overview instead.

2. Read the summary and identify:

   * The suspected initial attack activity
   * The first affected device or user
   * The main alerts associated with the incident
   * The possible attack objective
   * The sequence of important events

3. Write a brief summary of how the incident appears to have started and progressed.

### Task 3: Examine the incident timeline

1. On the incident page, select the **Attack story** tab. Collapse the Alerts and Incident details panes to see the full **incident graph**, then select the **Play attack story** run icon to replay the attack timeline alert by alert.
2. Review the alerts in chronological order.
3. Identify the earliest suspicious event.
4. Identify at least two actions that occurred after the initial event.
5. Record the sequence of events in the following format:

| Order | Event or alert | Affected entity | Significance |
| ----- | -------------- | --------------- | ------------ |
| 1     |                |                 |              |
| 2     |                |                 |              |
| 3     |                |                 |              |

### Task 4: Review related entities

1. On the incident page, select the **Assets** tab (some tabs may be hidden — select the ellipsis **...** to see them all) to review the devices, users, IP addresses, files, and processes associated with the incident.

2. Select the affected device (**WIN1**).

3. Record the following information:

   * Device name
   * Operating system
   * Risk level
   * Exposure level
   * Logged-on users
   * Related alerts

4. Select the affected user account (**Admin**).

5. Record the following information:

   * User name
   * User risk level
   * Related alerts
   * Devices used by the account
   * Any unusual sign-in or account activity

### Task 5: Use Security Copilot prompts

1. On the incident page, look for a **Copilot** icon or pane (usually top-right of the Defender XDR portal). Select it to open the Copilot chat pane.

    > **Note:** Microsoft Security Copilot requires purchased Security Compute Units (SCUs), which are **not** included in this course's trial tenant by default. If no Copilot pane appears, or it shows a message that Copilot isn't provisioned/enabled, that's expected here — skip to step 3.

2. If Copilot is available, enter prompts similar to the following, then review each generated response and verify it matches the incident evidence you already gathered in Tasks 1–4:

   * Summarize this incident.
   * What devices and users are affected?
   * What was the likely initial access method?
   * Create a timeline of the incident.
   * What actions should the security analyst take next?

3. If Copilot is not available, answer each of the five prompts above yourself, using only the incident data you reviewed in Tasks 1–4 (Summary/Attack story tab, timeline, Assets tab). This demonstrates the same analysis Copilot would otherwise accelerate.

## Part 3: Analyze artifacts and perform an advanced investigation

### Task 1: Review an alert

1. Open one of the alerts associated with the incident.

2. Review the following information:

   * Alert title
   * Severity
   * Detection source
   * Affected device
   * Affected user
   * Process name
   * File name
   * IP address
   * Timestamp
   * Recommended actions

3. Record the alert details in your lab report.

### Task 2: Analyze a suspicious artifact

1. On the incident page, select the **Evidence and response** tab, then select **IP addresses**. Select the displayed IP address (this is the external address the simulated attack tried to contact, imitating a C2 server) — in the pop-up, select **Open IP address page** to review it in full. (You can also pick a suspicious file, process, or URL from an alert instead, if one is present.)

2. Review the available evidence.

3. Determine:

   * Why the artifact was identified as suspicious
   * Which device or user was affected
   * Whether the artifact appears malicious or benign
   * What additional investigation is required

4. Record your conclusion and supporting evidence.

### Task 3: Investigate process activity

If process information is available:

1. Review the process tree.
2. Identify the parent process.
3. Identify the suspicious child process.
4. Review the command-line arguments.
5. Look for unusual PowerShell, command prompt, script, or executable activity.
6. Record the suspicious process chain.

Example:

```text
Parent process:
Child process:
Command line:
Reason the activity is suspicious:
```

### Task 4: Review device and user context

1. Open the affected device page.
2. Review recent alerts, logged-on users, and device risk.
3. Open the affected user page.
4. Review sign-in activity, related incidents, and associated devices.
5. Determine whether the incident appears limited to one device or involves multiple entities.

    > **Note:** In this trial tenant there's normally only one device (WIN1) and one user (Admin), so you should expect the incident to appear limited to a single device/user — that's a realistic scenario, just a small one. In a production tenant with more assets, the same review steps would scale to a wider set of entities.

### Task 5: Identify recommended response actions

> **Caution:** Do not actually execute containment actions (isolate device, disable account, etc.) against WIN1 or the Admin account in this task — WIN1 is the only virtual machine in your environment, and isolating it or disabling its account would cut off your own access. Treat this task as a planning/discussion exercise: identify what you *would* do and justify it, without performing the action in the portal.

Based on the available evidence, identify appropriate response actions.

Possible actions include:

* Isolate the affected device.
* Disable or reset the affected user account.
* Block a malicious IP address or URL.
* Quarantine or remove a malicious file.
* Run an antivirus scan.
* Collect an investigation package.
* Review additional devices for similar activity.
* Escalate the incident to a senior analyst.

Select at least three actions and explain why each action is appropriate.

## Lab deliverables

Submit a short lab report containing:

1. The incident title, severity, and status.
2. A summary of how the incident started and progressed.
3. A table containing at least three events from the incident timeline.
4. Details about one affected device and one affected user.
5. Details about one alert and one suspicious artifact.
6. Three recommended response actions.
7. Screenshots of the incident, alert, device, or user pages, when available.

## Knowledge check

Answer the following questions:

1. How can Security Copilot help an analyst understand a complex incident?
2. Why should an analyst verify a Copilot-generated summary against the original evidence?
3. What information can be obtained by reviewing an affected device?
4. Why is the process tree useful when investigating suspicious activity?
5. What factors should an analyst consider before isolating a device?
6. What response actions would you recommend for the incident reviewed in this lab?

## Summary

In this lab, you explored how Microsoft Security Copilot can support incident investigation in Microsoft Defender XDR. You reviewed incident context, analyzed alerts and affected entities, examined suspicious artifacts, and identified appropriate response actions.

Security Copilot can accelerate an investigation by summarizing complex information, connecting related events, generating timelines, and recommending next steps. However, analysts must validate Copilot-generated results against the original security evidence before taking action.
