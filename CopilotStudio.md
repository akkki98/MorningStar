# 🏦 Morningstar India — Investment Agent Lab Instructions
### Microsoft Copilot Studio | Hands-On Lab Guide

---

> **Lab Level:** Beginner to Intermediate  
> **Estimated Time:** 3 to 4 Hours  
> **Tool:** Microsoft Copilot Studio  
> **Prerequisites:** Microsoft 365 Account, Copilot Studio License

---

## 📋 Table of Contents

1. [Lab Overview](#1-lab-overview)
2. [Pre-Lab Setup](#2-pre-lab-setup)
3. [Lab 1 — Create the Agent](#3-lab-1--create-the-agent)
4. [Lab 2 — Configure Agent Instructions](#4-lab-2--configure-agent-instructions)
5. [Lab 3 — Add Knowledge Sources](#5-lab-3--add-knowledge-sources)
6. [Lab 4 — Create the Greeting Topic](#6-lab-4--create-the-greeting-topic)
7. [Lab 5 — Create the Mutual Funds Topic](#7-lab-5--create-the-mutual-funds-topic)
8. [Lab 6 — Create the Morningstar Ratings Topic](#8-lab-6--create-the-morningstar-ratings-topic)
9. [Lab 7 — Create the Risk & Returns Topic](#9-lab-7--create-the-risk--returns-topic)
10. [Lab 8 — Configure Fallback Topic](#10-lab-8--configure-fallback-topic)
11. [Lab 9 — Fund Research with Power Automate](#11-lab-9--fund-research-with-power-automate)
12. [Lab 10 — Test & Publish the Agent](#12-lab-10--test--publish-the-agent)
13. [Troubleshooting](#13-troubleshooting)
14. [Reference — All Trigger Phrases](#14-reference--all-trigger-phrases)

---

## 1. Lab Overview

In this lab, you will build a **Morningstar India Investment Education Agent** using Microsoft Copilot Studio. By the end of this lab, the agent will be able to:

- Answer questions about mutual fund concepts (NAV, SIP, Expense Ratio)
- Explain Morningstar ratings (Star Rating, Moat Rating, Analyst Rating)
- Explain risk and return terms (Alpha, Beta, Sharpe Ratio)
- Search for live mutual fund data using Power Automate
- Use uploaded PDF documents as a knowledge source

### 🏗️ Agent Architecture

```
User Message
      ↓
Copilot Studio Agent
      ↓
┌─────────────────────────────────────────┐
│  Topics          │  Knowledge Source    │
│  ─────────────   │  ─────────────────   │
│  • Greeting      │  • Star Rating PDF   │
│  • Mutual Funds  │  • Moat Rating PDF   │
│  • Ratings       │  • AMFI/SEBI docs    │
│  • Risk/Returns  │                      │
│  • Fallback      │                      │
└─────────────────────────────────────────┘
      ↓
Power Automate (Fund Research)
      ↓
mfapi.in / Morningstar API
```

---

## 2. Pre-Lab Setup

### ✅ Step 1 — Download Knowledge Source PDFs

Download the following files that will be uploaded as knowledge sources:

| File | Description |
|---|---|
| `Morningstar_Star_Rating_Methodology.pdf` | Explains how star ratings are calculated |
| `Morningstar_Moat_Rating_Guide.pdf` | Explains economic moat concept and ratings |

> **Note:** These PDFs have been provided as part of this lab package.

---

### ✅ Step 2 — Sign In to Copilot Studio

1. Open your browser and go to: **https://copilotstudio.microsoft.com**
2. Sign in with your **Microsoft 365 credentials**
3. Select your **Environment** from the top-right dropdown
4. You should see the Copilot Studio home screen

---

### ✅ Step 3 — Verify Access

Confirm you can see the following in the left navigation:

- ✅ Agents
- ✅ Topics
- ✅ Knowledge
- ✅ Actions
- ✅ Analytics

---

## 3. Lab 1 — Create the Agent

**Estimated Time: 10 minutes**

### Steps

1. On the Copilot Studio home screen, click **Create** in the left navigation
2. Select **New Agent**
3. Choose **Skip to configure** (do not use the AI builder wizard)
4. Fill in the following details:

| Field | Value |
|---|---|
| **Name** | Morningstar Learning Bot |
| **Description** | An investment education assistant that helps retail investors understand mutual funds, stocks, and Morningstar ratings |
| **Icon** | Upload a Morningstar-themed icon (optional) |
| **Language** | English (India) |

5. Click **Create**
6. You will be taken to the **Agent Overview** page

> ✅ **Checkpoint:** You should now see your agent listed under **Agents** in the left navigation.

---

## 4. Lab 2 — Configure Agent Instructions

**Estimated Time: 10 minutes**

### Steps

1. On the Agent Overview page, scroll down to the **Instructions** section
2. Click **Edit**
3. Clear any default text and paste the following instructions:

```
You are an Investment Education Assistant for Morningstar India.
Your name is "Morningstar Learning Bot".

## YOUR ROLE
You help retail investors and beginners in India understand
investment concepts related to mutual funds, stocks, and
Morningstar's proprietary ratings. You are friendly, simple,
and educational — not a financial advisor.

## WHAT YOU CAN HELP WITH
- Explain mutual fund concepts (NAV, SIP, expense ratio,
  exit load, lump sum, ELSS, etc.)
- Explain Morningstar ratings (Star Rating, Moat Rating,
  Analyst Rating, Sustainability Rating)
- Explain stock market concepts (P/E ratio, market cap,
  dividend yield, EPS, fair value)
- Explain risk and return terms (alpha, beta, Sharpe ratio,
  volatility, standard deviation)
- Answer questions using the uploaded Morningstar knowledge
  documents

## WHAT YOU CANNOT DO
- Do NOT recommend specific funds or stocks to buy or sell
- Do NOT provide personalized financial advice
- Do NOT predict market movements or future returns
- Do NOT discuss topics outside of investing and finance

## HOW TO RESPOND
- Always use simple, plain English
- Always give a real-life Indian Rupee (INR) example
- Keep answers between 3 to 6 sentences for simple questions
- After every answer, suggest 2 related topics to explore
- Always be encouraging toward beginner investors

## TONE
- Friendly, patient, and approachable
- Speak like a knowledgeable friend, not a textbook
- Never make the user feel bad for asking basic questions

## DISCLAIMER
End complex financial topic answers with:
"Note: This is for educational purposes only and is not
financial advice. Please consult a SEBI-registered financial
advisor before making investment decisions."
```

4. Click **Save**

> ✅ **Checkpoint:** Instructions should be saved and visible in the Overview section.

---

## 5. Lab 3 — Add Knowledge Sources

**Estimated Time: 15 minutes**

### Steps

1. In the left navigation click **Knowledge**
2. Click **Add Knowledge**
3. Select **Files**
4. Upload the following files one at a time:
   - `Morningstar_Star_Rating_Methodology.pdf`
   - `Morningstar_Moat_Rating_Guide.pdf`
5. Wait for the status to show **Ready** for both files (may take 2-3 minutes)
6. Go back to **Knowledge** and click **Add Knowledge** again
7. Select **Public Websites**
8. Add the following URLs:

| URL | Purpose |
|---|---|
| `https://www.morningstar.in` | Main Morningstar India site |
| `https://www.amfiindia.com` | AMFI investor education |

9. Click **Save**

### Enable Generative Answers

1. Go to **Agent Settings** (gear icon, top right)
2. Click **Generative AI**
3. Under **Generative Answers**, toggle to **Enabled**
4. Set **Content moderation** to **Medium**
5. Click **Save**

> ✅ **Checkpoint:** You should see 2 PDFs and 2 websites listed under Knowledge, all with status **Ready**.

---

## 6. Lab 4 — Create the Greeting Topic

**Estimated Time: 15 minutes**

### Steps

1. In the left navigation click **Topics**
2. Click **Add a Topic → From Blank**
3. Name the topic: **Greeting**

### Configure Trigger Phrases

4. Click on the **Trigger** node
5. Add the following phrases (add each one separately):

```
Hi
Hello
Get started
What can you do
Help
Start
I want to learn investing
Good morning
Hey
```

### Configure the Message Node

6. Click the **+** below the trigger node
7. Select **Send a message**
8. Paste the following message:

```
👋 Welcome to Morningstar India Learning Bot!

I'm here to help you understand investing — from 
mutual funds to stock ratings — in simple terms.

Here's what I can help you with:

📚 Mutual Fund Concepts
   (NAV, SIP, Expense Ratio, Types of Funds)

⭐ Morningstar Ratings
   (Star Rating, Moat Rating, Analyst Rating)

📊 Stock Market Basics
   (P/E Ratio, Dividends, Fair Value)

📉 Risk & Returns
   (Alpha, Beta, Sharpe Ratio, Volatility)

💼 Portfolio & Tax
   (Diversification, ELSS, Capital Gains)

Type any concept or question to get started!
```

### Add Conversation Starters

9. Go back to **Agent Overview**
10. Scroll to **Conversation Starters**
11. Click **Edit** and add:

```
What is NAV in a mutual fund?
Explain Morningstar Star Rating
What is an economic moat?
What is SIP and how does it work?
What is the difference between alpha and beta?
What does expense ratio mean?
```

12. Click **Save Topic**

> ✅ **Checkpoint:** Test by typing "Hi" in the test panel. You should see the welcome message.

---

## 7. Lab 5 — Create the Mutual Funds Topic

**Estimated Time: 25 minutes**

### Steps

1. Click **Topics → Add a Topic → From Blank**
2. Name the topic: **Mutual Funds**

### Configure Trigger Phrases

3. Add the following trigger phrases:

```
mutual fund
what is mutual fund
NAV
net asset value
SIP
systematic investment plan
expense ratio
exit load
types of mutual funds
ELSS
direct plan
regular plan
lump sum investment
how to invest in mutual fund
```

### Add Welcome Message Node

4. Add a **Send a message** node:

```
Great! Let me help you understand Mutual Funds. 🎯

Mutual Funds pool money from many investors and 
invest in stocks, bonds, or both — managed by a 
professional fund manager.

Which concept would you like to explore?
```

### Add Ask a Question Node

5. Add an **Ask a Question** node:

| Field | Value |
|---|---|
| **Question** | Which mutual fund concept would you like to learn about? |
| **Identify** | User's entire response |
| **Save response as** | VarUserQuestion (String) |

### Add Generative Answers Node

6. Click **+** and select **Generative Answers**
7. Configure as follows:

| Field | Value |
|---|---|
| **Input** | VarUserQuestion |
| **Data Sources** | Select both uploaded PDFs |
| **Allow AI to search knowledge** | ✅ Enabled |

### Add Follow-Up Question Node

8. Add another **Ask a Question** node after Generative Answers:

| Field | Value |
|---|---|
| **Question** | Would you like to explore another mutual fund concept? |
| **Option 1** | Yes, ask another question |
| **Option 2** | Go to Main Menu |
| **Option 3** | No thanks, I'm done |
| **Save response as** | VarNextAction |

### Add Condition Node

9. Add a **Condition** node:

```
IF VarNextAction = "Yes, ask another question"
    → Redirect to: Ask a Question node (loop back)

IF VarNextAction = "Go to Main Menu"  
    → Redirect to: Greeting Topic

IF VarNextAction = "No thanks, I'm done"
    → Go to: End Conversation node
```

### Add End Conversation Node

10. Add an **End Conversation** node with message:

```
Thank you for learning with Morningstar India! 🌟

Remember: The more you learn, the better 
decisions you make.

Visit www.morningstar.in for detailed research.

Note: This is for educational purposes only.
```

11. Click **Save Topic**

> ✅ **Checkpoint:** Test by typing "What is NAV?" in the test panel. The bot should return an answer from the PDF knowledge source.

---

## 8. Lab 6 — Create the Morningstar Ratings Topic

**Estimated Time: 20 minutes**

### Steps

1. Click **Topics → Add a Topic → From Blank**
2. Name the topic: **Morningstar Ratings**

### Configure Trigger Phrases

3. Add the following trigger phrases:

```
star rating
morningstar rating
5 star fund
moat rating
economic moat
wide moat
narrow moat
analyst rating
gold rating
silver rating
bronze rating
sustainability rating
how is star rating calculated
what does moat mean
morningstar methodology
```

### Add Message Node

4. Add a **Send a message** node:

```
⭐ Let me explain Morningstar's rating systems!

Morningstar has several rating types to help 
investors evaluate funds and stocks:

1️⃣ Star Rating — Quantitative, past performance
2️⃣ Analyst Rating — Qualitative, forward-looking
3️⃣ Moat Rating — Competitive advantage of a company
4️⃣ Sustainability Rating — ESG factors

What would you like to know about?
```

### Add Ask a Question Node

5. Add an **Ask a Question** node:

| Field | Value |
|---|---|
| **Question** | Which Morningstar rating would you like to understand? |
| **Identify** | User's entire response |
| **Save response as** | VarRatingQuestion (String) |

### Add Generative Answers Node

6. Add a **Generative Answers** node:

| Field | Value |
|---|---|
| **Input** | VarRatingQuestion |
| **Data Sources** | Both PDFs (Star Rating + Moat Rating) |

7. Add follow-up and end nodes same as Lab 5
8. Click **Save Topic**

> ✅ **Checkpoint:** Test by typing "What is a wide moat?" — the bot should explain using the Moat Rating PDF.

---

## 9. Lab 7 — Create the Risk & Returns Topic

**Estimated Time: 20 minutes**

### Steps

1. Click **Topics → Add a Topic → From Blank**
2. Name the topic: **Risk and Returns**

### Configure Trigger Phrases

3. Add the following trigger phrases:

```
alpha
beta
sharpe ratio
volatility
standard deviation
risk adjusted return
what is alpha in mutual fund
what is beta
how risky is a fund
fund risk
market risk
risk measure
```

### Add Message Node

4. Add a **Send a message** node:

```
📊 Understanding Risk & Returns

Before investing, it's important to understand 
how risk is measured. Here are the key terms:

📌 Alpha — Excess return over benchmark
📌 Beta — Sensitivity to market movements
📌 Sharpe Ratio — Return per unit of risk
📌 Standard Deviation — Measure of volatility

What would you like me to explain?
```

### Add Ask a Question + Generative Answers

5. Follow the same pattern as Labs 5 and 6:
   - Ask a Question → VarRiskQuestion (String)
   - Generative Answers → Input: VarRiskQuestion
   - Follow-up question → Loop or End

6. Click **Save Topic**

> ✅ **Checkpoint:** Test by typing "Explain beta" — the bot should give a clear explanation with an example.

---

## 10. Lab 8 — Configure Fallback Topic

**Estimated Time: 10 minutes**

### Steps

1. In **Topics**, find the **System Topics** section
2. Click on **Fallback**
3. Find the existing message node and replace the message with:

```
🤔 I'm not sure I understood that.

Here are topics I can help you with:

📚 Mutual Fund Concepts
⭐ Morningstar Ratings
📊 Stock Market Basics
📉 Risk & Returns Terms
💼 Portfolio & Tax Planning

Please try typing one of these topics, or ask 
me a question like:
"What is NAV?" or "Explain star rating"

You can also visit www.morningstar.in for 
detailed fund and stock research.
```

4. Click **Save Topic**

> ✅ **Checkpoint:** Test by typing "pizza" or a random word — the bot should show the fallback message.

---

## 11. Lab 9 — Fund Research with Power Automate

**Estimated Time: 45 minutes**

### Overview

This lab connects your agent to a live mutual fund API so users can search for real fund data.

```
User types fund name
        ↓
Copilot Studio calls Power Automate
        ↓
Power Automate calls mfapi.in (free API)
        ↓
Returns fund name, NAV, scheme code
        ↓
Bot displays results
```

---

### Part A — Create Power Automate Flow

1. Go to **https://make.powerautomate.com**
2. Click **Create → Instant Cloud Flow**
3. Name the flow: **GetMutualFundData**
4. Select trigger: **When Copilot Studio calls a flow**
5. Click **Create**

### Add Input Parameter

6. In the trigger, click **Add an input**
7. Select **Text**
8. Name it: `FundName`

### Add HTTP Action

9. Click **+ New Step**
10. Search for and select **HTTP**
11. Configure:

| Field | Value |
|---|---|
| **Method** | GET |
| **URI** | `https://api.mfapi.in/mf/search?q=` and then click **Add dynamic content** → select `FundName` |

### Add Parse JSON Action

12. Click **+ New Step → Parse JSON**
13. In **Content**, select the **Body** from the HTTP step
14. Click **Generate from sample** and paste:

```json
[
  {
    "schemeCode": 100033,
    "schemeName": "Aditya Birla Sun Life Frontline Equity Fund"
  }
]
```

15. Click **Done**

### Add Compose Action

16. Click **+ New Step → Compose**
17. In **Inputs**, build this message using dynamic content:

```
Fund Search Results for: [FundName]

Scheme Name: [schemeName from Parse JSON]
Scheme Code: [schemeCode from Parse JSON]

To get detailed ratings and returns, 
visit: www.morningstar.in
```

### Add Return Value

18. Click **+ New Step**
19. Search for **Return value(s) to Copilot**
20. Click **Add an output → Text**
21. Name: `FundDetails`
22. Value: Select **Outputs** from the Compose step
23. Click **Save** the flow

---

### Part B — Connect Flow to Copilot Studio

1. Go back to **Copilot Studio**
2. Click **Topics → Add a Topic → From Blank**
3. Name: **Fund Research**

### Trigger Phrases

4. Add triggers:

```
search fund
find fund
fund details
look up fund
check fund rating
tell me about a fund
fund performance
search for mutual fund
```

### Ask for Fund Name

5. Add **Ask a Question** node:

| Field | Value |
|---|---|
| **Message** | Please enter the mutual fund name you want to search. Example: HDFC Top 100, SBI Bluechip, Axis Midcap |
| **Identify** | User's entire response |
| **Save as** | VarFundName (String) |

### Add Searching Message

6. Add a **Message** node:

```
🔍 Searching for "{VarFundName}"...
Please wait a moment.
```

### Call Power Automate

7. Click **+** and select **Call an Action**
8. Select **GetMutualFundData** flow
9. Map input: `FundName` → `VarFundName`
10. Map output: `FundDetails` → Create new variable `VarFundResult`

### Show Results

11. Add a **Message** node:

```
Here are the search results:

{VarFundResult}

💡 For detailed star ratings, expense ratio, 
and returns, visit: www.morningstar.in
```

### Add Follow-Up

12. Add **Ask a Question** node:

```
Would you like to search for another fund?
Options: Yes | No
Save as: VarSearchAgain
```

13. Add **Condition**:
    - If Yes → loop back to Ask for Fund Name
    - If No → End Conversation

14. Click **Save Topic**

> ✅ **Checkpoint:** Test by typing "search fund" and entering "HDFC" — you should get live fund results from the API.

---

## 12. Lab 10 — Test & Publish the Agent

**Estimated Time: 20 minutes**

### Part A — Test the Agent

1. Click the **Test** button (top right, chat bubble icon)
2. Run through the following test scenarios:

| Test | Input | Expected Result |
|---|---|---|
| Greeting | "Hi" | Welcome message with menu |
| NAV concept | "What is NAV?" | Explanation from PDF |
| Star Rating | "Explain star rating" | Morningstar methodology answer |
| Moat Rating | "What is wide moat?" | Moat guide explanation |
| Risk term | "What is beta?" | Beta explanation with example |
| Fund Search | "Search fund HDFC" | Live fund results |
| Unknown input | "What is pizza?" | Fallback message |
| Hindi test | "NAV kya hota hai?" | Response in Hindi (if configured) |

### Part B — Fix Common Issues

| Issue | Fix |
|---|---|
| Generative Answers not responding | Check Knowledge source status is **Ready** |
| Variable type error | Change Ask a Question identify to **User's entire response** |
| Power Automate not connecting | Re-authenticate the connection in the flow |
| Fallback triggering too often | Lower confidence threshold in Agent Settings |

### Part C — Publish the Agent

1. Click **Publish** button (top right)
2. Select **Publish** to confirm
3. Wait for the green **Published** confirmation

### Part D — Share the Agent (Optional)

1. Go to **Channels** in the left navigation
2. Choose a channel:

| Channel | Steps |
|---|---|
| **Microsoft Teams** | Click Teams → Add to Teams |
| **Website** | Click Custom Website → Copy embed code |
| **Demo Website** | Click Demo Website → Share link |

> ✅ **Checkpoint:** Share the Demo Website link with a colleague and have them test it.

---

## 13. Troubleshooting

### ❌ Error: Variable is being set to an incorrect type (EmbeddedOptionSet expected String)

**Cause:** Multiple choice question variable cannot be passed directly to Generative Answers.

**Fix:**
1. Click the **Ask a Question** node
2. Change **Identify** from **Multiple Choice** to **User's entire response**
3. The variable will now be saved as String type
4. Generative Answers will accept it without error

---

### ❌ Error: Knowledge source not returning answers

**Cause:** PDF not fully indexed or generative answers not enabled.

**Fix:**
1. Go to **Knowledge** and check status shows **Ready**
2. Go to **Settings → Generative AI → Enable Generative Answers**
3. Re-test after 2-3 minutes

---

### ❌ Error: Power Automate flow not found in Copilot Studio

**Cause:** Flow not saved or created in wrong environment.

**Fix:**
1. Ensure the Power Automate flow is in the **same environment** as Copilot Studio
2. Go to flow → ensure it is **turned on**
3. In Copilot Studio, click **Refresh** in the Actions panel

---

### ❌ Error: HTTP action in Power Automate returns 400/404

**Cause:** Fund name has spaces or special characters in the URL.

**Fix:** Add a **Compose** step before HTTP to encode the fund name:
```
uriComponent(triggerBody()?['text'])
```
Use this composed value in the HTTP URI instead of the raw variable.

---

## 14. Reference — All Trigger Phrases

### Greeting Topic
```
Hi, Hello, Get started, What can you do, Help, 
Start, I want to learn investing, Good morning, Hey
```

### Mutual Funds Topic
```
mutual fund, NAV, net asset value, SIP, 
systematic investment plan, expense ratio, exit load, 
types of mutual funds, ELSS, direct plan, regular plan,
lump sum, how to invest in mutual fund
```

### Morningstar Ratings Topic
```
star rating, morningstar rating, 5 star fund, 
moat rating, economic moat, wide moat, narrow moat,
analyst rating, gold rating, silver rating, bronze rating,
sustainability rating, morningstar methodology
```

### Risk & Returns Topic
```
alpha, beta, sharpe ratio, volatility, 
standard deviation, risk adjusted return,
what is alpha, what is beta, fund risk, market risk
```

### Fund Research Topic
```
search fund, find fund, fund details, look up fund,
check fund rating, tell me about a fund, 
fund performance, search for mutual fund
```

### Fallback Topic
```
Triggered automatically for any unrecognized input
```

---

## 🏆 Lab Completion Checklist

```
✅ Lab 1  — Agent created with name and description
✅ Lab 2  — System instructions configured
✅ Lab 3  — 2 PDFs and 2 websites added as knowledge sources
✅ Lab 4  — Greeting topic with conversation starters
✅ Lab 5  — Mutual Funds topic with Generative Answers
✅ Lab 6  — Morningstar Ratings topic
✅ Lab 7  — Risk & Returns topic
✅ Lab 8  — Fallback topic configured
✅ Lab 9  — Power Automate fund search flow connected
✅ Lab 10 — Agent tested and published
```

---

## 📚 Additional Resources

| Resource | URL |
|---|---|
| Copilot Studio Documentation | https://learn.microsoft.com/copilot-studio |
| Power Automate Documentation | https://learn.microsoft.com/power-automate |
| Morningstar India | https://www.morningstar.in |
| AMFI Investor Education | https://www.amfiindia.com |
| Free Mutual Fund API | https://api.mfapi.in |
| SEBI Investor Education | https://www.sebi.gov.in/investors |

---

> **Disclaimer:** This lab is created for educational purposes to demonstrate Microsoft Copilot Studio capabilities using Morningstar India as a reference scenario. All investment content in this lab is for learning purposes only and does not constitute financial advice.

---

*Lab Version 1.0 | Morningstar India Investment Agent | Microsoft Copilot Studio*
