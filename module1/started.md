# Getting Started with Your MS-102 : MICROSOFT 365 ADMINISTRATOR AND ESSENTIALS Workshop
 
Welcome to your MS-102 : MICROSOFT 365 ADMINISTRATOR AND ESSENTIALS workshop! We've prepared a seamless environment for you to explore and learn about key elements of Microsoft 365 administration: Microsoft 365 tenant management, Microsoft 365 identity synchronization, and Microsoft 365 security and compliance. Let's begin by making the most of this experience:

> **!IMPORTANT**: `Once you launch the track, you’ll have access to a virtual machine (VM) for 40 hours. The displayed track duration of 30 days indicates the time frame during which you can use your VM. Please plan your lab sessions accordingly. If the VM uptime of 40 hours is fully exhausted before completing the labs, access will be lost. To avoid this and for detailed instructions on VM usage and stopping/deallocating the VM,` refer to the [Managing Your Virtual Machine](#managing-your-virtual-machine) section for step-by-step instructions.

> `If the full 40 hours of VM uptime is exhausted, the VM will no longer be accessible, and the lab duration cannot be extended.`

 
## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and **Guide** will be right at your fingertips within your web browser.
 
![Enter Your Password](../Images/ms-102-g1.png) 

### Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.
 
![Explore Lab Resources](../Images/ms102july26-envtab.png)

## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
![Use the Split Window Feature](../Images/ms102july26-splittab.png)
 
## Managing Your Virtual Machine
 
1. Feel free to **Start, Stop, or Restart** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!

    - Once you finish using the lab for the day, please **stop or deallocate** the VM from the Resources tab as shown in the image below.

    - **Label (2)** indicates your **maximum uptime limit** and **remaining uptime**.

    - **Label (3)** indicates **Starting the VM**, and **label (4)** indicates **stopping or deallocating** it. All VMs can be stopped and start from resources tab. Stopping or deallocating the VMs helps preserve the VM uptime limit so you can continue working the next day without exhausting the available uptime.

    - **Label (5)** and **Label (6)** indicates child VMs control to stop and start.

        ![](../Images/image%20(5).png)

    - Please note that once the lab is launched, the overall lab session cannot be paused and will continue to run until the allotted time is fully consumed. Only the VM itself can be stopped or deallocated as described above.
 
      ![Manage Your Virtual Machine](../Images/ms-102-vm-manage.png)



2. **NOTE:** If any virtual machine remains idle for approximately **30 minutes**, a **warning pop-up window** will appear (as shown in below image) indicating that the machine will shut down in **10 minutes** unless the warning is *cancelled*.

    ![](../Images/idleness-tracking-warning.png)

2. To initiate the required VMs, use the dropdown menu located at the top of the lab environment

    ![Manage Your Virtual Machine](../Images/ms-102-g4.png)

    > **NOTE:** If the drop-down to switch between virtual machines is not visible, connect to the **LON-CL1 VM**, and then select the required virtual machine from there to log in.
    >
    > ![](../Images/2026-04-17_23-31-58.png)
 
3. When logging into the Hyper-V virtual machines, if a message appears stating **"Press Ctrl+Alt+Delete to unlock"**, navigate to the **Actions** menu in the Virtual Machine Connection window and select the **Ctrl+Alt+Delete** option, as shown in the image below.

    ![Manage Your Virtual Machine](../Images/ms-102-29.png)

4. If you face an issue while copying the content from the lab guide and pasting it into the Hyper-V virtual machines, navigate to the **Clipboard** option in the Virtual Machine Connection window and select **Type Clipboard Text**.

    ![Manage Your Virtual Machine](../Images/ms-102-30.png)  

## Lab Guide Zoom In/Zoom Out
 
To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

   ![](../Images/ms-102-g6.png)

## Pasting Commands in the PowerShell/CloudShell Environment

Please make sure to use the **CTRL+SHIFT+V** or **CTRL+V** keys when pasting commands inside the PowerShell/CloudShell environment instead of right-clicking

## Let's Get Started with Azure Portal
 
1. On your virtual machine, click on the Azure Portal icon as shown below:
 
    ![Launch Azure Portal](../Images/ms-102-5.png)

2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
        ![Enter Your Username](../Images/ms-102-g7.png)
 
3. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
        ![Enter Your Password](../Images/ms-102-g8.png)

4. If prompted to **Stay signed in**, you can click **No.**
 
     ![](../Images/ms-102-g9.png)

5. If a **Welcome to Microsoft Azure** pop-up window appears, simply click "Maybe Later" to skip the tour.

6. If you want a list of users and their email IDs, you can select the **Environment** page and scroll down to view the users list. 

    >**Note:** You can also check the users on the **Microsoft Entra ID** portal. Follow the below steps:

    - In the **Search resources, services and docs** search and select **Microsoft Entra ID**.

    - From the left-hand navigation pane select **Users**, it will display all the users list.

    - Keep this tab open for your entire lab.

## Steps to Proceed with MFA Setup if "Ask Later" Option is Not Visible

1. On the **Let's Keep your account secure** page, select **Next** twice.

     ![](../Images/ms-102-g11.png)

1. On the **Set up your account in app** screen, select **Next** to continue.

    ![](../Images/ms-102-g12.png)

1. **Note:** If you don’t have the Microsoft Authenticator app installed on your mobile device:

   - Open **Google Play Store** (Android) or **App Store** (iOS).
   - Search for **Microsoft Authenticator** and tap **Install**.
   - Open the **Microsoft Authenticator** app, select **Add account**, then choose **Work or school account**.

     ![](../Images/ms-102-g13.png)

1. A **QR code** will be displayed on your computer screen.

1. In the Authenticator app, select **Scan a QR code** and scan the code displayed on your screen.

     ![](../Images/ms-102-g14.png)

1. After scanning, click **Next** to proceed.

1. On your phone, enter the number shown on your computer screen in the Authenticator app and select **Next**.
       
    ![](../Images/ms-102-g15.png)

1. Click on **Done**.

1. If prompted to stay signed in, you can click "No."
 
1. If a **Welcome to Microsoft Azure** pop-up window appears, simply click "Maybe Later" to skip the tour.

## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:
- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

- Now, click on **Next** from the lower right corner to move on to the next page.

    ![](../Images/ms-102-g-next.png)
 
Now you're all set to explore the powerful world of technology. Feel free to reach out if you have any questions along the way. Enjoy your workshop!
