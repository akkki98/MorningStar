# 🏦 Morningstar India — Investment Agent Lab Instructions
### Microsoft Copilot Studio | Hands-On Lab Guide

---

> **Lab Level:** Beginner to Intermediate  
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


---

## 1. Lab Overview

In this lab, you will build a **Morningstar India Investment Education Agent** using Microsoft Copilot Studio. By the end of this lab, the agent will be able to:

- Answer questions about mutual fund concepts (NAV, SIP, Expense Ratio)
- Explain Morningstar ratings (Star Rating, Moat Rating, Analyst Rating)
- Explain risk and return terms (Alpha, Beta, Sharpe Ratio)
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





*Lab Version 1.0 | Morningstar India Investment Agent | Microsoft Copilot Studio*
