## 🚀 Project Overview

A [Next.js](https://nextjs.org) AI SaaS app, bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).
Includes Tailwind-based UI components, tRPC, Prisma, and a serverless PostgreSQL backend (Neon).

---

## 📦 Prerequisites

* **Node.js** ≥ 16
* **Package Manager**: npm, Yarn, pnpm, or Bun
* **Git** (for version control)
* **PostgreSQL** (remote on Neon or local)

---

## 🔧 Getting Started

1. **Clone the repo**

   ```bash
   git clone https://github.com/your-username/your-repo.git
   cd your-repo
   ```

2. **Install dependencies**

   ```bash
   npm install
   # or
   yarn
   # or
   pnpm install
   # or
   bun install
   ```

3. **Configure environment**
   Copy `.env.example` → `.env` and set your database URL and any other secrets.

4. **Run the development server**

   ```bash
   npm run dev
   # or
   yarn dev
   # or
   pnpm dev
   # or
   bun dev
   ```

   Open [http://localhost:3000](http://localhost:3000) in your browser. The app will hot-reload as you edit.

---

## 🗂 Project Structure

```
├── app/                  # Next.js App Router pages & layouts
│   ├── page.tsx          # Home page
│   └── ...               
├── prisma/               # Prisma schema & migrations
│   ├── schema.prisma     
│   └── migrations/       
├── src/
│   ├── components/       # Reusable UI components (ShadCN/UI)
│   ├── trpc/             # tRPC router definitions & client
│   └── styles/           # Global styles & Tailwind config
├── public/               # Static assets (fonts, images)
├── README.md             # ← You are here
└── package.json          
```

---

## 🎨 Fonts & Styling

* Uses Next.js’s [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts)
* Loads the **Geist** font automatically for optimized performance
* Styled with **Tailwind CSS** and [ShadCN/UI](https://ui.shadcn.com/)

---

## 🗄️ Database Setup (Prisma + Neon)

1. **Initialize Prisma**

   ```bash
   npx prisma init
   ```

2. **Configure your schema** in `prisma/schema.prisma`

3. **Generate Prisma client**

   ```bash
   npx prisma generate
   ```

4. **Run migrations**

   ```bash
   npx prisma migrate dev --name init
   ```

5. **(Optional) Reset for development**
   Deletes all data & migrations—only do this locally:

   ```bash
   npx prisma migrate reset
   ```

6. **Use Neon for production**

   * Serverless, auto-scaling Postgres
   * Separate compute & storage for cost efficiency

---

## 🔌 tRPC Integration

* **Server:** define your router in `src/trpc/router.ts`
* **Client:** generate `trpc` hooks in `src/trpc/client.ts`
* **Using queries/mutations:**

  ```tsx
  const { data } = trpc.myRouter.myQuery.useQuery({ /* input */ }, { suspense: true });
  ```
* Supports **prefetching**, **SSR**, and **decoration** via React Query under the hood.

---

## ⚙️ Deployment

We recommend deploying on **Vercel**:

1. Push your repo to GitHub
2. On [vercel.com](https://vercel.com), “Import Project” → select your repo
3. Set your environment variables (e.g. `DATABASE_URL`) in Vercel dashboard
4. Click **Deploy**

For more details, see Next.js’s [deployment docs](https://nextjs.org/docs/app/building-your-application/deploying).

---

## 🤝 Contributing

1. **Fork** the repo
2. Create a **feature/bugfix** branch
3. Open a **Pull Request** against `main`
4. Ensure CI passes & add descriptive commit messages
5. We’ll review & merge—thank you!

---

## 📜 License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for details.


## Setup 01

Setup Next.js Project
1. confirm environment
2. Node.js
3. npm

- Verifying files and versions
- Setup ShadCN/UI
- Creating a GitHub repository

## Database 02

1. PostgreSQL database (Neon - cloud-native, serverless Postgres platform that separates storage and compute, auto-scales on demand)

2. Setup Primsa (ORM - Object-Relational Mapper - lets you define your schema declaratively and then map it to a DB)
3. In order to run, `npx prisma init`

4. generate prisma files `npx prisma generate`
- Add schema
- Basic migrations
- Database studio
- Database reset (FOR DEVELOPMENT - delete migrations,seed, and remove any call instance of the prisma db)

5. Push to GitHub
- Branch out
- Open a PR
- Review and Merge


## TRPC Setup 03

1. setup tRPC
- Experiement with client component
- Experiement with server component
- Preview prefetching

2. Push to GitHub
- Branch out
- Open a PR
- Review and Merge

## Background Jobs 04

1. Normal Task
- User clicks 'Login'
- Sends request
- Instant response (success or fail)


2. Long running task example
- User clicks 'Generate summary'
- Sends network request
- Backend generates summary (well over 30 seconds)
- User waits
- RISK: timeout / tab closed / connection timeout
- User might never get a result

3. Long running task example (WITH BACKGROUND JOB)
- User clicks 'Generate summary'
- Sends network request
- Backend generates summary (well over 30 seconds)
- Summary is being generated || Background job runs
- User can close tab || User notified when job completes

4. Setup Inngest
- Create the first function
- Explore Inngest Development Server
- Trigger a background job from Next.js

5. Push to GitHub
- Branch out
- Open a PR
- Review and Merge

## AI Jobs 05

1. Choose your AI provider

- OpenAI 
  - best choice 
  - gpt-4.1
  - normal rate limit, fast reset 

- Anthropic (Claude) 
  - claude-sonnet-3.5
  - claude-sonnet-4
  - strict rate limit, 24h+ reset 

- Grok (xAI) 
  - Unsure 

- Gemini (Google) 
  - Not good for calling tools 



## 