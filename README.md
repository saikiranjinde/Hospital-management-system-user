# MediCare+ Patient Portal — README

## Overview

The Patient Portal (`user.html`) is the front-facing interface for patients. It is a single-file HTML application deployed on **Vercel** that communicates with the backend API.

---

## Features

### 🏠 Homepage
- Animated hero section with hospital branding
- Real-time doctor availability listing
- Dynamic **Offers & Health Packages** section (managed by admin)
- Feature highlights (AI remedies, appointments, notifications)

### 🩺 Doctor Listing
- Live grid of all active doctors fetched from the backend
- Shows specialization, qualifications, experience, consultation fee
- **Available Today** / **Unavailable Today** status per doctor
- Tap any doctor card to auto-fill the booking form

### 📅 Book Appointment
- Patients must be logged in to book
- Select doctor, date, time, describe symptoms
- On submission: instant confirmation + AI home remedy suggestions

### 🤖 AI Home Remedy Suggestions (Gemini 2.5 Flash)
- After booking, AI analyzes symptoms and suggests home remedies
- Powered by Google Gemini 2.5 Flash
- **Strictly home remedies only — no medicines suggested**
- If AI is unavailable, pre-written remedies are shown as fallback
- Results are saved and visible in My Appointments

### 📋 My Appointments
- View all past and upcoming appointments
- See status: Pending / Confirmed / Rescheduled / Completed / Cancelled
- View doctor notes added by admin
- Access AI remedy suggestions per booking
- Data cached locally so it loads instantly on revisit

### 🔔 Notifications
- Bell icon in navbar shows unread count
- Notifications for booking events, confirmations, admin announcements
- Mark as read individually or all at once

### 👤 User Account
- Register with name, email, phone, age, blood group
- Login / Logout via dropdown on user avatar
- Session stored in browser (7-day token)

---

## Technology Stack

| Layer | Technology |
|---|---|
| Language | HTML, CSS, JavaScript (vanilla) |
| Fonts | Syne, Instrument Sans (Google Fonts) |
| Icons | Font Awesome 6.5 |
| Hosting | Vercel |
| API | Connects to Express backend on Render |

---

## Configuration

Open `user.html` and update the **first line** of the `<script>` block:

```js
const BACKEND_URL = "https://your-render-app.onrender.com";
```

Replace with your actual Render deployment URL. This is the **only change** needed after deploying the backend.

---

## Deployment

1. Push `user.html` to your GitHub repository
2. Connect the repo to **Vercel** (vercel.com)
3. Vercel deploys automatically — no build step needed
4. The file is served as a static HTML page

---

## Pages & Navigation

| Section | How to reach |
|---|---|
| Home / Hero | Scroll to top or click MediCare+ logo |
| Doctors | Navbar → Doctors |
| Book Appointment | Navbar → Book / click any doctor card |
| My Appointments | Navbar → My Appointments |
| Login / Register | Navbar → Login button |

---

## Mobile Support

Fully responsive for all screen sizes:
- Navbar collapses on mobile (username hidden, dropdown retained)
- Doctor grid shows 2 columns on phones
- Booking form stacks to single column
- All modals fit within mobile viewport

---

## Notes

- The offers section is **hidden** if no active offers exist in the database
- AI suggestions are saved per booking and persist across sessions
- All API calls automatically show a clear error if the backend URL is wrong
- The hospital loading animation plays once on every page open
