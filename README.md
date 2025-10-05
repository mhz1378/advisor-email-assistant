# Advisor Email Assistant

Automated email triage, classification, and reminders for university staff.  
Built on **n8n**, using Gmail, Google Sheets, Telegram, and OpenAI integrations.

---

## 🧭 Overview

| Phase | Name | Description |
|-------|------|--------------|
| **Phase 1** | Gmail Intake & Dedupe | Pulls new emails → normalizes fields → dedupes by threadId → logs to Google Sheets. |
| **Phase 2** | Smart Classification | Uses OpenAI LLM to classify, summarize, and assign priority with reasoning. |
| **Phase 3.1** | Reminder Hooks | Sends Telegram reminders for `Action Required` or high-priority emails (≥ 4). Optional Google Calendar event creation. |
| **Phase 3.2** | Daily Digest | At 20:00 daily, aggregates last 24 h emails, posts Telegram summary, and appends a dated log entry in Sheets. |

---

## 🧩 Files

| File | Purpose |
|------|----------|
| `advisor-email-assistant.v1.json` | Base workflow – Gmail intake → normalize → dedupe → priority scoring → Sheets logging. |
| `advisor-email-assistant.v2.json` | Phase 3.1 – Added Reminder Hooks (Telegram + optional Calendar). |
| `daily-digest.v1.json` | Phase 3.2 – Added Daily Digest (24 h filter + date logging). |

---

## 🧰 Requirements

- **n8n (self-hosted)** ≥ 1.60  
- **Google OAuth2** credentials for Gmail + Sheets  
- **Telegram Bot API** key  
- **OpenAI API key** (for GPT-4o-mini or later)

---

## 🧪 How to Use

1. Import the `.json` workflows into n8n.  
2. Connect credentials (`Uni Account`, `Main Sheets`, `Ticket Intake`).  
3. Adjust `chatId` and spreadsheet IDs if needed.  
4. Run a manual test email to verify Telegram reminders and Sheet logging.  
5. Enable both workflows once tested.

---

## 🧬 Version Log

| Version | Date | Summary |
|----------|------|----------|
| **v2** | Oct 2025 | Added Reminder Hooks with Telegram alerts + optional Calendar integration. |
| **digest-v1** | Oct 2025 | Added Daily Digest (24 h filtering + date logging). |
| **v1** | Sep 2025 | Initial base workflow with Gmail intake and dedupe. |

---

## 📦 Repo Structure

