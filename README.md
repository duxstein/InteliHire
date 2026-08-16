# Intellihire

**Intellihire** is an AI-powered mock interview platform that helps candidates practice for real job interviews. Enter a job role, description, and experience level — Intellihire generates tailored questions with Google Gemini, records your spoken answers, and delivers instant AI feedback with ratings.

![Dashboard](./public/image.png)

## Features

- **AI-generated interviews** — Gemini creates role-specific questions and model answers from your job title, description, and years of experience.
- **Voice & video practice** — Record answers with speech-to-text transcription and a live webcam feed for a realistic interview feel.
- **Instant feedback** — Each answer is evaluated by AI with a score and concise improvement suggestions.
- **Session history** — Review past mock interviews and detailed feedback from your dashboard.
- **Secure auth** — Sign in and manage sessions with Clerk.

## Tech Stack

| Layer | Technologies |
| --- | --- |
| Frontend | Next.js 15 (App Router), React 19, TypeScript, Tailwind CSS |
| AI | Google Gemini API |
| Database | PostgreSQL (Neon), Drizzle ORM |
| Auth | Clerk |

## Architecture

```mermaid
graph TD
    subgraph Client
        User[Candidate]
        Browser[Next.js App]
    end

    subgraph External
        Gemini[Google Gemini API]
        Clerk[Clerk Auth]
    end

    subgraph Data
        DB[(PostgreSQL)]
    end

    User --> Browser
    Browser -->|Authenticate| Clerk
    Browser -->|Generate questions & feedback| Gemini
    Browser -->|Server Actions| DB
```

Server-side logic lives in Next.js Server Actions (`app/actions/mockInterview.ts`) for creating interviews, saving answers, and fetching feedback — no separate REST API layer.

## Getting Started

### Prerequisites

- Node.js 18+
- PostgreSQL database ([Neon](https://neon.tech) recommended)
- [Clerk](https://clerk.com) account
- [Google AI Studio](https://aistudio.google.com) API key for Gemini

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/duxstein/InteliHire.git
cd InteliHire
```

2. **Install dependencies**

```bash
npm install
```

3. **Configure environment variables**

Create a `.env.local` file in the project root:

```env
# Database
DATABASE_URL=postgresql://user:password@host:port/db

# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_...
CLERK_SECRET_KEY=sk_test_...

# Google Gemini
NEXT_PUBLIC_GEMINI_API_KEY=your_gemini_api_key

# Interview settings
NEXT_PUBLIC_INTERVIEW_QUESTION_COUNT=5
NEXT_PUBLIC_QUESTION_NOTE=Take your time and answer clearly.
NEXT_PUBLIC_INFORMATION=Read each question carefully before recording your answer.
```

4. **Push the database schema**

```bash
npm run db:push
```

5. **Start the development server**

```bash
npm run dev
```

Open [http://127.0.0.1:3000](http://127.0.0.1:3000) in your browser.

### Other scripts

| Command | Description |
| --- | --- |
| `npm run build` | Production build |
| `npm run start` | Run production server |
| `npm run lint` | Run ESLint |
| `npm run db:studio` | Open Drizzle Studio |

## Project Structure

```
app/
├── (auth)/              # Clerk sign-in & sign-up pages
├── actions/             # Server Actions (interviews, answers, feedback)
├── dashboard/           # Main app — interview list, session, feedback
└── page.tsx             # Landing page
components/              # Shared UI components
utils/
├── db.ts                # Neon + Drizzle client
├── schema.ts            # Database tables
└── GeminiAIModal.ts     # Gemini chat session
```

## Contributing

Contributions are welcome. Fork the repo, create a feature branch, and open a pull request.

## License

This project is private. All rights reserved.
