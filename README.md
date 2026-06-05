# 🚀 AML Fraud Compliance Screening — n8n Workflow

**Author:** Banking Compliance AI Tester  
**Domain:** Payments | AML | Fraud Screening  
**Stack:** n8n · Groq/ChatGPT LLM · AI Agent · PostgreSQL/MySQL · Excel · Email Alerts  

---

## 📌 Overview

This project implements an **end-to-end AML (Anti-Money Laundering) and Fraud Compliance Screening workflow** using **n8n automation** and **AI-powered decisioning**.

The workflow processes **PAC008 payment transactions**, screens them against sanctions/fraud watchlists, and uses an AI agent to make compliance decisions.

---

## ⚙️ What This Workflow Does

When a PAC008 payment is received:

1. ✅ Triggered via Webhook / Scheduler / DB polling  
2. ✅ Checks transaction against fraud/sanctions watchlist  
3. ✅ Sends data to AI Agent (LLM)  
4. ✅ AI decides → **HIT or NO HIT**  
5. ✅ If HIT → Block transaction & move to **Pending/Repair queue**  
6. ✅ If NO HIT → Mark transaction as **PASSED**  
7. ✅ Store results in database  
8. ✅ Export compliance report to Excel  
9. ✅ Send email alert for high-risk cases  

---

## 🔄 Workflow Architecture
<img width="958" height="468" alt="image" src="https://github.com/user-attachments/assets/af104a68-2a69-4729-8a8a-562e7ba4e5d9" />





## 🧪 AML Test Cases

### ✅ 1. No Hit Transaction
{
  "txn_ref": "PAC008-DEMO-001",
  "sender_account": "GB29NWBK60161331926819",
  "beneficiary_account": "NL91ABNA0417164300",
  "beneficiary_name": "Clean Vendor BV",
  "amount": 5000,
  "currency": "GBP",
  "destination_country": "NL"
}

## 2. MEDIUM RISK (Fraud Watchlist)
{
  "txn_ref": "PAC008-DEMO-002",
  "sender_account": "GB29NWBK60161331926819",
  "beneficiary_account": "GB12FAKE12345678901234",
  "beneficiary_name": "Fraud Merchant Ltd",
  "amount": 15000,
  "currency": "GBP",
  "destination_country": "GB"
}

##3. HIGH RISK (Iran Sanctions HIT)
{
  "txn_ref": "PAC008-DEMO-003",
  "sender_account": "GB29NWBK60161331926819",
  "beneficiary_account": "IR987654321098765",
  "beneficiary_name": "Tehran Import Export",
  "amount": 75000,
  "currency": "USD",
  "destination_country": "IR"
}
``



