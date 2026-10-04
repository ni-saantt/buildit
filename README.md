# BuildIt - The AI-Powered Full Stack Startup Builder & Co-Founder

BuildIt is a next-generation, AI-driven platform designed to act as your technical and strategic co-founder. By leveraging advanced generative AI models, BuildIt helps entrepreneurs identify problems, validate ideas, generate business models, simulate VC pitches, and build comprehensive startup plans from scratch.

---

## 🚀 Overview & What Is Happening
BuildIt transforms a simple idea or a photo of a real-world problem into a fully structured startup blueprint. 
- **Identify:** Users can upload images of industrial/operational problems or type their ideas.
- **Analyze:** The AI acts as a consultant, breaking down the root causes, financial impacts, and potential solutions.
- **Strategize:** The platform automatically generates business models, validation experiments, Minimum Viable Product (MVP) documents, and scaling strategies.
- **Fund:** Users can practice pitching to a simulated AI Venture Capitalist ("Ananya") to prepare for real-world fundraising.

---

## 🧠 AI Agents & API Architecture
BuildIt is powered by a fleet of specialized AI "Agents" operating in the backend. Each agent handles a specific domain of startup building. 

### Gemini Model Used
Across all agents, we specifically utilize the **`gemini-3.8-flash`** model via the `@google/generative-ai` SDK. This model was chosen for its rapid reasoning capabilities and multimodal (image + text) support. Our backend implements a highly resilient 3-retry loop to automatically handle Google server load spikes and ensure 100% uptime.

### Active Agents (API Routes)
1. **Problem Text Analyzer Agent** (`/api/analyze-text-problem`): Evaluates raw text descriptions of problems and suggests immediate and long-term action plans.
2. **Visual Assessment Agent** (`/api/analyze-image`): Multimodal agent that processes camera inputs/images to detect safety, maintenance, and operational inefficiencies.
3. **Market Research Agent** (`/api/analyze-competitors`): Identifies market gaps, analyzes competitors, and calculates market sizing.
4. **Business Model Agent** (`/api/generate-business-model`): Generates Lean Canvas, revenue models, and pricing strategies.
5. **Pitch Generation Agent** (`/api/generate-pitch`): Creates comprehensive pitch decks, elevator pitches, and founder narratives.
6. **VC Simulation Agent** (`/api/ananya-vc-chat`): Interactive chatbot acting as a tough, analytical venture capitalist.
7. **MVP Architect Agent** (`/api/generate-mvp-document`): Defines core features, tech stacks, and development timelines.
8. **Growth & Scaling Agent** (`/api/generate-startup-plan`): Outlines a long-term roadmap for scaling the validated startup.

---

## 🛠️ Technology Stack
- **Framework:** Next.js 14 (App Router) & React 18
- **Styling:** Tailwind CSS & Radix UI (shadcn/ui)
- **Database:** Vercel Postgres (with Schema tracking)
- **Authentication:** Custom JWT-based authentication
- **Payments & Subscriptions:** Razorpay integration (Free, Basic, and Premium tiers)
- **AI / LLM:** Google Gemini API (`@google/generative-ai`)

---

## 📁 Repository Structure

### 1. Project Source Code Folders
- **/app**: The core Next.js application router. Contains all pages, layouts, and API routes.
  - `/app/api`: The backend serverless functions (where all AI Agents live).
  - `/app/(pages)`: The frontend user interfaces (e.g., `/idea`, `/dashboard`, `/market`).
- **/components**: Reusable UI components.
  - `/components/ui`: Base design system components (shadcn/ui).
  - `/components/auth`: Registration and login forms.
- **/lib**: Core utilities and integrations.
  - `auth.ts`: Authentication logic.
  - `razorpay.ts`: Payment gateway configuration.
  - `db/schema.ts`: Database structure.

### 2. Prompt Files & AI Configurations
- **/app/api/.../route.ts**: All system prompts, few-shot examples, and JSON structure schemas are housed directly inside the respective agent's API route file to ensure tight coupling with the execution logic.
- **AI Documentation (.md)**: Files like `AI_PROBLEM_IDENTIFICATION.md` and `AI_COFOUNDER_FEATURES.md` dictate the design philosophy and expected outputs of the AI system.

### 3. Configuration Files
- **`package.json`**: Defines all dependencies, scripts, and project metadata.
- **`next.config.mjs`**: Next.js compiler and build configuration.
- **`tailwind.config` / `postcss.config.mjs`**: Styling and theme configurations.
- **`tsconfig.json`**: TypeScript strict typing rules.
- **`components.json`**: UI component registry configuration.

---

## 🔑 Environment Variables & Setup
To run this project locally, you must create a `.env.local` file in the root directory. This file is ignored by Git for security reasons.

Required variables:
```env
# Google Gemini API
GOOGLE_GEMINI_API_KEY=your_gemini_api_key

# Authentication
JWT_SECRET=your_secure_jwt_secret

# Application
NEXT_PUBLIC_APP_URL=http://localhost:3000

# Razorpay (Optional - for subscriptions)
NEXT_PUBLIC_RAZORPAY_KEY_ID=your_public_key
RAZORPAY_KEY_SECRET=your_secret_key
```

## 💻 Running the Project
1. Install dependencies:
   ```bash
   npm install
   ```
2. Start the development server:
   ```bash
   npm run dev
   ```
3. Open [http://localhost:3000](http://localhost:3000) in your browser.
