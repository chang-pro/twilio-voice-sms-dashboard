# Twilio Voice & SMS Platform

![Next.js](https://img.shields.io/badge/Next.js-15-black?style=flat-square&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Twilio](https://img.shields.io/badge/Twilio-Voice_&_SMS-F22F46?style=flat-square&logo=twilio&logoColor=white)
![WebRTC](https://img.shields.io/badge/WebRTC-Softphone-333333?style=flat-square)
![Supabase](https://img.shields.io/badge/Supabase-Postgres-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![Live](https://img.shields.io/badge/Powers-TechHelpFL.com-brightgreen?style=flat-square)
![Repo](https://img.shields.io/badge/Source-Private-orange?style=flat-square)

**I built a full communication platform — softphone, power dialer, mass SMS, and email — all running in the browser.** This is the system behind [TechHelpFL.com](https://techhelpfl.com), handling real client calls and outreach.

---

## Why This Is Hard

Twilio gives you APIs. It doesn't give you a product. I had to build:
- **A real softphone in the browser** — WebRTC audio, call state management, oall transfer, voicemail drop. This isn't a "click to call" button — it's a full phone replacement.
- **A power dialer that doesn't get you sued** — every call has to pass DNC checks and consent verification before it dials. Miss one and you're looking at TCPA fines.
- **Mass SMS that actually delivers** — rate limiting, delivery tracking, error handling, deduplication. Blasting 10,000 messages through Twilio is easy. Making sure they arrive is the hard part.

## What I Built

### Softphone 2.0
- Full in-browser calling via **Twilio Voice SDK (WebRTC)** — no phone hardware needed
- **Mute, consult transfer, and manual voicemail drop** during live calls
- Real-time call status display (Connecting → Ringing → In Call → Ended)
- Call duration tracking and automatic logging to the CRM
- Works across Chrome, Firefox, and Edge

### Power Dialer
- Feeds from CSV uploads or CRM queue
- **Compliance gates before every call** — DNC list check, consent verification, suppression list
- Automatic attempt logging with dispositions (answered, voicemail, no answer, bad number)
- Agent notes per call, callback scheduling
- Voicemail drop via pre-recorded messages — agents don't wait for the beep

### Mass SMS Engine
- Bulk messaging from CSV uploads with real-time progress tracking
- Delivery status updates per message (queued → sent → delivered → failed)
- Contact deduplication and error handling
- Character count enforcement (160 char limit for single-segment SMS)

### Email System
- Transactional emails via **Resend SMTP**
- Template management and delivery tracking

### CRM & Analytics
- Automatic call logging with notes, recordings, and activity tracking
- Unified analytics combining `call_log` + `dialer_attempts` for agent performance
- Dashboard with call volume, connect rates, and average call duration per agent

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

`Next.js 15` · `TypeScript` · `Twilio Voice SDK` · `Twilio Programmable SMS` · `WebRTC` · `Supabase` · `Resend SMTP` · `Vercel`

---

> *Closed source — powers [TechHelpFL.com](https://techhelpfl.com). Source code available for serious inquiries.*
