<a name="readme-top"></a>

<br />
<div align="center">
  <a href="https://github.com/priyanshubh/PrepBot">
    <img src="https://cdn-icons-png.flaticon.com/512/4712/4712035.png" alt="PrepBot Logo" width="80" height="80">
  </a>

  <h3 align="center">PrepBot</h3>

  <p align="center">
    AI-Powered Mock Interview Platform
    <br />
    <a href="https://prepbot-pb.vercel.app"><strong>View Demo »</strong></a>
    <br />
    <br />
    <a href="https://github.com/priyanshubh/PrepBot">View Code</a>
    ·
    <a href="https://github.com/priyanshubh/PrepBot/issues">Report Bug</a>
    ·
    <a href="https://github.com/priyanshubh/PrepBot/issues">Request Feature</a>
  </p>
</div>

<div align="center">
  <img src="https://img.shields.io/badge/Next.js-black?style=for-the-badge&logo=next.js&logoColor=white" alt="Next.js" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Gemini_AI-8E75B2?style=for-the-badge&logo=googlebard&logoColor=white" alt="Gemini AI" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Clerk-6C47FF?style=for-the-badge&logo=clerk&logoColor=white" alt="Clerk Auth" />
  <img src="https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=for-the-badge&logo=drizzle&logoColor=black" alt="Drizzle ORM" />
</div>

<br />

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#-about-the-project">About The Project</a></li>
    <li><a href="#-key-features">Key Features</a></li>
    <li><a href="#-tech-stack">Tech Stack</a></li>
    <li><a href="#-architecture">Architecture</a></li>
    <li><a href="#-getting-started">Getting Started</a></li>
    <li><a href="#-contributing">Contributing</a></li>
    <li><a href="#-contact">Contact</a></li>
  </ol>
</details>

---

## 🤖 About The Project

**PrepBot** is an advanced AI-driven mock interview platform designed to help candidates prepare for real-world job interviews. Leveraging the power of **Google's Gemini API**, PrepBot generates dynamic, role-specific questions and provides detailed, AI-powered feedback on performance.

The platform supports **100+ unique role-based sessions**, featuring real-time video, text-to-speech capabilities, and adaptive difficulty scaling to create a personalized and rigorous interview environment.

<div align="center">
  <img src="./public/image.png" alt="Dashboard" />
</div>

---

## 🔥 Key Features

- **🧠 AI-Powered Intelligence**
  Integrated **Google Gemini API** to dynamically generate context-aware interview questions and deliver detailed performance analysis with improvement recommendations.

- **🎯 Role-Based Sessions**
  Supports over **100 unique roles**, tailoring the interview context and technical depth to the specific job description selected by the user.

- **📹 Real-Time Interaction**
  Features **real-time video** processing and **text-to-speech** functionality to simulate a realistic face-to-face interview experience.

- **⚖️ Adaptive Difficulty**
  The system automatically scales the difficulty of questions based on the candidate's responses, ensuring a personalized learning curve.

- **🔐 Secure Authentication**
  Implemented **Clerk** for robust and secure user authentication and session management.

- **💾 Scalable Data Architecture**
  Designed with **Drizzle ORM** and **PostgreSQL**, capable of managing interview data and history for **200+ users** efficiently.

---

## ⚙️ Tech Stack

| Category | Technology | Description |
| :--- | :--- | :--- |
| **Frontend** | <img src="https://img.shields.io/badge/Next.js-000000?style=flat&logo=next.js&logoColor=white"/> <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white"/> <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat&logo=tailwind-css&logoColor=white"/> | Next.js 14 App Router for framework, styled with Tailwind CSS. |
| **AI Engine** | <img src="https://img.shields.io/badge/Gemini_API-8E75B2?style=flat&logo=googlebard&logoColor=white"/> | Google Gemini for generating questions and analyzing responses. |
| **Backend & DB** | <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white"/> <img src="https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=flat&logo=drizzle&logoColor=black"/> | PostgreSQL database managed via Drizzle ORM for type-safe queries. |
| **Auth** | <img src="https://img.shields.io/badge/Clerk-6C47FF?style=flat&logo=clerk&logoColor=white"/> | Complete user management and authentication suite. |

---

## 🏗 Architecture

```mermaid
graph TD
    subgraph Client
        User[User / Candidate]
        Browser[Next.js Frontend]
    end

    subgraph AI Services
        Gemini[Google Gemini API]
    end

    subgraph Backend Services
        Clerk[Clerk Auth]
        DB[PostgreSQL Database]
    end

    User -->|Start Session| Browser
    Browser -->|Auth Request| Clerk
    Browser -->|Fetch Questions| Gemini
    Gemini -->|Generated Content| Browser
    Browser -->|Save Progress| DB
    Browser -->|Submit Answer| Gemini
    Gemini -->|Feedback & Rating| Browser

```
---

## ⚡ API Design

PrepBot utilizes Next.js Server Actions and API routes. Key endpoints include:

| Endpoint | Method | Description |
| --- | --- | --- |
| `/api/generate-questions` | `POST` | Generates interview questions based on role & difficulty using Gemini. |
| `/api/submit-answer` | `POST` | Analyzes user answer (audio/text) and returns feedback. |
| `/api/save-result` | `POST` | Saves the interview session data to PostgreSQL via Drizzle. |
| `/api/user/history` | `GET` | Retrieves past interview performance for the logged-in user. |

---

## 🧰 Getting Started

Follow these steps to set up the project locally.

### Prerequisites

* **Node.js** (v18+)
* **PostgreSQL Database** (e.g., NeonDB, Supabase, or Local)
* **Clerk Account** (for Auth keys)
* **Google Cloud Console** (for Gemini API Key)

### Installation

1. **Clone the repository**
```bash
git clone [https://github.com/priyanshubh/PrepBot.git](https://github.com/priyanshubh/PrepBot.git)
cd PrepBot

```


2. **Install dependencies**
```bash
npm install
# or
yarn install

```


3. **Environment Variables**
Create a `.env.local` file and add the following:
```env
# Database
DATABASE_URL=postgresql://user:password@host:port/db

# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_...
CLERK_SECRET_KEY=sk_test_...

# Google Gemini AI
NEXT_PUBLIC_GEMINI_API_KEY=your_gemini_api_key

```


4. **Database Migration (Drizzle)**
```bash
npm run db:push
# or
npx drizzle-kit push:pg

```


5. **Run the application**
```bash
npm run dev

```



---

## 🔧 Contributing

Contributions are welcome!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/NewFeature`)
3. Commit your Changes (`git commit -m 'Add NewFeature'`)
4. Push to the Branch (`git push origin feature/NewFeature`)
5. Open a Pull Request

---

## 🚀 Follow Me
<div align="center">
  <a href="https://github.com/priyanshubh">
    <img src="https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  </a>
  <a href="https://linkedin.com/in/priyanshu-bharti">
    <img src="https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  <a href="https://priyanshubharti.vercel.app">
    <img src="https://img.shields.io/badge/Portfolio-%23000000.svg?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" />
  </a>
</div>

<br />
<p align="center">Built with ❤️ by <a href="https://www.google.com/search?q=https://github.com/priyanshubh">Priyanshu Bharti</a></p>

```

```#   I n t e l i H i r e  
 