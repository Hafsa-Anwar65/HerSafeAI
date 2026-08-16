# 🏗️ Architecture: HerSafe AI

## System Overview

HerSafe AI is built as a conversational workflow using **n8n** for
orchestration and the **OpenRouter API** for language understanding,
classification, and guidance generation. The frontend is a lightweight
HTML/JS chat widget that sends user messages to the n8n Chat Trigger and
displays the AI's responses.

## End-to-End Flow

```
┌─────────────────────────────┐
│   User (browser chat widget) │
└──────────────┬───────────────┘
               │
               ▼
┌─────────────────────────────┐
│   n8n Chat Trigger           │  Receives the incoming message
└──────────────┬───────────────┘
               │
               ▼
┌─────────────────────────────┐
│   Normalize Input            │  Prepares message + conversation context
└──────────────┬───────────────┘
               │
               ▼
┌─────────────────────────────┐
│   AI Understanding           │  The LLM (via OpenRouter) interprets the narrative and
│                               │  extracts structured incident info:
│                               │  category, description, date/time,
│                               │  context, ongoing status, safety
│                               │  concern, support preference
└──────────────┬───────────────┘
               │
               ▼
┌─────────────────────────────┐
│   Parse + Validate           │  Checks the AI's JSON output; falls back
│                               │  safely if malformed
└──────────────┬───────────────┘
               │
               ▼
┌─────────────────────────────┐
│   Safety Assessment          │  Flags High / Moderate / Low-Unclear
│                               │  concern, based only on what the user
│                               │  has stated. High-risk cases short-
│                               │  circuit into immediate safety guidance
└──────────────┬───────────────┘
               │
               ▼
┌─────────────────────────────┐
│   Incident Classification    │  Categorizes the incident (e.g. online
│                               │  harassment, workplace harassment,
│                               │  stalking, etc.)
└──────────────┬───────────────┘
               │
               ▼
┌─────────────────────────────┐
│   Support & Guidance         │  Generates next-step suggestions and
│                               │  support categories — no invented
│                               │  org names or numbers
└──────────────┬───────────────┘
               │
               ▼
┌─────────────────────────────┐
│   Report Generator           │  Compiles an editable, clearly-labeled
│                               │  AI-generated draft incident report
└──────────────┬───────────────┘
               │
               ▼
┌─────────────────────────────┐
│   Response to User           │  Returned through the chat widget
└─────────────────────────────┘
```

## Design Rationale

| Decision | Why |
|---|---|
| **n8n** for orchestration | Build and iterate on AI logic visually, without standing up custom backend infrastructure |
| **OpenRouter API** for reasoning | Handles free-text understanding, classification, and empathetic guidance far more flexible than keyword-matching or static forms |
| **Structured JSON extraction** | Keeps AI output predictable enough to route reliably through classification and safety logic |
| **No database / persistent storage** | Conversation state lives only for the session, minimizing data retention and privacy risk |

## Privacy & Safety Design

- No fields for name, phone number, address, or ID numbers are ever requested
- Users can skip any question
- All classifications and risk assessments are explicitly labeled as
  AI-generated, based only on the information provided never presented
  as legal or official determinations
- If immediate danger is indicated, the workflow prioritizes calm safety
  guidance over continued data collection
- The final report is clearly marked as an editable **draft** never
  described as submitted, filed, or sent to any authority or organization

## Limitations

- This is a prototype; classification and safety assessment are
  AI-generated and not a substitute for professional or legal judgment
- Support resource categories are generic and not tied to verified local
  organizations users are told to confirm details locally
- No persistent, secure storage is implemented in this version

## Future Improvements

- Verified, location-aware support resource directory
- Secure, consent-based persistent report storage
- Multilingual support
- Optional (opt-in) connection to real reporting channels with proper safeguards

---

## 👤 Author

**Hafsa Anwar**
