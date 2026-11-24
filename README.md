# whatsapp-ai-coach-and-cbt-simulator-for-waec-and-jamb

Build a WhatsApp-first AI Exam Coach and CBT Simulator for WAEC and JAMB students.
Since you are a developer, you can build the core engine in 2 to 3 weeks with minimal upfront cost by leveraging the tools you were already exploring—embeddings and vector search—to ensure your AI tutor never hallucinates answers.

1. System Architecture & Tech Stack

To keep infrastructure costs low while supporting 20,000+ weekly active users, build a lightweight, event-driven architecture:
• Frontend / Interface: WhatsApp Cloud API (via Meta directly to avoid third-party markup) + a ultra-lightweight Progressive Web App (PWA) (built with Next.js or plain HTML/HTMX) specifically for timed 40-question CBT mock exams where a timer and full screen matter.
• Backend: Python (FastAPI) or Node.js (Express/Hono) hosted on a single VPS (DigitalOcean/Hetzner) or serverless containers.
• RAG & Knowledge Base (Your AI Edge):
	• Ingest verified WAEC and JAMB past questions (1995–2026) and official syllabi into PostgreSQL with pgvector or Qdrant (using FastEmbed locally on your server so embedding generation costs ₦0).
	• When a student asks "Why is option B wrong?" or snaps a photo of a math problem, your system retrieves the exact syllabus rule and verified solution before passing it to an affordable, fast LLM (like Gemini Flash or GPT-4o-mini) to explain step-by-step in simple Nigerian English.
• Payment Engine (Solving the ₦300 Fee Trap):
	• Integrate Paystack or Flutterwave with Dedicated Virtual Accounts (DVA) or Direct Debit.
	• Instead of charging ₦300 every week (where gateway fees + bank charges eat ~10–15%), let students/parents fund a ₦1,200 monthly wallet (1 gateway fee) and deduct ₦300 every Monday at 6:00 AM for that week's mock test and AI tutor access. Offer a ₦300 "7-day trial pass" via instant bank transfer for first-timers.

2. Core Features That Drive Weekly Retention

To keep 20,000 students renewing every single week, design around habit loops and social competition:
1. Daily 10-Question Morning Sprint (WhatsApp): At 7:00 AM daily, the bot sends 10 bite-sized questions on the student's 4 JAMB subjects using WhatsApp interactive buttons (A, B, C, D). Instant grading + 2-sentence explanation.
2. "Snap & Solve" Homework Helper: Students send a photo of a past question or textbook problem on WhatsApp. OCR + your RAG pipeline breaks down the solution step-by-step.
3. Saturday Nationwide Mock & Leaderboard: Every Saturday, open a timed 60-minute CBT mock on your lightweight web link. Publish state-by-state and school-by-school rankings on Sunday evening (e.g., "Top 10 JAMB Scorers in Benue State This Week"). Students share their scorecards on WhatsApp Status, driving free viral signups.
4. Parent Weekly Progress Report: When a student signs up, ask for a parent's WhatsApp number. Every Sunday, send the parent a clean report card ("Chinedu answered 65 questions this week, 72% accuracy, weak in Organic Chemistry"). Parents gladly pay ₦300/week when they see proof their child is studying.

3. Unit Economics at 20,000 Weekly Users

Here is what your weekly numbers look like at scale:

Metric	Weekly Estimate	Notes
Gross Revenue	₦6,000,000	20,000 active users × ₦300
Payment Processing (~2%)	-₦120,000	Optimized via ₦1,200 monthly wallet top-ups
WhatsApp API & Server Costs	-₦450,000	Service conversations are free; pay only for proactive utility/marketing templates
AI / LLM Inference Costs	-₦250,000	Cached explanations for repeated past questions cut API calls by ~80%
Affiliate / School Commissions	-₦1,000,000	Paying lesson teachers/ambassadors ₦50–₦100 per active renewal
Estimated Weekly Net Profit	~₦4,180,000	~70% net margin once cached and batched

(Pro-tip: Cache every AI explanation in Postgres/Redis the first time a student asks about Question #42 from JAMB Physics 2019. By week 4, 85% of student queries will serve straight from your database at zero AI cost.)

4. Step-by-Step Roadmap to Your First 20,000 Users

• Weeks 1–2: Data & Core Bot MVP
	• Scrape, clean, and structure at least 10,000 verified past questions across English, Mathematics, Physics, Chemistry, Biology, Economics, Government, and Literature.
	• Build the WhatsApp webhook flow: Onboarding (pick 4 subjects) → 3 free daily questions → ₦300 paywall.
• Weeks 3–4: Local School & Lesson Center Pilot (0 → 500 Users)
	• Do not start with expensive Facebook/Instagram ads. Visit 5 private secondary schools and JAMB tutorial centers right around you (e.g., in Otukpo or Makurdi).
	• Pitch the school principal or lesson coordinator: "Let your SS3/JAMB students take our weekly CBT mock for free for 2 weeks; after that, give the school ₦50 every week for each student who stays subscribed." Five schools of 100 students gives you your first 500 paying users and live feedback.
• Weeks 5–8: Viral Referral Engine & Micro-Influencers (500 → 5,000 Users)
	• Add a built-in referral command (REFERRAL): "Invite 3 classmates to subscribe and get 2 weeks free."
	• Pay small Nigerian student TikTokers and WhatsApp TV admins (₦15k–₦30k per post) to post screen recordings of the bot solving tough JAMB math questions in 5 seconds.
• Weeks 9–16: B2B2C Scaling (5,000 → 20,000 Users)
	• Recruit 100 campus/lesson-center ambassadors across major hubs (Lagos, Abuja, Ibadan, Port Harcourt, Enugu, Kano, Makurdi). Give each ambassador a custom referral code earning ₦70/week per active student they bring in—200 students per ambassador equals 20,000 weekly subscribers
