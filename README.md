<div align="center">

# 🛡️ HerSafe AI

### A GenAI conversational assistant for harassment reporting and support navigation

*Turning a hard conversation into a clear, safe first step.*

<a href="https://hersafeai.netlify.app/"><img src="https://img.shields.io/badge/▶%20Try%20the%20live%20demo-hersafeai.netlify.app-E91E63?style=for-the-badge" alt="Try the live demo"></a>
&nbsp;
<a href="https://youtu.be/bx4r2AGHs5Q"><img src="https://img.shields.io/badge/Watch-Video%20walkthrough-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Video walkthrough"></a>

[![Built with n8n](https://img.shields.io/badge/Built%20with-n8n-EA4B71?style=flat-square)](https://n8n.io)
[![Powered by OpenRouter](https://img.shields.io/badge/Powered%20by-OpenRouter%20API-8A63D2?style=flat-square)](https://openrouter.ai)
[![SDG 5](https://img.shields.io/badge/SDG-5%20Gender%20Equality-FF3A21?style=flat-square)](https://sdgs.un.org/goals/goal5)
[![License: MIT](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)

**🌐 Live website: [https://hersafeai.netlify.app](https://hersafeai.netlify.app/)**

</div>

---

## ✨ Overview

Reporting harassment usually starts with a form that asks the hardest questions first. **HerSafe AI** flips that: the person simply describes what happened, in their own words, and the assistant does the structuring.

From one conversation it will:

- 🧠 **Understand** the narrative and extract structured incident details
- 🏷️ **Classify** the type of incident (online, workplace, stalking and others)
- ⚠️ **Assess** the safety context as High, Moderate or Low/Unclear concern
- 🤝 **Recommend** relevant categories of support
- 📝 **Draft** an editable, downloadable incident report

It is built end to end with **n8n** for orchestration and the **OpenRouter API** for language understanding, with no custom backend.

> Supports **UN SDG 5: Gender Equality** by improving access to reporting assistance and support resources.

---

## 🚀 Try it

1. Open **[hersafeai.netlify.app](https://hersafeai.netlify.app/)**, or scan the QR code below on your phone.
2. Start the chat and describe a situation in your own words. You can skip any question.
3. Review the safety guidance and support suggestions, then download your draft report.

<p align="center">
  <img src="./N8N%20Workflow%20Screenshots/HerSafeAI-QR%20CODE.png" width="180" alt="QR code to the HerSafe AI live demo">
</p>

---

## 🧩 How it works

<p align="center">
  <img src="./N8N%20Workflow%20Screenshots/N8N%20Workflow.png" width="100%" alt="HerSafe AI n8n workflow">
</p>

```
User (chat widget on the website)
      │
      ▼
n8n Chat Trigger  ──▶  Normalize input
      │
      ▼
AI Understanding  ──▶  Parse + validate JSON  ──▶  Safety Assessment
      │                                              │ high risk → immediate safety guidance
      ▼
Incident Classification  ──▶  Support & Guidance  ──▶  Draft Report
      │
      ▼
Response to user
```

| Stage | What it does |
|---|---|
| AI Understanding | The LLM reads the narrative and extracts category, description, date/time, context, whether it is ongoing, safety concern and support preference |
| Parse + Validate | Checks the model's JSON output and falls back safely if it is malformed |
| Safety Assessment | Rates concern only from what the user stated. High-risk cases skip straight to calm safety guidance |
| Support & Guidance | Suggests next steps and support categories, without inventing organization names or phone numbers |
| Report Generator | Compiles a clearly labeled, AI-generated, editable draft report |

Full design notes and rationale: [`docs/architecture.md`](docs/architecture.md)

---

## 🔒 Privacy & safety by design

- 🚫 Never asks for name, phone number, address or ID numbers
- ✅ Every question can be skipped
- 🏷️ All classifications are labeled as AI-generated and are never presented as legal or official determinations
- 🆘 If immediate danger is indicated, the flow prioritizes safety guidance over collecting details
- 🗂️ No database: conversation state lives only for the session
- 📄 The report is a **draft**. It is never submitted, filed or sent anywhere automatically

---

## 🛠️ Tech stack

| Layer | Technology |
|---|---|
| Workflow orchestration | [n8n](https://n8n.io) (Chat Trigger, AI Agent, LLM Chain, window buffer memory, Code nodes) |
| AI reasoning | [OpenRouter API](https://openrouter.ai) |
| Frontend | HTML + JavaScript chat widget |
| Hosting | [Netlify](https://hersafeai.netlify.app/) (frontend), n8n Cloud (workflow) |

---

## 💻 Run your own copy

1. **Import the workflow:** in n8n, choose *Import from file* and select `HerSafe AI - Workflow.json`.
2. **Add credentials:** create an OpenRouter credential with your API key and attach it to the OpenRouter chat model node.
3. **Activate** the workflow and copy the Chat Trigger's production URL.
4. **Connect the frontend:** in `Frontend/Frontend.html.html`, replace the webhook URL with yours, then open the file in a browser or deploy it to Netlify.

---

## 📁 Repository structure

```
HerSafeAI/
├── Frontend/                        # Chat widget UI (HTML + JS)
├── N8N Workflow Screenshots/        # Workflow screenshot and QR code for the live demo
├── docs/
│   └── architecture.md              # Detailed system design and data flow
├── HerSafe AI - Workflow.json       # Exported n8n workflow (AI logic)
├── .gitignore
└── README.md
```

---

## 🚧 Limitations & future work

- Prototype-stage AI classification, not a substitute for professional or legal judgment
- Support categories are generic and not yet tied to verified local organizations
- No persistent secure storage in this version

**Planned:** verified, location-aware resource directory · secure consent-based report storage · multilingual support · opt-in connection to real reporting channels

---

## 👤 Author

**Hafsa Anwar**, AI & Automation Engineer · BS Robotics & Intelligence Systems, Bahria University

[Portfolio](https://hafsaanwar.dev) · [LinkedIn](https://www.linkedin.com/in/hafsa-anwar-53b251313/) · [GitHub](https://github.com/Hafsa-Anwar65)

<div align="center">

Built for the GenAI Fellowship · 2026

</div>
