---
lab:
    title: 'Configure Microsoft Sentinel Data Collection and Automation in a Unified SecOPs'
    description: 'Connect Microsoft Entra ID and Azure Activity data into Sentinel, verify ingestion, and configure automation rule.'
    level: 300
    duration: 45
    islab: true
    primarytopics:
        - Microsoft Sentinel
        - Data connectors
        - Automation rules and playbooks
---

# Lab Setup

Use an Azure subscription and Microsoft Entra tenant that you are authorized to administer. This lab requires the **Security Administrator** role and a Microsoft Sentinel-enabled workspace. Use privileged roles only for the duration of the exercise and follow your organization's least-privilege practices.

===

# Configure Microsoft Sentinel Data Collection and Automation

Your SOC cannot automate triage if data sources are disconnected and workflow actions are missing. In this lab, you will connect high-value Microsoft data sources, verify ingestion in the workspace, and configure an automation rule that drives a pre-built playbook.

In this lab, you will:

- Review the pre-provisioned Sentinel workspace state.
- Connect the Microsoft Entra ID connector.
- Connect the Azure Activity connector.
- Verify event ingestion with a Log Analytics query.
- Build an automation rule for high-severity incidents.
- Link the rule to an alert.

This exercise should take approximately **45** minutes to complete.

> **Note**: This lab uses the workspace created at the start of the course.

---

## Review the Workspace for use in Microsoft Sentinel

1. Open a browser and connect to **HTTPS://security.microsoft.com**, if necessary login as your **Admin** account.

1. Select **Show Navigation** then expand **Setup & Configuration** and then click **Settings**.

1. In Settings click **Microsoft Sentinel** and confirm that your workspace is connected.

1. In the Navigation pane, expand **Microsoft Sentinel**, expand **Content Management** and then click **Content Hub**.

---

## Connect Microsoft Entra ID

1. In **Content Hub** search for **Microsoft Entra ID**, tick the check box and click **Install**.

1. Wait for it to install then click **Manage** Select the Microsoft Entra ID Connector and then click **open the connector Page**.

1. Under Configuration select the tick boxes for **Sign-in Logs** & **Audit Logs** and then **Apply Changes**.

1. Open another browser window in-private/incognito and connect to **Https://portal.azure.com**.

1. Attemp to log-in as **USER2** twice but use an incorrect password to generate failed logins.

1. Return to your **Admin** browser.

---

## Connect Azure Activity

1. In **Content Hub**, search for **Azure Activity**.

1. Repeat the previous steps to Install the solution and Manage the connector to open the connector page.

1. In the Connector details page click **Launch Azure Policy Assignment Wizard**.

1. In the Assign Policy window, click the **...** next to Scope and select your subscription then click **Select** and **Next**.

1. On the Parameters tab click the **...** and select your workspace, click **Select** then **Next**.

1. On the Remediation tab, check the **Create a remediation task** box and then **Review + create** and then **Create**.

---

## Verify Ingestion

1. In the Navigation menu expand Hunting and then click Advanced Hunting.

1. Run the following query:

    ```kusto
    EntraIdSignInEvents
| where ErrorCode == 50126
    ```

1. You should see 2 rows returned, expand the rows to examine the details.

---

## Configure Detection Rule and Automation rule

1. In Advanced Hunting, click **Create Detection Rule** then:

    - Detection name: `sc500-auto-triage`
    - Severity: High
    - Mitre Attack: Discovery

1. Click **Next**, Alert Details:

    - Alert Title : My Alert
    - Description : My Alert
    - Click **Next** twice.

1. On Automated Actions expand **Users** and tick **Mark user as compromised** then click Next and **Submit**.

1. Open another browser window in-private/incognito and connect to **Https://portal.azure.com**.

1. Attemp to log-in as **USER2** twice but use an incorrect password to generate failed logins.

1. Open a browser and connect to **Https://Entra.microsoft.com** and login as **Admin**

1. Expand **Identity Protection** and click **Risky Users** and confirm the User2 is **Confirmed compromised**

1. Return to **Microsoft Defender** Portal and confirm **Alert** generation.

---

## Summary

In this lab, you established Sentinel collection and orchestration fundamentals:

- Connected core Microsoft security telemetry sources.
- Verified that events are ingesting into the workspace.
- Configured incident automation to standardize triage actions.

This creates the base operating pattern for SOC data readiness and repeatable incident response automation.
