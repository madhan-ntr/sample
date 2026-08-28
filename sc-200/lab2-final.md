---
lab:
  title: Explore Microsoft Security Copilot Use Cases
  description: In this exercise, you explore how Microsoft Security Copilot supports incident investigation, alert analysis, and advanced security investigation in Microsoft Defender XDR.
  level: 200
  islab: true
---

## Lab scenario

Your organization wants to improve the efficiency of its security operations team and strengthen its incident response capabilities. The office of the CISO has identified Microsoft Security Copilot as a tool that can help analysts investigate incidents, summarize alerts, analyze affected entities, and recommend response actions.

> **Important**
>
> The original interactive simulations are no longer available. This lab instead uses your live CloudLabs environment. A freshly deployed tenant has no incidents yet, so **Exercise 1** below has you onboard your device and generate a real one — a genuine multi-stage attack simulation, not a canned example. Exercises 2 and 3 then investigate that real incident.

## Lab objectives

In this lab, you will complete the following exercises:

- Exercise 1: Onboard your device and generate an incident
- Exercise 2: Investigate incident context and activity
- Exercise 3: Analyze artifacts and perform an advanced investigation

By the end of this lab, you should be able to:

- Explain how Microsoft Security Copilot supports incident investigation.
- Identify important information in an incident summary.
- Review alerts, devices, users, and other related entities.
- Describe how Security Copilot can support advanced investigation.
- Recommend appropriate investigation and response actions.

## Estimated timing: 60 minutes

> **Note:** Devices and user accounts in this environment are limited (a single **WIN1** device and one admin account), so "affected device" and "affected user" throughout this lab refer to that device/account rather than a wider fleet. That's expected here.

## Exercise 1: Onboard your device and generate an incident

WIN1 isn't onboarded yet on a freshly deployed environment — nothing onboards it automatically, so you'll do it directly, then run a real (simulated) attack so you have a genuine incident to investigate in the rest of this lab.

### Task 1: Onboard WIN1 to Microsoft Defender for Endpoint

1. Sign in to the **WIN1** virtual machine as **Admin** with the password provided in your CloudLabs environment.

2. Start the Microsoft Edge browser and go to the Microsoft Defender XDR portal at <https://security.microsoft.com>.

3. Sign in with the admin account and password provided in your CloudLabs environment.

4. From the navigation menu, scroll down, expand the **System** section, and select **Settings**.

    > **Note:** Some versions of the portal may not have **Settings** under **System** — it may be grouped with *Reports* and *Audit* instead.

5. On the Settings page, select **Device discovery**, and confirm **Standard discovery (recommended)** is selected under Discovery setup.

    > **Hint:** If the option isn't visible, refresh the page.

6. From the navigation menu, expand **System** again, select **Settings**, then select **Endpoints**.

7. Select **Onboarding** in the Device management section. WIN1 runs Windows Server, so under **Select operating system to start onboarding process**, choose **Windows Server 2019, 2022, and 2025** (not the default "Windows 10 and 11," which is for client OS devices).

8. In the *1. Onboard a device* area, leave **Connectivity** set to *Streamlined* and **Deployment method** set to *Local Script (for up to 10 devices)*.

9. Select **Download onboarding package**.

10. In the *Downloads* pop-up, highlight *GatewayWindowsDefenderATPOnboardingPackage.zip* and select the folder icon **Show in folder** (or find it under `C:\Users\Admin\Downloads`).

    > **Tip:** If Edge blocks the download, select the ellipsis (**...**) and choose **Keep**, then **Show more** → **Keep anyway** on the follow-up warning.

11. Right-click the zip file, select **Extract All...**, keep *Show extracted files when complete* checked, and select **Extract**.

12. Right-click the extracted **WindowsDefenderATPLocalOnboardingScript.cmd** file, select **Properties**, check the **Unblock** box, and select **OK**.

13. Right-click **WindowsDefenderATPLocalOnboardingScript.cmd** again and select **Run as Administrator**. If Windows SmartScreen appears, select **More info** → **Run anyway**.

14. When the User Account Control prompt appears, select **Yes**. When the script asks a Y/N question, type **Y** and press **Enter**. Wait for the message **"Successfully onboarded machine to Microsoft Defender for Endpoint"**, then press any key to close the window.

15. Back in the Defender XDR portal, go to <https://security.microsoft.com/machines> (the **Assets** menu in this portal doesn't list "Devices" directly — use this link instead). Wait until **WIN1** appears in the Device Inventory list — this can take some time (occasionally over an hour) after onboarding completes.

    > **Note:** If WIN1 doesn't appear at all after several hours, that indicates a genuine onboarding or connectivity problem — check with your instructor before continuing.

    ![Device Inventory list showing the onboarded device with Total, Critical assets, High risk, and Exposure counts.](./Media/sc200-l3-device-inventory-list.png)

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

6. Confirm a new incident appears in the list.

    > **Note:** Defender XDR names incidents dynamically based on the techniques it detects, and can rename an incident later as its automated investigation (and Attack Disruption, if triggered) learns more — don't expect a fixed title. Since this is a fresh environment, it should be the only incident listed; that's how you'll recognize it, not its name. This is the incident you'll investigate for the rest of this lab.

    > **Note:** This can take several minutes after step 4 to show up, since Defender for Endpoint needs time to detect and correlate the activity into an incident. If it still hasn't appeared after 15 minutes, verify Defender for Endpoint onboarding completed (Task 1) before retrying Task 2.

## Exercise 2: Investigate incident context and activity

### Task 1: Review the incident overview

1. In the Microsoft Defender XDR portal, from the navigation menu, select **Incidents & alerts**.

2. Select **Incidents**.

3. Open the incident (it should be the only one listed) — the one you generated in Exercise 1. Its title may not match what you saw right after Exercise 1; that's expected (see the note in Exercise 1, Task 2).

4. Review the following information:

   - Incident title
   - Incident severity
   - Incident status
   - Assigned analyst
   - Number of alerts
   - Affected devices
   - Affected users
   - Incident start time
   - Most recent activity

5. Record the incident title, severity, and status in your lab report.

    ![Incident overview page showing title, severity, status, tabs (Attack story, Alerts, Activities, Assets), and the Tasks panel.](./Media/sc200-l3-incident-overview.png)

### Task 2: Review the incident summary

1. On the open incident page, select the **Summary** tab (and the **Attack story** tab, if shown). If Microsoft Security Copilot is enabled for your tenant, an AI-generated narrative summary appears at the top of the Attack story tab — this is the "Security Copilot summary." If it isn't shown, use the Summary tab's built-in incident overview instead.

2. Read the summary and identify:

   - The suspected initial attack activity
   - The first affected device or user
   - The main alerts associated with the incident
   - The possible attack objective
   - The sequence of important events

3. Write a brief summary of how the incident appears to have started and progressed.

    ![Summary tab showing Alerts and categories, Scope, Evidence, and the Incident information panel.](./Media/sc200-l3-summary-tab.png)

### Task 3: Examine the incident timeline

1. On the incident page, select the **Attack story** tab. Collapse the Alerts and Incident details panes to see the full **incident graph**, then select the **Play attack story** run icon to replay the attack timeline alert by alert.

    ![Attack story tab with the incident graph and an AI-generated incident description on the right.](./Media/sc200-l3-attack-story.png)

2. Review the alerts in chronological order.

3. Identify the earliest suspicious event.

4. Identify at least two actions that occurred after the initial event.

5. Record the sequence of events in the following format:

    | Order | Event or alert | Affected entity | Significance |
    | ----- | -------------- | --------------- | ------------ |
    | 1     |                |                 |              |
    | 2     |                |                 |              |
    | 3     |                |                 |              |

    ![Alerts pane after selecting Play attack story, with the incident graph and Priority assessment panel showing MITRE ATT&CK techniques.](./Media/sc200-l3-play-attack-story.png)

### Task 4: Review related entities

1. On the incident page, select the **Assets** tab (some tabs may be hidden — select the ellipsis **...** to see them all) to review the devices, users, IP addresses, files, and processes associated with the incident.

2. Select the affected device (**WIN1**). If it isn't a clickable link there, go to <https://security.microsoft.com/machines> instead and select it from the Device Inventory list.

3. Record the following information:

   - Device name
   - Operating system
   - Risk level
   - Exposure level (may show "No data available" if the device was onboarded recently — that's expected, not an error)
   - Logged-on users (may show "0" or "No data found" even when a user is actively signed in — this is a known reporting delay, not a sign the account isn't real)
   - Related alerts

4. Select the affected user account (**Admin**). The incident may list two user entities — pick the real named account, not a placeholder identity like `S-1-0-0`.

5. Record the following information:

   - User name
   - Open incidents / active alerts for this user
   - MFA status and last password change (typically show "Not available" for a local, non-Entra-joined account — that's expected, and worth noting as a real limitation of local accounts vs. cloud identities)
   - Devices used by the account
   - Any unusual sign-in or account activity

### Task 5: Use Security Copilot prompts

1. On the incident page, look for a **Copilot** icon or pane (usually top-right of the Defender XDR portal). Select it to open the Copilot chat pane.

    > **Note:** Microsoft Security Copilot requires purchased Security Compute Units (SCUs), which are **not** included in this course's trial tenant by default. If no Copilot pane appears, or it shows a message that Copilot isn't provisioned/enabled, that's expected here — skip to step 3.

    ![Incident "..." menu showing Ask Defender Experts, Export incident as PDF, Merge incidents, and Report incident inaccuracy — no Copilot option, confirming Copilot isn't provisioned in this tenant.](./Media/sc200-l3-no-copilot-menu.png)

2. If Copilot is available, enter prompts similar to the following, then review each generated response and verify it matches the incident evidence you already gathered in Tasks 1–4:

   - Summarize this incident.
   - What devices and users are affected?
   - What was the likely initial access method?
   - Create a timeline of the incident.
   - What actions should the security analyst take next?

3. If Copilot is not available, answer each of the five prompts above yourself, using only the incident data you reviewed in Tasks 1–4 (Summary/Attack story tab, timeline, Assets tab). This demonstrates the same analysis Copilot would otherwise accelerate.

## Exercise 3: Analyze artifacts and perform an advanced investigation

### Task 1: Review an alert

1. On the incident page, select the **Alerts** tab (go through the incident, not the standalone *Alerts* item in the left navigation menu — that shows every alert in the tenant, not just this incident's).

    ![Incident Alerts tab listing the alerts generated by the attack simulation and the detection test.](./Media/sc200-l3-alerts-tab.png)

2. Select one of the alerts (avoid the `[Test Alert]` one if present — pick one from the real attack simulation, such as "Suspicious PowerShell command line").

3. Review the following information:

   - Alert title
   - Severity
   - Detection source
   - Affected device
   - Affected user
   - Process name
   - File name
   - IP address
   - Timestamp
   - Recommended actions

4. Record the alert details in your lab report.

    ![Alert detail page showing "What happened," Recommended actions, and the device/user affected.](./Media/sc200-l3-alert-detail.png)

### Task 2: Analyze a suspicious artifact

1. Go back to the incident page, select the **Evidence and response** tab, then select **IP addresses**.

    ![Evidence and response tab showing the IP addresses evidence list.](./Media/sc200-l3-evidence-ip-list.png)

2. Select a **public** IP address from the list (not `127.0.0.1`, which is from the quick detection test, and not a private `192.168.x.x` address) — this is the external address the simulated attack tried to contact, imitating a C2 server. Select **Open IP address page** to review it in full.

    ![IP address page showing IP summary, Incidents & Alerts, Prevalence, and Threat Intelligence Insights.](./Media/sc200-l3-ip-page.png)

3. Review the available evidence, including the **Organization (ISP)** and **Reputation** fields.

4. Determine:

   - Why the artifact was identified as suspicious (hint: it's usually the *behavior* around the IP — an unusual process contacting it — not the IP's own reputation, which may show as "Unknown")
   - Which device or user was affected
   - Whether the artifact appears malicious or benign
   - What additional investigation is required

5. Record your conclusion and supporting evidence.

### Task 3: Investigate process activity

1. Go back to the alert from Task 1, and select the **Process tree** tab. Select **Expand all**.

2. Review the process tree.

3. Identify the parent process and the suspicious child process.

4. Review the command-line arguments shown for the PowerShell process.

5. Look for unusual PowerShell, command prompt, script, or executable activity.

6. Record the suspicious process chain.

    ![Process tree showing the parent/child process chain, with Detection source and MITRE ATT&CK technique in the Alert details panel.](./Media/sc200-l3-process-tree.png)

    Example format for your notes:

    ```text
    Parent process:
    Child process:
    Command line:
    Reason the activity is suspicious:
    ```

### Task 4: Review device and user context

1. Go back to the incident's **Assets** tab, select **Devices**, then select the affected device to open its side panel, and select **Open device page** for the full view.

    ![Device side panel from the incident's Assets tab, with VM details and Open device page link.](./Media/sc200-l3-device-panel.png)

    ![Full device page showing Active alerts, Logged-on users, and Security assessments.](./Media/sc200-l3-device-fullpage.png)

2. Review recent alerts, logged-on users, and device risk.

3. Go back to the incident's **Assets** tab, select **Users**, then select the affected user to open its side panel.

    ![User side panel showing Protection, User threat (Open incidents, Active alerts), and Top UEBA anomalies.](./Media/sc200-l3-user-panel.png)

4. Review sign-in activity, related incidents, and associated devices.

5. Determine whether the incident appears limited to one device or involves multiple entities.

    > **Note:** In this trial tenant there's normally only one device (WIN1) and one user (Admin), so you should expect the incident to appear limited to a single device/user — that's a realistic scenario, just a small one. In a production tenant with more assets, the same review steps would scale to a wider set of entities.

### Task 5: Identify recommended response actions

> **Caution:** Do not actually execute containment actions (isolate device, disable account, etc.) against WIN1 or the Admin account in this task — WIN1 is the only virtual machine in your environment, and isolating it or disabling its account would cut off your own access. Treat this task as a planning/discussion exercise: identify what you *would* do and justify it, without performing the action in the portal.

Based on the available evidence, identify appropriate response actions.

Possible actions include:

- Isolate the affected device.
- Disable or reset the affected user account.
- Block a malicious IP address or URL.
- Quarantine or remove a malicious file.
- Run an antivirus scan.
- Collect an investigation package.
- Review additional devices for similar activity.
- Escalate the incident to a senior analyst.

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
