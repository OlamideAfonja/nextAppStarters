# Acme Dashboard — Next.js Learn Course

A full-stack dashboard application built by following the official [Next.js Learn Course](https://nextjs.org/learn/dashboard-app) by Vercel. This project covers core Next.js App Router concepts including data fetching, streaming, authentication, and server actions.

---

## 🚀 Tech Stack

- **Framework:** [Next.js 14](https://nextjs.org/) (App Router)
- **Language:** TypeScript
- **Database:** PostgreSQL via [Supabase](https://supabase.com/) (connected through Vercel Marketplace)
- **ORM/Query:** `postgres.js`
- **Styling:** Tailwind CSS
- **Auth:** NextAuth.js
- **Validation:** Zod
- **Package Manager:** pnpm
- **Deployment:** Vercel

---

## 📦 Features

- 📊 Dashboard with revenue chart, latest invoices, and summary cards
- 🧾 Full invoices CRUD — create, read, update, delete
- 👥 Customers listing
- 🔐 Authentication with login/logout
- ⚡ Streaming with Suspense for improved performance
- 🔍 Search and pagination
- ♿ Accessible forms with error handling via `useActionState`

---

## 🛠️ Getting Started

### Prerequisites

- Node.js 18+
- pnpm (`npm install -g pnpm`)
- A [Supabase](https://supabase.com/) account

### Installation

```bash
# Clone the repository
git clone https://github.com/OlamideAfonja/nextAppStarters.git
cd nextjs-dashboard

# Install dependencies
pnpm install
```

### Environment Variables

Create a `.env.local` file in the root directory:

```env
# Supabase pooled connection — port 6543 (for app queries)
POSTGRES_URL="postgresql://postgres:[password]@aws-0-us-east-1.pooler.supabase.com:6543/postgres?sslmode=require&pgbouncer=true&connection_limit=1"

# Supabase direct connection — port 5432 (for migrations/seeding)
POSTGRES_PRISMA_URL="postgresql://postgres:[password]@db.[project-ref].supabase.co:5432/postgres?sslmode=require"

DIRECT_URL="postgresql://postgres:[password]@db.[project-ref].supabase.co:5432/postgres?sslmode=require"

# NextAuth
AUTH_SECRET="your-auth-secret"
AUTH_URL="http://localhost:3000"
```

> ⚠️ **Important:** Never commit `.env.local` to GitHub. Make sure it is listed in `.gitignore`.

### Seed the Database

Start the dev server and visit the seed endpoint in your browser:

```bash
pnpm run dev
```

Then open: [http://localhost:3000/seed](http://localhost:3000/seed)

You should see: `{ "message": "Database seeded successfully" }`

> **Note:** If you encounter a `PostgresError code 26000` (FetchPreparedStatement), make sure your `postgres()` connection includes `prepare: false` to disable prepared statements — required when using Supabase's PgBouncer pooler.

### Run Locally

```bash
pnpm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 🗂️ Project Structure

```
app/
├── dashboard/
│   ├── page.tsx          # Dashboard home
│   ├── layout.tsx        # Dashboard layout
│   ├── loading.tsx       # Streaming loading UI
│   ├── customers/        # Customers page
│   └── invoices/
│       ├── page.tsx      # Invoices list
│       ├── create/       # Create invoice
│       └── [id]/edit/    # Edit invoice
├── lib/
│   ├── actions.ts        # Server actions (create, update, delete)
│   ├── data.ts           # Data fetching functions
│   └── placeholder-data.ts
├── seed/
│   └── route.ts          # Database seeding endpoint
└── ui/
    ├── dashboard/        # Dashboard components
    ├── invoices/         # Invoice form components
    └── customers/        # Customer components
```

---

## ⚠️ Known Gotchas

| Issue | Fix |
|-------|-----|
| `PostgresError code 26000` | Add `prepare: false` to your `postgres()` connection |
| Vercel Supabase URLs have `&supa=base-pooler.x` | Copy URLs directly from Supabase dashboard instead |
| `/seed` route redirected to homepage | Exclude `/seed` from auth middleware matcher |
| `updateInvoiceWithId is not defined` | Use `formAction` (from `useActionState`) in `<form action={}>` |

---

## 📚 Course Progress

Built through the official Next.js Learn Course — 15 chapters covering:

- App Router & file-based routing
- CSS & Tailwind styling
- Fonts & image optimisation
- Layouts & pages
- Database setup & seeding
- Data fetching
- Static & dynamic rendering
- Streaming
- Search & pagination
- Mutating data with Server Actions
- Error handling
- Accessibility & form validation
- Authentication
- Metadata

---

## 📄 License

This project is for learning purposes, based on the [Next.js Learn Course](https://nextjs.org/learn) by Vercel.
