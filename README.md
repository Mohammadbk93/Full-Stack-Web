#1. Moveit Website 🚚

> A full-stack moving company web application built with Flask, PostgreSQL, and OpenAI — featuring AI-powered quote generation, a customer chatbot, user authentication, and an admin panel.

**Live Demo:** [moveit-website.onrender.com](https://moveit-website.onrender.com)

---

## About

Move it is an immaginary modern moving company platform built for customers in Italy. It allows users to register, request personalised AI-generated moving quotes, and interact with an intelligent chatbot assistant. Company admins can manage all users and quotes through a dedicated admin panel.

---

## Features

### Customer-Facing
- **AI Quote Generator** — Enter move details and receive a funny, personalised quote powered by GPT-4o-mini
- **MoverBot Chatbot** — Floating assistant available on every page, answers moving-related questions in real time
- **User Authentication** — Register, login, forgot/reset password, remember me
- **Dashboard** — View all personal quotes with status badges (Pending / Confirmed / Completed)
- **Quote Detail Page** — Printable and shareable view of each quote
- **Profile Management** — Update email, change password, delete account
- **Contact Form** — Sends emails directly via Gmail SMTP

### Homepage Sections
- Hero with animated fade-in
- Why Move With Us (features)
- Pricing tiers (Basic / Standard / Premium)
- Customer testimonials
- FAQ accordion
- Image carousel

### Admin Panel (`/admin/`)
- Dashboard with stat cards and recent activity
- User management — view all users, grant/revoke admin, delete accounts
- Quote management — view all quotes, update status inline, delete
- Access protected by `@admin_required` decorator
<img width="1280" height="670" alt="2026-05-29 22 02 07" src="https://github.com/user-attachments/assets/51259346-5575-4578-b554-042a61a69c0d" />



### Technical
- CSRF protection on all forms and API calls
- Rate limiting on AI endpoints (chat: 10/min · quotes: 5/min)
- Custom error pages (403, 404, 429, 500)
- Structured logging with timestamps
- Flask-Migrate for database migrations
- Toast notifications replacing browser alerts
- Hero animations

---

## Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | Python 3.11, Flask 2.3 |
| **Database** | PostgreSQL (production), SQLite (fallback) |
| **ORM** | Flask-SQLAlchemy + Flask-Migrate |
| **Authentication** | Flask-Login + Werkzeug password hashing |
| **AI** | OpenAI API — `gpt-4o-mini` |
| **Security** | Flask-WTF (CSRF), Flask-Limiter (rate limiting) |
| **Email** | Python smtplib + Gmail SMTP |
| **Frontend** | Bootstrap 5.3, Bootstrap Icons, vanilla JS |
| **Containerisation** | Docker + Docker Compose |
| **Deployment** | Render (Web Service + Managed PostgreSQL) |

---

## Project Structure

```
moveit-website/
├── main.py               # App factory, error handlers, logging
├── config.py             # Config class, environment variables
├── routes.py             # Main Blueprint — all customer routes
├── admin.py              # Admin Blueprint — /admin/ routes
├── models.py             # SQLAlchemy models (User, MoveQuote)
├── extensions.py         # Flask-Limiter instance
├── Dockerfile            # Python 3.10-slim container
├── docker-compose.yml    # Web + PostgreSQL services
├── Procfile              # Render deployment command
├── runtime.txt           # Python 3.11.9
├── requirements.txt      # Pinned dependencies
├── migrations/           # Flask-Migrate version history
├── static/
│   ├── style.css
│   └── js/
│       └── chat.js       # MoverBot chat widget
└── templates/
    ├── base.html          # Shared layout (navbar, footer, chat widget)
    ├── index.html         # Homepage
    ├── login.html
    ├── register.html
    ├── forgot_password.html
    ├── reset_password.html
    ├── dashboard.html
    ├── profile.html
    ├── quote_detail.html
    ├── 403.html / 404.html / 429.html / 500.html
    └── admin/
        ├── base.html      # Admin sidebar layout
        ├── dashboard.html
        ├── users.html
        └── quotes.html
```
---

### Grant Admin Access (production)

---

## Rate Limits

| Endpoint | Limit |
|---|---|
| `POST /api/chat` | 10 per minute / 50 per day |
| `POST /get-quote` | 5 per minute / 20 per day |

---

## Screenshots

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/c8697647-6a2b-4d3c-a590-e356618eeb15" width="300"/></td>
    <td><img src="https://github.com/user-attachments/assets/b6f24848-da5e-48b1-8da8-0e34f6b5c940" width="300"/></td>
    <td><img src="https://github.com/user-attachments/assets/d1b21ded-03cb-4a6e-afb4-7b551d579dbd" width="300"/></td>
  </tr>
</table>

---

