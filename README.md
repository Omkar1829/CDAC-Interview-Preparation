# 🤖 Adaptive Technical Interviewer & DSA Mentor Agent

An intelligent, autonomous AI technical interviewer and DSA problem-solving mentor designed for candidates of all experience levels—from freshers and CDAC candidates to experienced engineers (Mid-Level 1–4 YOE and Senior 5+ YOE).

---

## ✨ Key Capabilities

* 👤 **One-Time Adaptive Onboarding:** Gathers your profile once (years of experience, primary tech stack, target companies/roles, DSA comfort level) and permanently remembers it. Never prompts again unless explicitly requested.
* 📈 **Seniority-Calibrated Difficulty & Evaluation:** Calibrates questions, depth, and ranking criteria strictly to your seniority level.
* 🔁 **Sharp Cross-Questioning on Your Answers:** Evaluates your response and immediately asks technical follow-up questions probing edge cases, runtime/memory mechanics, internal optimizations, and trade-offs.
* 🧩 **Interactive DSA Solving:** Supports step-by-step algorithmic guidance, dry-running, live code review, time/space complexity proofs, and edge-case verification.
* 🧠 **Persistent Memory & Spaced Repetition:** Stores weak spots and mistakes in `AGENTS_MEMORY/` to automatically re-test you on past errors in subsequent drills.

---

## 🚀 How to Use

Simply start talking to the agent:

1. **First-Time Setup (Automatic):** If it's your first time, the agent will prompt you with a few quick questions about your experience, tech stack, and goals.
2. **Commands & Modes:**
   - `"Start mock interview"`: Initiates a personalized technical mock interview.
   - `"Solve DSA"`: Presents a calibrated algorithmic problem to solve together with code evaluation.
   - `"Review my mistakes"`: Summarizes your past errors and weak topics logged in memory.
   - `"My profile"`: Shows your stored experience level and settings.
   - `"Reset profile"`: Clears your profile if you want to re-onboard for a different target role.

---

## 📂 Repository Structure

```
├── AGENTS_MEMORY/
│   ├── memory.json              # Persistent user profile, weak topics & practice history
│   ├── mistakes.json            # Exact conceptual and algorithmic mistakes log
│   └── revision_schedule.json   # Spaced repetition revision queue
├── bootcamp/
│   ├── assignments/             # Study guides and reference assignments
│   ├── cheatsheets/             # Generated quick-reference cheatsheets
│   ├── code-reviews/            # Automated code review logs
│   ├── mistakes/                # Subject-wise mistakes archives (DSA, Java, SQL)
│   └── mock-interviews/         # Recorded transcripts and performance audit reports
├── AGENT_WORKFLOW.md            # Detailed workflow specifications and scoring rubrics
└── README.md                    # Project documentation
```
