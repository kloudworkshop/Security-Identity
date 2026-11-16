---
lab:
    title: 'Pre Requisite Setup'
    description: 'Pre Requisite Setup.'
    level: 300
    duration: 30
    islab: true
    primarytopics:
        - Pre Requisite Setup for course
---

# Lab Setup

===

## Pre Requisite Setup

As the course covers technologies that can take between 12 to 24 hours to generate any results or be available
to configure we are going to complete the steps now to minimise wait time later.


---

## Enable Defender For Cloud

1. Login to https://portal.azure.com using the admin account provided by your Instructor.
   
  >**Note**: If necessary complete Multi Factor Authentication Registration.

1. On the Azure portal home page, type Defender in the top search bar and select Defender for Cloud.
   
1. In the Defender for Cloud portal, expand Management and then click Environment Settings.
   
1. At the bottom of the main pane expand Tenant Root Group and then select your Subscription.
   
  > **Note**: If Subscription reports as Unregistered, wait 1 min & refresh page).

1. At the top of the page select Enable All Plans.
   
1. In the Plan Selection popout, select Microsoft Defender for APIs Plan 1 anc click Save.
   
1. Confirm that all plans report a status of ON and click the top Save button.
   
1. After approx 2 mins you should get notifications of success.
   
1. Return to the Home page.

## Enable Microsoft Sentinel

1. On the Azure portal home page, type Sentinel in the top search bar and select Microsoft Sentinel.

1. Click +Create, and then +Create a new workspace.

1. Create a new Resource Group called SC500MS and in the name box type MySentinel.

1. Click Review & Create and after validation click Create.

1. Once the deployment is complete type Sentinel in the top search bar and select Microsoft Sentinel.

1. Click +Create, and then select MySentinel and click add.

1. Wait for 1 min for Sentinel to deploy.

1.  Open a new browser tab and type https://security.microsoft.com

1. In the Microsoft Defender Portal, click Show Navigation, expand Setup & Configuration and click Settings.

1. Wait until Settings appear.

1. Select Microsoft Sentinel, and in the WorkSpaces page, confirm MySentinel is connected, if not connect the workspace.

## Manage Entra ID

1. Open another browser tab and type https://entra.microsoft.com.

1. Select Overview under Entra ID and then click the Properties tab.

1. Scroll to the bottom of the page and click the Manage Security Defaults link.

1. In the pop out select Disabled under Security Defaults and then select My Organisation is planning to use Conditional Access
and then Save, then Disable and wait for the confirmation.

1 Open another browser tab and type https://admin.microsoft.com

1. In the Microsoft 365 Admin Center expand Users and click Active Users.

1. Select the Tick box next to your Admin account and click Manage Product Licenses.

1. Tick the box next to Microsoft Entra ID P2 and click Save changes, then click the X to close the user page.

1. Click Add a User.

1. For First Name, Display Name & Username type USER1.

1. Remove the Automatically create a password & Require this user to change their password ticks.

1. Use the same password as your admin account in the password box click next.

1. Select Create User without product license, click nect twice and then click Finish Adding, then close.

1. Create 2 more user accounts, USER2 & USER3, same password, no license.

## DEFENDER CSPM LAB

1. To best experience the Explore Defender for Cloud Security Posture and CSPM lab, the setup needs to be run at least 24 hours before attempting the lab.

1. Consider runnung the lab setup exercise either as the last activity of day 2 or first thing day 3.

1. Ensure that the sc500-lab4d-rg Resource Group is not deleted until completing the lab.
