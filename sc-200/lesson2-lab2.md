---

lab:
title: Explore Microsoft Security Copilot Use Cases
description: In this exercise, you explore how Microsoft Security Copilot supports incident investigation, alert analysis, and advanced security investigation in Microsoft Defender XDR.
level: 200
islab: true
-----------

## Lab scenario

Your organization wants to improve the efficiency of its security operations team and strengthen its incident response capabilities. The office of the CISO has identified Microsoft Security Copilot as a tool that can help analysts investigate incidents, summarize alerts, analyze affected entities, and recommend response actions.

In this lab, you will explore two common Microsoft Security Copilot use cases:

1. Investigating the context and activity associated with a security incident.
2. Analyzing security artifacts and performing an advanced investigation.

> **Important**
>
> The original interactive simulations may not be available or may not function correctly. Complete the activities below by reviewing the provided screenshots, instructor demonstration, or Microsoft Defender XDR training environment.
>
> Your instructor may also provide a recorded demonstration or replacement simulation.

## Learning objectives

By the end of this lab, you should be able to:

* Explain how Microsoft Security Copilot supports incident investigation.
* Identify important information in an incident summary.
* Review alerts, devices, users, and other related entities.
* Describe how Security Copilot can support advanced investigation.
* Recommend appropriate investigation and response actions.

## Part 1: Investigate incident context and activity

### Task 1: Review the incident overview

1. Open Microsoft Defender XDR or the demonstration environment provided by your instructor.

2. From the navigation menu, select **Incidents & alerts**.

3. Select **Incidents**.

4. Open the incident assigned by your instructor.

5. Review the following information:

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

1. Locate the incident summary or Security Copilot summary.

2. Read the summary and identify:

   * The suspected initial attack activity
   * The first affected device or user
   * The main alerts associated with the incident
   * The possible attack objective
   * The sequence of important events

3. Write a brief summary of how the incident appears to have started and progressed.

### Task 3: Examine the incident timeline

1. Open the incident timeline, attack story, or activity view.
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

1. Review the devices, users, IP addresses, files, processes, or mailboxes associated with the incident.

2. Select one affected device.

3. Record the following information:

   * Device name
   * Operating system
   * Risk level
   * Exposure level
   * Logged-on users
   * Related alerts

4. Select one affected user account.

5. Record the following information:

   * User name
   * User risk level
   * Related alerts
   * Devices used by the account
   * Any unusual sign-in or account activity

### Task 5: Use Security Copilot prompts

If Security Copilot is available, enter prompts similar to the following:

* Summarize this incident.
* What devices and users are affected?
* What was the likely initial access method?
* Create a timeline of the incident.
* What actions should the security analyst take next?

Review the generated response and verify that it matches the incident evidence.

If Security Copilot is not available, review the instructor-provided example responses and identify the information that each prompt is intended to produce.

## Part 2: Analyze artifacts and perform an advanced investigation

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

1. Select a suspicious file, process, IP address, URL, or user account from the alert.

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

### Task 5: Identify recommended response actions

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
