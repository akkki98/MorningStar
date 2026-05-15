# Lab — Investment Report Approval System

**Agent:** Morningstar Learning Bot
**Tool:** Microsoft Copilot Studio
**Estimated Time:** 30 minutes

---

## What You Will Build

A simple approval flow where an employee requests a Morningstar investment report, the manager (you) receives an approval request in Outlook, and the employee gets a confirmation email after approval.

```
Employee submits request
        ↓
Agent collects details
        ↓
Approval sent to manager (Outlook + Teams)
        ↓
Manager clicks Approve
        ↓
Employee receives confirmation email ✅
```

---

## Pre-requisites

- Labs 1–8 completed (Morningstar Learning Bot already created)
- Microsoft 365 account with Outlook access
- Copilot Studio license

---

## Part 1 — Create the Topic

### Step 1 — Add a new topic

1. Go to **Topics → Add a Topic → From Blank**
2. Name it: `Investment Report Approval`

### Step 2 — Add trigger phrases

Click the **Trigger** node and add:

```
I want to request a report
Submit approval request
Request investment analysis
I need a report approved
Get report approved
```

### Step 3 — Add a welcome message

Click **+** → **Send a message**:

```
📋 Let me collect your request details.
```

### Step 4 — Add 4 question nodes

Add an **Ask a Question** node for each, saving to the variable shown:

| Question | Save as |
|---|---|
| What is your full name? | `VarRequesterName` |
| What is your email address? | `VarRequesterEmail` |
| What type of report are you requesting? | `VarReportType` |
| Why do you need this report? | `VarReason` |

> **How to set the variable:** In each question node, scroll to **"Save response as"** and type the variable name exactly as shown above.

### Step 5 — Add confirmation message

Click **+** → **Send a message** and insert each variable using the **{x} button** in the toolbar (do not type variable names as plain text):

```
Got it! Here's your request summary:

👤 Name:   [insert VarRequesterName via {x}]
📧 Email:  [insert VarRequesterEmail via {x}]
📄 Report: [insert VarReportType via {x}]
📝 Reason: [insert VarReason via {x}]

Submitting your request for manager approval...
```

> ⚠️ Each variable must appear as a **blue pill chip**. If you see red errors like `"Identifier not recognized"`, delete the chip and re-insert using the **{x}** button.

---

## Part 2 — Create the Agent Flow

### Step 1 — Open Workflows

Go to **Workflows → New agent flow**

Name it: `Investment Report Approval Flow`

### Step 2 — Configure the trigger inputs

On the **"When an agent calls the flow"** trigger, add 4 inputs:

| Type to click | Name it |
|---|---|
| Text | `RequesterName` |
| Email | `RequesterEmail` |
| Text | `ReportType` |
| Text | `Reason` |

### Step 3 — Add approval action

Click **+** below the trigger → search **"Start and wait for an approval"**

Configure:

| Field | Value |
|---|---|
| **Approval type** | Approve/Reject - First to respond |
| **Title** | `Report Request from` + ⚡`RequesterName` |
| **Assigned to** | Your own email address (hardcode it) |
| **Details** | Add each field using ⚡ dynamic content: RequesterName, RequesterEmail, ReportType, Reason |

> **Assigned to** is where you put **your email** so you receive the approval request.

### Step 4 — Add email action

Click **+** below the approval → search **"Send an email (V2)"** → select **Office 365 Outlook**

Configure using ⚡ dynamic content for each field:

| Field | Value |
|---|---|
| **To** | ⚡ `RequesterEmail` |
| **Subject** | `✅ Your Morningstar Report Request is Approved` |
| **Body** | `Hi` ⚡`RequesterName`, `your request for` ⚡`ReportType` `has been approved. Our team will get back to you shortly.` |

> ⚠️ Always use the **⚡ lightning bolt / dynamic content picker** to insert variable values. Never type `{RequesterName}` as plain text — it will appear literally in the email.

### Step 5 — Delete the "Respond to the agent" node

Click **...** on the last node → **Delete**

Not needed for this simple flow.

### Step 6 — Save and Publish

Click **Save** → then **Publish**

---

## Part 3 — Wire the Flow to the Topic

### Step 1 — Go back to your topic

**Topics → Investment Report Approval**

### Step 2 — Add the flow after the confirmation message

Click **+** below the confirmation message → **Add a tool** → search and select `Investment Report Approval Flow`

### Step 3 — Map the inputs

| Flow Input | Map to Variable |
|---|---|
| `RequesterName` | `VarRequesterName` |
| `RequesterEmail` | `VarRequesterEmail` |
| `ReportType` | `VarReportType` |
| `Reason` | `VarReason` |

### Step 4 — Add final message

Click **+** → **Send a message**:

```
✅ Your request has been submitted!

You will receive a confirmation email 
once the manager reviews your request. 🌟
```

### Step 5 — Add end conversation

Click **+** → **Topic management** → **End conversation**

### Step 6 — Save the topic

Click **Save**

---

## Part 4 — Test It

In the **Test pane** click **+** to start a new session, then type:

```
I want to request a report
```

Walk through the prompts:

```
Name?        → Your name
Email?       → Your email address
Report type? → Star Rating Analysis
Reason?      → Fund comparison for client
```

Then verify:

| Check | Expected |
|---|---|
| Outlook / Teams | Approval request arrives from the flow |
| Click **Approve** in Outlook | — |
| Check inbox | Confirmation email with your name and report type |

---

## Troubleshooting

| Problem | Fix |
|---|---|
| `"Identifier not recognized"` in topic | Delete the red chip, re-insert using **{x}** button |
| Email shows `{RequesterName}` as text | Rebuild email body using **⚡ dynamic content** picker |
| Flow not showing in "Add a tool" | Make sure the flow was **Published**, not just saved |
| Approval request not arriving | Check the **Assigned to** field has your correct email |
| Variables not in {x} picker | Check each question node has **"Save response as"** filled in |

---

*Lab Version 1.0 | Morningstar India Investment Agent | Microsoft Copilot Studio*
