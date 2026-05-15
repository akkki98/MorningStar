# 🧪 Lab Instructions: Morningstar Document Research Agent
### SharePoint AI Agent — Hands-On Lab Guide  
**Difficulty:** Beginner to Intermediate  
**Platform:** Microsoft SharePoint + Microsoft 365

---

## 📋 Table of Contents

1. [Lab Overview](#1-lab-overview)
2. [Prerequisites](#2-prerequisites)
3. [Lab Setup](#3-lab-setup)
4. [Module 1 — Upload Knowledge Sources to SharePoint](#module-1--upload-knowledge-sources-to-sharepoint)
5. [Module 2 — Create the SharePoint Agent](#module-2--create-the-sharepoint-agent)
6. [Module 3 — Configure Knowledge Source](#module-3--configure-knowledge-source)
7. [Module 4 — Write the System Prompt](#module-4--write-the-system-prompt)
8. [Module 5 — Test the Agent](#module-5--test-the-agent)

---

## 1. Lab Overview

### 🎯 Objective
In this lab, you will build a **Morningstar Document Research Agent** on SharePoint that allows users to ask questions in plain English and receive accurate answers sourced directly from internal research documents.

### 🏗️ What You Will Build

```
SharePoint Document Library
├── Morningstar_Equity_Research_Report.pdf
├── Morningstar_Knowledge_Base.xlsx
└── DocumentResearchAgent.agent  ← You will build this
```

### 📂 Knowledge Sources Used

| File | Contents |
|---|---|
| `Morningstar_Equity_Research_Report.pdf` | Apple Inc. equity research report with fair value, financials, risks, and valuation methodology |
| `Morningstar_Knowledge_Base.xlsx` | 4 sheets — Equity Ratings, Fund Performance, Analyst Coverage, Price & Rating Log |

### ✅ Learning Outcomes
By the end of this lab, you will be able to:
- Upload and organize knowledge source files in SharePoint
- Create and configure a SharePoint AI Agent
- Connect the agent to a document library
- Write an effective system prompt
- Test the agent with structured prompts
- Troubleshoot common agent issues

---

## 2. Prerequisites

### 🔑 Access Requirements
Before starting this lab, ensure you have:

- [ ] Microsoft 365 account with SharePoint access
- [ ] Permission to create SharePoint sites or access an existing one
- [ ] Microsoft Copilot Studio license **OR** SharePoint Premium (for agent creation)
- [ ] The two knowledge source files downloaded:
  - `Morningstar_Equity_Research_Report.pdf`https://poc29e5c.blob.core.windows.net/ref/Morningstar_Equity_Research_Report.pdf
  - `Morningstar_Knowledge_Base.xlsx` https://poc29e5c.blob.core.windows.net/ref/Morningstar_Knowledge_Base.xlsx


---

## 3. Lab Setup

### 📁 Step 1 — Prepare Your Files

Ensure you have both files ready on your local machine:

```
📁 Local Folder
├── Morningstar_Equity_Research_Report.pdf
└── Morningstar_Knowledge_Base.xlsx
```

### 🌐 Step 2 — Navigate to SharePoint

1. Open your browser and go to:
   ```
   https://[your-tenant].sharepoint.com
   ```
2. Navigate to your **Morningstar SharePoint site**
3. Click on **Documents** in the left navigation panel

---

## Module 1 — Upload Knowledge Sources to SharePoint



### Step 1.1 — Open the Documents Library
1. Go to your SharePoint site
2. Click **Documents** in the left sidebar
3. You should see the document library grid view

### Step 1.2 — Upload the PDF File
1. Click **+ New** → **File upload** (or drag and drop)
2. Select `Morningstar_Equity_Research_Report.pdf` from your local machine
3. Wait for the upload to complete
4. ✅ Confirm it appears in the library with a PDF icon

### Step 1.3 — Upload the Excel File
1. Click **+ New** → **File upload** again
2. Select `Morningstar_Knowledge_Base.xlsx`
3. Wait for the upload to complete
4. ✅ Confirm it appears in the library with an Excel icon

### Step 1.4 — Verify Uploads

Your Documents library should now show:

```
Documents
├── 📄 Morningstar_Equity_Research_Report.pdf    ← just uploaded
└── 📊 Morningstar_Knowledge_Base.xlsx           ← just uploaded
```

> ⚠️ **Important:** Wait **15–30 minutes** after uploading before testing the agent. SharePoint needs time to index the files so the agent can search them.

---

## Module 2 — Create the SharePoint Agent



### Step 2.1 — Open Agent Builder
1. From your SharePoint Documents library, click the **⚡ AI actions** button in the top toolbar
2. Select **"Create an agent"** from the dropdown
   
   > Alternatively, click **+ New** → **Agent**

### Step 2.2 — Name Your Agent
1. In the agent creation panel, enter the name:
   ```
   DocumentResearchAgent
   ```
2. Add a description:
   ```
   AI research assistant for Morningstar equity reports, 
   fund data, analyst ratings, and fair value estimates.
   ```


---

## Module 3 — Configure Knowledge Source


### Step 3.1 — Open Agent Settings
1. Click on `DocumentResearchAgent.agent` in the Documents library
2. The agent editor panel will open on the right side
3. Look for the **"Knowledge"** or **"Sources"** tab

### Step 3.2 — Add SharePoint as Knowledge Source
1. Click **"+ Add knowledge source"**
2. Select **"SharePoint"** from the source options
3. Enter your SharePoint site URL:
   ```
   https://[your-tenant].sharepoint.com/sites/Morningstar
   ```
4. Click **Connect**

### Step 3.3 — Select Knowledge Files
1. Browse to the **Documents** library
2. Select both files:
   - ✅ `Morningstar_Equity_Research_Report.pdf`
   - ✅ `Morningstar_Knowledge_Base.xlsx`
3. Click **Add** or **Confirm**

### Step 3.4 — Verify Connection

Your Knowledge Sources panel should show:

```
Knowledge Sources
├── ✅ Morningstar_Equity_Research_Report.pdf   [SharePoint]
└── ✅ Morningstar_Knowledge_Base.xlsx          [SharePoint]
```

> ⚠️ If files are not visible, ensure they are fully uploaded and try refreshing the page.

---

## Module 4 — Write the System Prompt

**⏱ Estimated Time: 10 minutes**

The system prompt tells the agent **who it is** and **how to behave**. This is the most important configuration step.

### Step 4.1 — Open the Instructions / System Prompt Field
1. In the agent editor, find the **"Instructions"** or **"System Prompt"** field
2. Clear any default text

### Step 4.2 — Paste the System Prompt

Copy and paste the following system prompt exactly:

```
You are the Morningstar Document Research Assistant, an AI agent 
built to help employees retrieve accurate information from 
Morningstar's internal research documents stored in SharePoint.

You have access to two knowledge source files:
1. Morningstar_Equity_Research_Report.pdf — Contains Apple Inc. 
   equity research including fair value estimate, financial summary, 
   risk factors, analyst opinion, and valuation methodology.
2. Morningstar_Knowledge_Base.xlsx — Contains 4 sheets:
   - "Equity Ratings Universe": 15 stocks with star ratings, 
     fair values, moat ratings, and analyst assignments
   - "Fund Performance": 12 funds with returns, expense ratios, 
     and risk profiles
   - "Analyst Coverage": 8 analysts with coverage areas and 
     report counts
   - "Price & Rating Log": Historical AAPL price and rating data 
     from January to May 2026

RULES:
- Only answer using data from the uploaded knowledge source files
- Never make up or estimate values not found in the documents
- Always specify which file and section your answer comes from
- If the data is not in the documents, say: 
  "This information is not available in the current knowledge sources."
- Format responses clearly using tables or bullet points
- Keep answers concise and factual
```

### Step 4.3 — Save the System Prompt
1. Click **Save** or **Apply**
2. ✅ Confirm the instructions are saved

---

## Module 5 — Test the Agent

**⏱ Estimated Time: 20 minutes**

Now you will test the agent using structured prompts to verify it reads from your knowledge sources correctly.

### Step 5.1 — Open the Agent Chat
1. Click **"Test"** or **"Open in chat"** in the agent editor
2. The chat interface will open

---

### 🧪 Test 1 — Fair Value Lookup (PDF)

**Paste this prompt:**
```
You are a Morningstar research assistant.
Read the file "Morningstar_Equity_Research_Report.pdf" from SharePoint.
Find the section called "Valuation Methodology".
Return ONLY:
- Fair Value Estimate
- The 3 methods used
- The weight and weighted fair value for each method
Format as a table.
```

**✅ Expected Result:**

| Methodology | Implied FV | Weight | Weighted FV |
|---|---|---|---|
| DCF (Base Case) | $218.00 | 50% | $109.00 |
| EV/EBITDA (25x FY2026E) | $207.00 | 25% | $51.75 |
| P/E (28x FY2026E EPS) | $208.00 | 25% | $52.00 |
| **Blended Fair Value** | | | **$212.75** |

---

### 🧪 Test 2 — Undervalued Stocks (Excel)

**Paste this prompt:**
```
You are a Morningstar research assistant.
Read the sheet "Equity Ratings Universe" from 
"Morningstar_Knowledge_Base.xlsx" in SharePoint.
Find all rows where Star Rating is 4 or 5 stars AND 
Current Price is LESS than Fair Value.
Return: Ticker | Company | Star Rating | Fair Value | Current Price | Moat
Sort by Star Rating descending.
```

**✅ Expected Result:** Should return stocks including AAPL, GOOGL, AMZN, BRK.B, JNJ, UNH, XOM

---

### 🧪 Test 3 — Fund Filter (Excel)

**Paste this prompt:**
```
You are a Morningstar research assistant.
Read the sheet "Fund Performance" from 
"Morningstar_Knowledge_Base.xlsx" in SharePoint.
Find all funds where Expense Ratio is less than 0.50%.
Return: Fund Name | Ticker | Expense Ratio | Morningstar Rating | Risk Profile
Sort by Expense Ratio lowest to highest.
```

**✅ Expected Result:** Should return FXAIX (0.015%), VTSAX (0.04%), VWELX (0.17%), DODGX (0.52% — borderline), FCNTX (0.39%)

---

### 🧪 Test 4 — Analyst Lookup (Excel)

**Paste this prompt:**
```
You are a Morningstar research assistant.
Read the sheet "Analyst Coverage" from 
"Morningstar_Knowledge_Base.xlsx" in SharePoint.
Return the total YTD reports published across ALL analysts.
Show a table with: Analyst Name | Coverage Area | YTD Reports
Add a TOTAL row at the bottom.
```

**✅ Expected Result:** Total YTD Reports = **273**

---

### 🧪 Test 5 — Historical Price Log (Excel)

**Paste this prompt:**
```
You are a Morningstar research assistant.
Read the sheet "Price & Rating Log" from 
"Morningstar_Knowledge_Base.xlsx" in SharePoint.
Find the row where Date = "2026-03-03".
Return: Close Price | Fair Value | Star Rating | Analyst Note
Return ONLY this row. No extra commentary.
```

**✅ Expected Result:**
- Close Price: $188.50
- Fair Value: $215.00
- Star Rating: ★★★★☆
- Analyst Note: FVE raised to $215; Vision Pro 2 launch

---

### 🧪 Test 6 — Cross-Document Summary (Advanced)

**Paste this prompt:**
```
You are a Morningstar research assistant.
Read BOTH files from SharePoint:
1. "Morningstar_Equity_Research_Report.pdf"
2. Sheet "Price & Rating Log" from "Morningstar_Knowledge_Base.xlsx"

Create a structured client briefing for Apple Inc. with:
1. Current Rating & Fair Value (1 line)
2. Latest Financial Highlights — FY2024A only (3 bullet points)
3. Top 3 Risk Factors (3 bullet points)
4. Price trend summary from Jan to May 2026 (2 sentences)
Keep it concise.
```

**✅ Expected Result:** A structured 4-section briefing pulling data from both files

---

### 📊 Test Results Tracker

| Test | Expected Data Found | Pass / Fail | Notes |
|---|---|---|---|
| Test 1 — Fair Value | $212.75 blended FV | | |
| Test 2 — Undervalued Stocks | 7+ stocks listed | | |
| Test 3 — Low Cost Funds | FXAIX at top | | |
| Test 4 — Analyst YTD Total | 273 reports | | |
| Test 5 — Date Lookup | Mar 3 row correct | | |
| Test 6 — Cross-Document | Both files referenced | | |

---


---

### 🚀 Next Steps — Extend the Agent

Once your base agent is working, consider these enhancements:

1. **Add More Knowledge Sources**
   - Upload additional analyst reports (MSFT, GOOGL, NVDA)
   - Add a fund methodology PDF
   - Include a compliance policy document

2. **Deploy to Microsoft Teams**
   - Share the agent in a Teams channel for your analyst team
   - Enable @mention support

3. **Add More Excel Sheets**
   - ESG Ratings sheet
   - Sector performance tracker
   - Client portfolio data

4. **Scheduled Refresh**
   - Set up a weekly process to update the Excel knowledge base
   - Configure agent to notify users of data updates

---

### 📚 Reference

| Resource | Link |
|---|---|
| Microsoft SharePoint Agents Docs | https://learn.microsoft.com/sharepoint |
| Copilot Studio Documentation | https://learn.microsoft.com/microsoft-copilot-studio |
| SharePoint Admin Center | https://admin.microsoft.com |

---

*© 2026 Morningstar, Inc. — Internal Lab Guide | Document Version 1.0*
