# Debug-Buddy
It helps students and beginner developers understand how to fix the bug by understanding not by only copy pasting it . We learn what we should do and the code is bug free.

# 🧭 Debug Buddy
> **"We don't fix your bug. We make you faster at finding it."**
> 
> *An AI-powered cognitive debugging companion that builds problem-solving intuition instead of spoiling solutions.*
---
## 📖 Overview
**Debug Buddy** is an interactive debugging assistant designed for computer science students, bootcamp learners, and software engineers.
Mainstream AI tools (like ChatGPT, Copilot, or Claude) often immediately output the corrected code, bypassing the critical cognitive process of learning how to debug. **Debug Buddy** enforces **pedagogical scaffolding**:
- **🔍 Plain-English Code Walkthrough:** Translates unfamiliar functions and execution flows into clear, jargon-free explanations.
- **📍 Dynamic Suspect Zone Shading:** Focuses your attention on a 3+ line suspect region directly in the code editor without pinpointing the exact line.
- **🧩 Multi-Bug Detection & Issue Switching:** Analyzes entire snippets to identify all concurrent bugs (e.g. array bounds, type narrowing, uninitialized memory, logic inversions) and lets you toggle focus between issues.
- **❓ Guided Trace Questions:** Asks step-by-step questions about variable states and loop transitions so you trace execution yourself.
- **🧪 Diagnostic Experiments & Verification:** Suggests minimal print statements and boundary inputs to isolate runtime discrepancies.
- **🔥 Interactive Hypothesis Tester:** Test your theories and receive instant **Hot / Warm / Colder** feedback.
- **🪜 Progressive 3-Tier Hint Ladder:** Escalates from a high-level conceptual nudge to a concrete comparison short of the answer.
- **🔒 Gated Solution & Explain-Back:** The root cause and corrected fix remain locked until you have explored all hint tiers.
- **🛡️ Automated Leak Checker:** Enforces strict guardrails against code diff leaks or line number reveals in early hints.
- **📊 Session Bug Pattern Tracking:** Tracks recurring mistakes (Off-by-one, Bad Initial Value, Type Issues) in local storage.
---
## 🛠️ Tech Stack
- **Frontend:** React 18, Vite, Tailwind CSS, Lucide Icons
- **Backend:** Node.js, Express, Rate Limiting (CORS protected)
- **AI Engine:** Google Gemini API (`@google/genai` with `gemini-3.8-flash`) + Two-Pass Reasoning Pipeline
- **Offline Fallback Engine:** Built-in Abstract Syntax & Control-Flow Analyzer
- **Orchestration:** Single root command with `concurrently`
---
## 🚀 Quick Start (Local Setup)
### 1. Prerequisites
- **Node.js** (v18.0.0 or higher)
- **npm** (v9.0.0 or higher)
### 2. Clone & Install Dependencies
```bash
git clone https://github.com/your-username/debug-buddy.git
cd debug-buddy
# Install dependencies for root, server, and client in one command
npm run install:all

  
3. Configure Environment Variables (Optional)

  

Debug Buddy includes an offline dynamic code analyzer that works out of the box. To enable live Gemini AI semantic analysis:


  
bash
# Copy the environment template
cp .env.example .env
# Add your Gemini API key inside .env (Get free key from https://aistudio.google.com/)
# GEMINI_API_KEY=your_gemini_api_key_here

  

(You can also paste your key directly in the web app via the "🔑 Gemini Key" button in the header.)


  
4. Run the Application

  
bash
npm run dev

  

The application will start concurrently:


  

  
Frontend App: http://localhost:5173

  
Backend API: http://localhost:3001

  

  

  
🎯 How It Works: The 7-Stage Scaffolding Flow

  

  

  
Card ① - What Your Code is Doing: High-level summary of intent and structure.

  
Card ② - Trace Questions: Inquisitive prompts to step through variables on scratch paper.

  
Card ③ - Focus Zone & Bug Type: Highlights the relevant 3-line block in the editor.

  
Card ④ - Diagnostic Experiments: Checklists for print statements and edge-case inputs.

  
Card ⑤ - My Hypothesis Tester: Real-time feedback on user guesses (Hot / Warm / Colder).

  
Card ⑥ - Progressive Hints:
  
  

  
Level 1: Conceptual nudge

  
Level 2: Targeted focal area

  
Level 3: Concrete comparison short of the answer

  

  
Card ⑦ - Locked Solution: Root cause explanation and fix revealed only after completing all tiers.

  

  

  
📁 Project Structure

  
debug-buddy/
├── .env.example               # Environment variables template
├── package.json               # Root orchestration scripts
├── README.md                  # Main documentation
├── client/                    # React + Vite Frontend
│   ├── index.html
│   ├── vite.config.js         # API proxy & network host configuration
│   ├── tailwind.config.js     # Styling tokens and dark mode
│   └── src/
│       ├── App.jsx            # State management & app layout
│       ├── components/
│       │   ├── Header.jsx         # Controls, mode switcher, ELI5 mode, theme
│       │   ├── CodeEditor.jsx     # Textarea with line numbers & shaded focus zone
│       │   ├── GuidePanel.jsx     # Container for 7-stage debugging cards
│       │   ├── TraceQuestions.jsx # Guided execution questions
│       │   ├── SuspectZone.jsx    # Suspect region & multi-bug selector
│       │   ├── Experiments.jsx    # Interactive diagnostic checklist
│       │   ├── HypothesisBox.jsx  # Guess evaluation (Hot/Warm/Colder)
│       │   ├── HintLadder.jsx     # Progressive 3-tier hint ladder
│       │   ├── LockedReveal.jsx   # Solution reveal & learning takeaway
│       │   ├── SessionHistory.jsx # History and bug pattern analytics
│       │   ├── ApiKeyModal.jsx    # In-app Gemini key configuration
│       │   └── ThemeToggle.jsx    # Light / Dark mode switcher
│       └── data/
│           └── sampleSnippets.js  # Curated demo bugs (Python, JS, C++)
├── server/                    # Node.js + Express Backend
│   ├── index.js               # Express server, rate limiter, CORS
│   ├── routes/
│   │   ├── guide.js           # POST /api/guide
│   │   ├── hypothesis.js      # POST /api/hypothesis
│   │   └── reveal.js          # POST /api/reveal
│   └── services/
│       ├── llmService.js      # Gemini API client with caching & dynamic fallback
│       ├── twoPassReasoning.js# Pass 1 (Diagnostic) + Pass 2 (Pedagogical) pipeline
│       ├── leakChecker.js     # Guardrail scanner blocking solution leaks in hints
│       └── dynamicCodeAnalyzer.js # Universal multi-bug AST & control-flow analyzer
├── prompts/                   # LLM Prompt Templates
│   ├── guide.pass1.txt        # Hidden root-cause analyzer
│   ├── guide.pass2.txt        # Student-facing guide generator
│   └── hypothesis.system.txt  # Hypothesis evaluator
└── docs/                      # Technical Documentation
    ├── problem_statement.md   # Problem statement & personas
    ├── solution_design.md     # Architectural design & cognitive principles
    ├── architecture.md        # Mermaid diagrams & API reference
    ├── roadmap.md             # MVP to future scope
    └── demo_script.md         # Presentation script

  

  
💻 Developer Tooling Insights

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
Feature	Pedagogical Value
Cognitive Scaffolding	Replaces answer-spoiling LLMs with progressive discovery.
Rapid Feedback Loop	Validates student hypotheses in real time (Hot / Warm / Colder).
Multi-Bug Handling	Simultaneously tracks multiple defects in a single file and adapts dynamically when one is fixed.
Accessibility & Inclusion	Includes ELI5 Mode to translate technical jargon into simple analogies, keyboard shortcuts (Ctrl+Enter), and light/dark theme support.

  
