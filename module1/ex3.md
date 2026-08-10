# Lab 02 - Exercise 3: Manage a Microsoft 365 Apps for enterprise installation

> **!IMPORTANT**: `Once you launch the track, you’ll have access to a virtual machine (VM) for 40 hours. The displayed track duration of 30 days indicates the time frame during which you can use your VM. Please plan your lab sessions accordingly. If the VM uptime of 40 hours is fully exhausted before completing the labs, access will be lost. To avoid this and for detailed instructions on VM usage and stopping/deallocating the VM, refer to the Getting Started page.`

> `If the full 40 hours of VM uptime is exhausted, the VM will no longer be accessible, and the lab duration cannot be extended.`

## Lab scenario

You have taken on the persona of Holly Dickson, Adatum's new Microsoft 365 Administrator, and you have Microsoft 365 deployed in a virtualized lab environment. In this exercise, you will perform the tasks necessary to manage a user-driven Microsoft 365 Apps for enterprise installation. Performing a user-driven Microsoft 365 Apps for enterprise installation is a two-step process:

- Configuring the user account so the user is eligible to download and install the Office 365 deployment tool.
- Performing the installation.

In the first two tasks in this exercise, you will verify the following conditions that affect whether a user can be blocked from downloading the Microsoft 365 Apps for enterprise suite:

- Whether the user has an appropriate Microsoft 365 license (which you will verify in Task 1).
- Whether an admin has turned off the global Office download setting that controls the downloading of mobile and desktop apps for all users (which you will verify in Task 2).

In the final task in this exercise, you will install the Microsoft 365 Apps for enterprise suite for one of Adatum's users.

### Task 1 – Verify how licensing affects installing Microsoft 365 Apps for enterprise

In this task, you will review how user licensing impacts the ability to install Microsoft 365 Apps for enterprise and verify that the correct licenses are assigned.

1. On **LON-CL1**, you should be logged into Microsoft 365 as **Holly Dickson** in your Edge browser.

1. In the **Microsoft 365 admin center**, in the navigation pane, select **Users (1)** and then select **Active users (2)**.

1. You will begin by testing whether a user **without** an appropriate Microsoft 365 license can install Microsoft 365 Apps for enterprise. For this test, you will use **Laura Atkins**. Your lab hosting provider has already created an on-premises user account for Laura, but she does not have a Microsoft 365 user account. You will create a Microsoft 365 account for Laura, but you will NOT assign her a Microsoft 365 license.

1. At the top of the **Active users** window, select **Add a user (3)** on the menu bar. Doing so initiates the **Add a user** wizard.

   ![](../Images/p5t1p1-july26.png)

1. In the **Add a user** wizard, in the **Set up the basics** window, enter the following information:
   - First name: **Laura (1)**
   - Last name: **Atkins (2)**
   - Display name: When you tab into this field, **Laura Atkins (3)** will appear
   - Username: **Laura (4)**
   - Password settings: Clear (uncheck) the **Automatic create a password (5)** option
   - Password: Enter the enter Password:- <inject key="AzureAdUserPassword"></inject> (6).
   - Clear (uncheck) the **Require this user to change their password when they first sign in (7)** check box
   - Select **Next (8)**.

     ![](../Images/ms102-p6t1p2.png)

1. In the **Assign product licenses** window, select the **Create user without product license (not recommended) (1)** option, and then select **Next (2)**.

   ![](../Images/ms102-p6t1p3.png)

1. In the **Optional settings** window, select **Next**.

1. On the **Review and finish** window, review your selections. If anything needs to be changed, select the appropriate **Edit** link and make the necessary changes. Otherwise, if everything looks good, select **Finish adding**.

   ![](../Images/L2E3T1S7-2904.png)

1. On the **Laura Atkins added to active users** page, select **Close**. If a survey form appears, select **Cancel**.

   ![](../Images/ms102-p6t1p4.png)

1. Open **Hyper-V Manager** page, Right click on the **LON-CL2** VM, click on **Connect**, and on the **Connect to LON-CL2** pop-up select **Connect**.

   > **Note:** if required maximize the **LON-CL2** VM.

   > **Note:** You can also access the **LON-CL2** virtual machine directly from the desktop of the **LON-CL1** host virtual machine.

1. In **LON-CL2**, on the log-in screen, you will log in as the local **Admin** account with a password of **Pa55w.rd**.

   > **Note:** If a **Networks** window appears, select **Yes**.

1. In the **Type here to search**, search and select **Computer Management**.

1. Under **Computer Management (Local) (1)**, select **Local users and groups (2)** > **Groups (3)** > Open **Remote Desktop Users (4)** group.

   ![](../Images/ms102-p6t1p5.png)

1. Click on **Add(1)** and in **Enter the object names to select**, type **Laura (2)** and click on **Ok (3)**.

   > **Note:** `If you receive an error indicating that Laura cannot be found, or if the From this location field shows LON-CL2 instead of Adatum.com, open Hyper-V Manager and verify that LON-DC1 is running. If it is stopped, start LON-DC1, wait for it to finish booting, and then repeat this step.`

   ![](../Images/note-1.png)

   ![](../Images/ms102-p6t1p6.png)

1. On the **Name Not Found** window, click on **OK**.

1. It will pop up a dialog box to enter **Network Credentials** of Laura, please enter **Username** as **adatum\laura** and **password** as **Pa55w.rd**. Select **OK**.

   ![](../Images/L2E3T1S13.2-2904.png)

1. Select **Apply (1)** and **OK (2)**.

   ![](../Images/ms102-p6t1p7.png)

1. Now restart the **LON-CL2 VM** and attempt to sign in again using the Laura account. On the sign-in screen, select **Other user (1)**, enter **adatum\laura (2)** as the username and **Pa55w.rd (3)** as the password, then press **Enter** to log in.

   ![](../Images/ms102-p6t1p8.png)

1. Minimize **LON-CL2**. On **LON-CL1**, use the search bar to open **Hyper-V Manager (1)**, and then select it from the search results **(2)**.

   ![](../Images/ms102-p6t1p9.png)

1. Right click on **LON-CL2 (1)**, and select **Turn-off (2)** option, it will turn-off your VM, as you can see the state of the **LON-CL2** VM is showing as **Off**.

   ![](../Images/ms102-p6t1p10.png)

1. Now, right click on the **LON-CL2** VM, select **Start** button, and see the VM is now in running state. Again right click on the Client-2 VM (LON-CL2) and select **Connect**, and select **Connect**.

   > **Note:** if the **Connect to LON-CL2** pop-up appears select **Connect**.

1. On **LON-CL2**, you want to log into the machine as **Laura Atkins**. the desktop displays the **Admin** and **Other user** options. Select **Other user**. Since you want to log on to the LON-CL2 machine using Laura Atkins's local account (adatum\laura).

1. In the **Other user (1)** log in, enter **adatum\laura (2)** in the **Username** field, enter **Pa55w.rd (3)** as the **Password**, and then select the forward arrow to log in.

   ![](../Images/ms102-p6t1p8.png)

1. Select the **Microsoft Edge** icon on the taskbar.

1. In **Microsoft Edge**, maximize your browser if necessary. If you receive a **Welcome to Microsoft Edge** window that displays a message indicating **Let's start by signing you in and bringing over your passwords, history, and more**, perform the following steps to initialize your Edge browser and navigate to the Microsoft 365 Home page:
   - On the first screen, select the **Start without your data** button.
   - On the second screen, select the **Continue without this data** button.
   - On the third screen, unselect (clear) the **Make your Microsoft experience more useful to you** check box and then select the **Confirm and start browsing** button.
   - In the Edge browser, go to the **Microsoft 365 Home** page by entering the following URL in the address bar: **https://portal.office.com/**

1. In the **Sign in** window, enter **Laura@otuwamocZZZZZZ.onmicrosoft.com** (where ZZZZZZ is the tenant prefix provided by your lab hosting provider), and then select **Next**.

   > **Note:** For example, in **odl*user*<inject key="DeploymentID" enableCopy="false"/>@otuwamocZZZZZZ.onmicrosoft.com**, the highlighted portion (**otuwamocZZZZZZ.onmicrosoft.com**) represents the domain name or tenant prefix, which you can replace with your desired tenant prefix.

1. In the **Enter password** window, enter **<inject key="AzureAdUserPassword"></inject>** and then select **Sign in.**

   > **Note**: if it asks you to change the password, then change the password for the laura's account.

1. In the **Stay signed in?** window, select **Yes**.

    > **Note:** If the **Let's keep your account secure** screen appears instead, follow the prompts to set up **Microsoft Authenticator** and complete the MFA setup. For detailed steps, refer to the **[Steps to Proceed with MFA Setup if "Ask Later" Option is Not Visible](#steps-to-proceed-with-mfa-setup-if-ask-later-option-is-not-visible)** section on **Page 1**.

   > **Note:** If the **Let's keep your account secure** screen appears instead, follow the prompts to set up **Microsoft Authenticator** and complete the MFA setup. For detailed steps, refer to the **[Steps to Proceed with MFA Setup if "Ask Later" Option is Not Visible](started.md#steps-to-proceed-with-mfa-setup-if-ask-later-option-is-not-visible)** section on **Page 1**.

1. In the **All your work in one place, now easier with AI.** dialog box that appears in the middle of the screen, close it by clicking on **X**.

1. On the **Microsoft 365 Copilot** page, select the **App launcher (1)** in the upper-left corner, and then select **More apps (2)** (Laura’s Microsoft 365 landing page), observe that the usual list of Microsoft 365 app icons does not appear in the left navigation pane. This indicates that a Microsoft 365 license has not yet been assigned to Laura’s account.

   ![](../Images/p5t1p3-july26.png)

1. From the right top corner, select the **Install apps (1)** button, and then in the drop-down menu that appears, select **Microsoft 365 apps (2)**. This opens the **My account** window for Laura.

   ![](../Images/p5t1p4-july26.png)

1. In Laura's **My account** window, under the **Office apps & devices** tile, select **View apps & devices**. Note the message that appears at the top of page. Laura has not been assigned a license that includes the Office desktop apps, so she’s unable to install Microsoft 365 Apps for enterprise.

   ![](../Images/p5t1p5-july26.png)

   ![](../Images/appsdevice.png)

   > **Important:** You have just verified that a user can't download Microsoft 365 Apps for enterprise if they haven't been assigned an appropriate Microsoft 365 license.

1. Leave LON-CL2 open and remain signed into Microsoft 365 as Laura Atkins for the next task. In your Edge browser, close the **My account** tab and the **Welcome to Microsoft Edge** tab, but leave the **Microsoft 365 Copilot** tab open for the next task.

### Task 2 – Verify how the global Office download setting affects installing Microsoft 365 Apps for enterprise

In this task, you will check how the global Office download settings within the Microsoft 365 admin center influence the installation process for Microsoft 365 Apps for enterprise.

> **Note:** Microsoft 365 includes a global Office download setting that controls the downloading of mobile and desktop apps for all users. Holly is now going to test whether users can be prohibited from downloading Microsoft 365 Apps for enterprise if an admin turns off this setting. In this test, Holly will once again use Laura Atkins as her test case. However, since you just proved in the prior task that Laura can't install Microsoft 365 Apps for enterprise without a proper license, you must first assign her a license.

1. Switch back to **LON-CL1**. Open the Edge browser.

1. On **LON-CL1**, Holly wants to turn off the global Office download setting. To do so, select the **Microsoft 365 admin center** tab in your browser, and then if necessary, select **...Show all** in the navigation pane. Select **Settings (1)**, and then within the Settings group, select **Org Settings (2)**.

   ![](../Images/ms102-p6t2p1.png)

1. In the **Org settings** window, the **Services (1)** tab is displayed by default. Scroll down through the list of services and select **Microsoft 365 installation options (2)**.

   ![](../Images/ms102-p6t2p2.png)

1. In the **Microsoft 365 installation options** pane that appears, the **Feature Updates** tab is displayed by default. Select the **Installation (1)** tab that appears next to it. Then under the **Apps for Windows and mobile devices** section, the **Office (includes Skype for Business) (2)** check box is currently selected. Select this check box to clear it. This disables the ability of users to download Office apps through Microsoft 365 Apps for enterprise.

1. Select **Save (3)**.

   ![](../Images/ms102-p6t2p3.png)

1. At the top of the **Microsoft 365 app installation options** pane, select the **X** in the upper-right corner of this window to close it.

1. In the **Active users (1)** list, scroll down to **Laura Atkins**. The value in the **Licenses (2)** column for Laura currently indicates that she is **Unlicensed**. Select **Laura Atkins (3)**.

   ![](../Images/ms102-p6t2p4.png)

1. In **Laura Atkins** account pane, select the **Licenses and apps (1)** tab. In the **Licenses** section, select the **Microsoft 365 Business Premium (2)** check boxes and then select **Save changes (3)**. Once the changes are saved, close Laura’s account pane. In the **Active users** list, note how the value in the **Licenses** column for Laura now displays **Microsoft 365 Business Premium**.

   ![](../Images/ms102-p6t2p5.png)

1. You should now check whether Laura can download Microsoft 365 Apps for enterprise to her client PC when the global Office download setting has been turned Off.

   > **Note:** To do this, you must first switch back to **LON-CL2**, navigate back to the hyper-v manager, right click on the **LON-CL2** VM and select **Connect**.

1. In **LON-CL2**, your Edge browser should still be open, and you should still be logged into Microsoft 365 as Laura Atkins (verify Laura's **LA** initials appear in the below-left corner of the browser; note that Laura's name doesn't appear because she's not a member of the M365 copilot project group that was assigned to the custom theme).

1. In your browser, verify you're on the **Apps | Microsoft 365** tab. When you left off after the prior lab task, this page didn't display any Microsoft 365 apps in the navigation pane on the left because Laura wasn't assigned a Microsoft 365 license. Let's see what happens now that Laura has been assigned a license.

1. Click the **Refresh** icon next to the browser’s address bar to reload the page. After refreshing, notice that the Microsoft 365 applications are now displayed on the **Apps** page (such as Outlook, Word, Excel, etc.). Previously, no apps were visible because Laura had not yet been assigned a Microsoft 365 license.

   ![](../Images/p5t1p6-july26.png)

   > **Note:** If a **Find more apps** window appears, select the **X** to close it.

1. Select the **Install apps (1)** button, and then in the drop-down menu, select **Microsoft 365 apps (2)**.

   ![](../Images/p5t1p7-july26.png)

1. This will open Laura's **My account** window. Under the **Office apps & devices** tile, select **View apps & devices**.

1. In the **Apps & devices** window, a message is displayed under the **Office** section that indicates the admin has turned off Office installs.

   > **Important:** You have just verified that a licensed user is unable to download Microsoft 365 Apps for enterprise if the global Office download setting has been turned Off.

   ![](../Images/officeppas.png)

1. At this point Holly wants to turn the global Office download setting back On so that Laura can download Microsoft 365 Apps for enterprise.

   > **Note:** To do this, switch back to **LON-CL1**.

1. On **LON-CL1**, you should still be logged into Microsoft 365 as Holly Dickson. In the **Microsoft 365 admin center**, under the **Settings (1)** section in the navigation pane, select **Org Settings (2)**.

1. In the **Org settings** window, the **Services** tab is displayed by default. Scroll down through the list of services and select **Microsoft 365 installation options (3)**.

1. In the **Microsoft 365 installation options** pane, select the **Installation (4)** tab, then under the **Apps for Windows and mobile devices** section, the **Office (includes Skype for Business) (5)** check box is currently blank. Select this check box so that it displays a check mark, which now turns this feature back On.

1. Select **Save (6)**, and then once the update has been saved, select the **X** in the upper-right corner of this window to close it.

   ![](../Images/ms102-p6t2p8.png)

1. Now that this global Office download option is turned back On, you should see if it affects Laura’s ability to download Microsoft 365 Apps for enterprise.

   > **Note:** To do this, switch back to **LON-CL2**.

1. In **LON-CL2**, your Edge browser should still be open, and you should still be logged into Microsoft 365 as Laura Atkins. The **Office apps and devices** page should be displayed along with the message that indicated your admin has turned off Office installs. Since you just turned this global option back On, you need to refresh this page to see how it affects Laura’s ability to download Microsoft 365 Apps for enterprise. Select the **Refresh** icon that appears to the left of the address bar at the top of your browser.

1. In the **My account** window that appears, under the **Office apps & devices** tile, an **Install Office** button appears along with a message indicating you can install Office on up to 5 PCs or Macs, 5 tablets, and 5 smartphones.

   ![](../Images/ms102-p6t3p3.png)

   > **Important:** You have just verified that a user with a Microsoft 365 license is able to download Microsoft 365 Apps for enterprise if the global Office download setting is turned On. Do **NOT** select the **Install Office** button at this time.

   > **Note:** It may take several minutes for the **Install Office** option and device installation message to appear after enabling the global Office download setting or assigning the license. If the option is not visible, wait a few minutes and refresh the page. You may proceed with the next exercise in the meantime and return later to verify that the option is available.

1. Remain on **LON-CL2**.

### Task 3 – Perform a User-Driven Installation of Microsoft 365 Apps for enterprise

In this task, you will complete a manual, user-initiated installation of Microsoft 365 Apps for enterprise and confirm successful deployment on a device.

> **Note:** In the prior task, you logged into Laura Atkins client PC, and you verified that she could download Microsoft 365 Apps for enterprise once she was assigned a Microsoft 365 license and the global Office download setting was turned On. In this task, you will continue the process by having Laura perform a user-driven installation of the Microsoft 365 Apps for enterprise suite from the Microsoft 365 portal.

1. On **LON-CL2**, your Edge browser should be open, and you should be logged into Microsoft 365 as Laura Atkins.

1. You should still be in Laura’s **My account** window since this is where you left off at the end of the prior task. Under the **Office apps & devices** section, the **Install Office** button now appears since Laura is assigned a Microsoft 365 Business Premium license and the global Office download setting is turned On.

   > **Important:** Selecting this **Install Office** button will install the 64-bit, English version of Microsoft 365 Apps for enterprise. However, if you want to install a different language or version, then select **View apps & devices**, which opens the **Apps & devices** page; this enables you to select a different language and version of Microsoft 365 Apps for enterprise to install.

   > **Note:** If a **Just a few more steps** window appears, select **Close**.

1. No need to install the office, you already have the Office installed in the **LON-CL2** VM.

1. In the **Start** menu, type and select **Word**.

1. On the **Sign in to get started with Word** pop-up select **Sign in or create account**.

   ![](../Images/ms102-p6t3p1.png)

1. Enter **Laura@otuwamocZZZZZZ.onmicrosoft.com** (where ZZZZZZ is the tenant prefix provided by your lab hosting provider), and then select **Next**.

1. In the **Enter password** window, For the password, sign-in with the same **Microsoft 365 Tenant Password**.
   - Password:- <inject key="AzureAdUserPassword"></inject> and then select **Sign in.**

     > **Note:** For example, in **odl*user*<inject key="DeploymentID" enableCopy="false"/>@otuwamocZZZZZZ.onmicrosoft.com**, the highlighted portion (**otuwamocZZZZZZ.onmicrosoft.com**) represents the domain name or tenant prefix, which you can replace with your desired tenant prefix.

1. On the Account asking pop-up, select **No, this app only**.

   ![](../Images/ms102-p6t3p2.png)

   > **Note:** On **Your privacy matters** pop-up select **Close**.

1. Verify that Word is functioning properly by opening a blank Word document, entering some text, and saving the document to the **Documents** folder.

1. Close Word.

1. Now that you have completed this lab exercise, you should log out of Microsoft 365 as Laura Atkins by navigating back to the Edge browser. Select Laura's icon in the upper-right corner of the screen (the circle with LA in it), and then in Laura's property window, select **Sign out**.

1. Once Laura is signed out, close your Microsoft Edge browser.

1. You now want to log out of LON-CL2 as Laura Atkins and log back in as the Adatum administrator. This will prepare LON-CL2 for the next lab that uses this PC.

1. Minimize **LON-CL2**. Inside **LON-CL1** VM.

1. Switch back to the Hyper-V Manager, on LON-CL2, right click on the **LON-CL2** VM and turn-off the VM, after the status shows Off, right click again and start the VM. Right click on the **LON-CL2** VM click on **Connect**.

1. On the desktop, the **Laura Atkins** is selected by default. select **Other user**, enter **lon-cl2\admin** in the username filed and **Pa55w.rd** in the **Password** field and then select the forward arrow. The desktop should now display the logged-on user as **lon-cl2\admin**. LON-CL2 is now ready for the next lab that uses it.

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
>
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="7d9fdfc3-5392-4896-ab0f-7b5f3a8a3b09" />

## Review

In this lab, you have:

- Verified how licensing affects installing Microsoft 365 Apps for enterprise.
- Verified how the global Office download setting affects installing Microsoft 365 Apps for enterprise.
- Performed a User-Driven Installation of Microsoft 365 Apps for enterprise

## The lab has been completed successfully. Click **Next >>** to proceed to the next exercise.

![](../Images/ms-102-g-next.png)
