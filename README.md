# 🍽️ RR Restaurant WhatsApp AI Assistant  
### 🤖 Powered by n8n + Google Gemini + Google Sheets + WhatsApp API

---
### 🧾 Presentation (PPT)
📊 **View the complete presentation here:**  
[RR Restaurant WhatsApp AI Assistant – PPT](https://docs.google.com/presentation/d/1Sc66XvpsTBq1GzscD249lIoYDBbf-61h/edit?usp=sharing&ouid=113049746936695823016&rtpof=true&sd=true)

---

## 📘 Overview

**RR Restaurant AI Assistant** is an automated WhatsApp chatbot built using **n8n** and **Google Gemini AI**, designed to handle:
- 🛒 Taking food orders  
- 📦 Checking inventory  
- ❓ Answering FAQs  
- 🧾 Showing order status  

The workflow connects **WhatsApp**, **Google Sheets**, and **Gemini AI** to create a smart, conversational food-ordering experience.

---

## ⚙️ Workflow Summary

| Property | Description |
|-----------|--------------|
| **Workflow Name** | My workflow 4 |
| **Platform** | n8n |
| **Language Model** | Google Gemini (PaLM) |
| **Trigger** | WhatsApp message |
| **Database** | Google Sheets |
| **AI Memory** | Buffer memory (last 10 messages per user) |

---

## 🧩 Workflow Components

### 1. 🟢 **WhatsApp Trigger**
- Node: `WhatsApp Trigger`
- Purpose: Captures incoming messages from customers via WhatsApp.
- Webhook ID: `16bf761b-6b77-4cbf-be66-48368362b20a`

---

### 2. 🧠 **AI Agent**
- Node: `LangChain Agent`
- Role: Acts as the restaurant assistant with predefined conversational rules.
- Integrated with:
  - `Google Gemini Chat Model` → AI brain
  - `Simple Memory` → Conversation context
  - Google Sheets tools (`Inventory`, `Orders`, `FAQ`)
- Tone: Friendly, concise, and WhatsApp-like (short sentences, emojis, polite replies)

---

### 3. 🗣️ **Google Gemini Chat Model**
- Node: `Google Gemini Chat Model`
- Provides natural language responses based on prompt rules.
- Credential: `Google Gemini (PaLM) API`

---

### 4. 🧠 **Simple Memory**
- Node: `memoryBufferWindow`
- Stores last 10 messages for continuity in conversation.
- Session Key: Customer’s WhatsApp ID.

---

### 5. 📊 **Google Sheets Integration**

| Node | Sheet | Purpose |
|-------|--------|----------|
| `get Inventory` | Inventory | Check item availability |
| `post orders` | Orders | Append new confirmed orders |
| `FAQ` | FAQ | Fetch quick answers |
| `Get row(s)` | Orders/Inventory | Check existing data |

Google Sheet: [Food Delivery System](https://docs.google.com/spreadsheets/d/1DoANXGyG0dyrkFgcQi30iZz-hmW6KeJ0Bs8Sl2Tzvtc/edit?usp=drivesdk)

---

### 6. 💬 **Send Message**
- Node: `Send message`
- Sends AI-generated replies back to users on WhatsApp.
- Body: `{{ $json.output }}`

---
### 🎥 Project Execution Video
 
🔗 [Click here to watch execution video](https://drive.google.com/file/d/1SKHRt6jbnt4uqcLkPdjqR0QtiA4KodwW/view?usp=sharing)

---


## 🧭 Importing the Workflow into N8n

You can easily import and visualize this automation inside **N8n** (the no-code AI workflow builder).

### 🪄 Steps:

1. **Open n8n**
   - Go to [https://n8n.ai](https://n8n.ai) and log in to your account.

2. **Create a New Workspace**
   - Click **“New Workspace”** or open an existing one where you want to import the workflow.

3. **Import the Workflow File**
   - Click on the **“Import Workflow”** button.
   - Select the file:  
     ```
     /workflow/automation_flow.json
     ```
   - Natn will automatically generate the flow with all nodes and connections.

4. **Review the Nodes**
   - Verify that all nodes (Input Trigger, OpenAI Model, Output Action) are connected correctly.
   - Update any credentials or API keys (for example, your **OpenAI API key** or **Ngrok URL**) inside the configuration panels.

5. **Run a Test**
   - Click **“Run Workflow”**.
   - Send a sample input (for example: “Generate an email reply for a customer complaint.”)
   - Observe the output in the preview or console panel.

6. **Deploy the Workflow**
   - Click **“Publish”** or **“Deploy”** in Natn to make the workflow active and connect it to your real webhook or automation trigger.

---

### ✅ Screenshots
1. **Flow**

<img width="885" height="422" alt="Screenshot (42)" src="https://github.com/user-attachments/assets/018d7ee0-84a7-4f1c-aa45-d6feb9134680" />

2. **Chat**

<img width="1043" height="685" alt="Screenshot (43)" src="https://github.com/user-attachments/assets/d4af3cd7-86aa-4713-bb70-c56f78c978b3" />

3. **Orders**

<img width="1366" height="768" alt="Screenshot (44)" src="https://github.com/user-attachments/assets/f59ca273-679d-4136-b831-b1dc08285553" />



### ✅ Example Result in Natn

After import, you’ll see a visual flow like this:

## 🧱 Workflow Architecture Diagram

```plaintext
 ┌──────────────────────┐
 │ WhatsApp Trigger     │
 └─────────┬────────────┘
           │
           ▼
 ┌──────────────────────┐
 │ AI Agent (LangChain) │
 │  • Uses Google Gemini│
 │  • Memory enabled    │
 │  • Accesses Sheets   │
 └─────────┬────────────┘
           │
  ┌────────┼──────────────────────────────────────────┐
  ▼        ▼                  ▼                       ▼
Inventory Sheet      Orders Sheet             FAQ Sheet        Get Row (Check)
  │                       │                        │                │
  └──────────────→ Google Sheets API ←──────────────┘                │
           │                                                         │
           ▼                                                         ▼
                            Send Message → WhatsApp Reply



```

## 🔚 Conclusion

This project connects **WhatsApp, Google Sheets, and Gemini AI** to create a smart restaurant assistant that can chat, take orders, and reply instantly.  
It’s a simple idea that shows how AI + automation can make real work easier and faster.  

🍽️ Just chat. Order. Done.  

---

✍️ Author

Rithwik Racharla
📧 rithwikracharla@gmail.com

