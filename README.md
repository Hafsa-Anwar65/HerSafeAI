<div align="center">

# 🛡️ HerSafe AI

### A GenAI powered conversational assistant for harassment reporting & support navigation

*Turning a hard conversation into a clear, safe first step.*

[![Built with n8n](https://img.shields.io/badge/Built%20with-n8n-EA4B71?style=flat-square)](https://n8n.io)
[![Powered by OpenRouter](https://img.shields.io/badge/Powered%20by-OpenRouter%20API-8A63D2?style=flat-square)](https://openrouter.ai)
[![SDG 5](https://img.shields.io/badge/SDG-5%20Gender%20Equality-FF3A21?style=flat-square)](https://sdgs.un.org/goals/goal5)

🔗 **[Live Demo](https://hersafeai.netlify.app/)** &nbsp;·&nbsp; 🎥 **[Video Walkthrough](https://youtu.be/bx4r2AGHs5Q)**

</div>

---

## ✨ Overview

**HerSafe AI** helps people describe a harassment incident in their own words
no forms, no interrogation and uses AI to:

- 🧠 Understand the narrative and extract structured incident details
- 🏷️ Classify the type of incident
- ⚠️ Assess the safety context
- 🤝 Recommend relevant categories of support
- 📝 Generate an editable, downloadable draft report

Built end-to-end with **n8n** for workflow orchestration and the **OpenRouter API**
for language understanding no custom backend required.

> Supports **SDG 5 Gender Equality**, improving access to reporting
> assistance and support resources for people experiencing harassment.

---

## 🧩 How It Works

```
User (chat widget)
      │
      ▼
n8n Chat Trigger
      │
      ▼
AI Understanding  ──▶  Structured Extraction  ──▶  Safety Assessment
      │
      ▼
Incident Classification  ──▶  Support Guidance  ──▶  Draft Report
      │
      ▼
Response to User
```

Full breakdown in [`docs/architecture.md`](docs/architecture.md).

---

## 📁 Repository Structure

```
HerSafeAI/
├── Frontend/                        # Chat widget UI (HTML + JS)
├── N8N Workflow Screenshots/        # Visual reference of the n8n workflow
├── docs/
│   └── architecture.md              # Detailed system design & data flow
├── HerSafe AI - Workflow.json       # Exported n8n workflow (AI logic)
├── .gitignore
└── README.md
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Workflow orchestration | [n8n](https://n8n.io) |
| AI reasoning | [OpenRouter API](https://openrouter.ai) |
| Frontend | HTML + JavaScript |

---

## 🔒 Privacy & Safety

- 🚫 Never asks for name, phone number, address, or ID numbers
- ✅ Every question can be skipped
- 🏷️ All AI classifications are clearly labeled as AI-generated never presented as legal or official determinations
- 🆘 If immediate danger is indicated, the flow prioritizes calm safety guidance over data collection
- 📄 The final report is a **draft** it is never submitted, filed, or sent anywhere automatically

---

## 🚧 Limitations & Future Work

- Prototype-stage AI classification not a substitute for professional or legal judgment
- Support categories are generic, not tied to verified local organizations
- No persistent secure storage in this version

**Planned:** verified local resource directory · secure consent-based storage · multilingual support · opt-in integration with real reporting channels

---

---

## 👤 Author

**Hafsa Anwar**

<div align="center">

Built for the GenAI Fellowship · 2026

</div>
