# Twilio Voice & SMS Platform

![Next.js](https://img.shields.io/badge/Next.js-15-black?style=flat-square&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Twilio](https://img.shields.io/badge/Twilio-Voice_&_SMS-F22F46?style=flat-square&logo=twilio&logoColor=white)
![WebRTC](https://img.shields.io/badge/WebRTC-Softphone-333333?style=flat-square)
![Supabase](https://img.shields.io/badge/Supabase-Postgres-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![Repo](https://img.shields.io/badge/Source-Private-orange?style=flat-square)

**A production-ready communication platform with an in-browser softphone, power dialer, mass SMS, and email — built on Twilio and Supabase.**

---

## Features

### Softphone 2.0
- In-browser calling with Twilio Voice SDK (WebRTC)
- Mute, consult transfer, and manual voicemail drop
- Real-time call status tracking and duration display

### Power Dialer
- Sequential dialing from CSV uploads or CRM queue
- Compliance gates (DNC, consent) before every call
- Attempt logging, dispositions, and agent notes
- Voicemail drop via pre-recorded messages

### Mass SMS
- Bulk messaging from CSV uploads with progress tracking
- Real-time delivery status updates
- Contact deduplication and error handling

### Email System
- Transactional emails powered by Resend SMTP
- Template management and delivery tracking

### CRM & Analytics
- Automatic call logging with notes and activity tracking
- Unified analytics combining call logs and dialer attempts
- Agent performance dashboards

## Architecture

```
┌─────────────────────────────────────────────┐
│              Next.js 15 Frontend             │
│     Softphone │ Dialer │ SMS │ Analytics     │
│         Twilio Voice SDK (WebRTC)            │
└──────────────────┬──────────────────────────┘
                   │
        ┌──────────┼──────────┐
        ▼          ▼          ▼
  ┌──────────┐ ┌────────┐ ┌────────┐
  │ API      │ │Webhooks│ │ Resend │
  │ Routes   │ │(Twilio)│ │ SMTP   │
  └────┬─────┘ └───┬────┘ └────────┘
       │            │
       ▼            ▼
  ┌──────────────────────────────────┐
  │        Supabase (Postgres)        │
  │  call_log │ dialer_attempts │ CRM │
  └──────────────────────────────────┘
```

## Tech Stack

- **Framework:** Next.js 15, React, TypeScript
- **Voice:** Twilio Programmable Voice + Voice SDK (WebRTC)
- **SMS:** Twilio Programmable Messaging
- **Email:** Resend SMTP
- **Database:** Supabase (PostgreSQL)
- **Deployment:** Vercel

## Skills Demonstrated

- WebRTC integration for browser-based telephony
- Twilio Voice SDK implementation (client + server)
- Webhook-driven event processing
- Real-time UI with streaming status updates
- Compliance engineering (DNC, consent enforcement)
- Full-stack application with multiple communication channels

---

> *This is a showcase page for a private repository. Source code available upon request for verified opportunities.*
