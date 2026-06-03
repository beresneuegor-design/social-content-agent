# 📱 Social Content Agent — n8n

> Topic from Google Sheets → Groq writes LinkedIn/Telegram post → sends for approval → auto-publishes after one click. Content pipeline on autopilot.

![n8n](https://img.shields.io/badge/n8n-workflow-FF6B6B?style=flat-square)
![Groq](https://img.shields.io/badge/Groq-LLaMA%203.3%2070B-F55036?style=flat-square)
![Telegram](https://img.shields.io/badge/Telegram-Bot%20API-26A5E4?style=flat-square&logo=telegram)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-34A853?style=flat-square&logo=google-sheets)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

## ✨ What it does

Every morning the agent:
1. **Reads** next topic from Google Sheets content calendar
2. **Generates** post with Groq AI (tone, hashtags, CTA)
3. **Sends** draft to your Telegram for approval
4. **Waits** for your reply: ✅ publish / ✏️ edit / ❌ skip
5. **Posts** automatically to LinkedIn/Telegram channel after approval

## 🏗️ Architecture

```
Schedule Trigger (9:00 AM)
        │
        ▼
┌──────────────┐
│ Google Sheets │  reads next topic from calendar
└──────┬───────┘
       │
       ▼
┌──────────────┐
│   Groq AI     │  writes post: hook, body,
│               │  CTA, hashtags, emoji
└──────┬───────┘
       │
       ▼
┌──────────────┐
│   Telegram    │  sends draft + approval buttons
│   (to you)    │  ✅ Publish  ✏️ Edit  ❌ Skip
└──────┬───────┘
       │
       ▼ (on ✅)
┌──────────────┐
│  LinkedIn /   │  publishes post automatically
│  TG Channel   │
└──────────────┘
```

## 📅 Content Calendar (Google Sheets)

| Date | Topic | Tone | Platform | Status |
|------|-------|------|----------|--------|
| 2025-06-03 | AI automation for SMB | professional | LinkedIn | pending |
| 2025-06-04 | n8n vs Zapier | casual | Telegram | pending |

## 🚀 Setup

1. Import `workflow.json` into n8n
2. Add credentials: Groq API, Google Sheets OAuth2, Telegram Bot
3. Fill content calendar in Google Sheets
4. Set your Telegram chat ID for approvals
5. Activate — runs every morning at 9:00

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| Automation | n8n |
| AI Writing | Groq — LLaMA 3.3 70B |
| Calendar | Google Sheets |
| Approval | Telegram Bot API |
| Publishing | LinkedIn API / Telegram |

---
*Built by [VinteliVision](https://vintelivision.com) — AI automation for Polish SMBs.*
