# 🧭 Debug Buddy

> **"We don't fix your code. We teach your brain how to find the bug."**

Debug Buddy is an AI-powered debugging coach. Instead of spoiling the answer like ChatGPT or GitHub Copilot, it guides your thinking step-by-step using progressive hints, trace questions, and interactive experiments.

---

## 💡 Why Debug Buddy?

When you paste buggy code into traditional AI tools, they immediately give you the fixed code. 

**The problem?** You copy-paste the fix, but you never actually learn *why* it failed or *how* to find similar bugs on your own.

**Debug Buddy solves this by acting like a senior developer sitting next to you:**
- 🚫 **Zero Spoilers:** It will never write the fix for you or say *"the bug is on line 4"*.
- 📍 **Focus Zones:** It gently points to a 3-line area on the editor to focus your attention.
- 🧩 **Multi-Bug Detection:** If your code has 2 or 3 separate issues, it catches all of them and lets you tackle them one at a time.
- ❓ **Thinking Questions:** It gives you trace questions to think about variable states on scratch paper.
- 🧪 **Mini-Experiments:** Suggests exact `print` / `console.log` statements to prove your theories.
- 🔥 **Hot / Warm / Colder Guesses:** Test your own theory and get immediate feedback.
- 🪜 **3-Level Hint Ladder:** Start with a gentle conceptual nudge, and only reveal stronger hints if you're truly stuck.
- 🔒 **Gated Solution:** The final answer is locked until you work through the hints.

---

## 🎬 How It Works (The 7-Step Experience)

When you paste your code and click **"Help Me Think"**, you get a 7-card guided workspace:

1. **Card 1 (The Intent):** What your code is trying to accomplish in plain English.
2. **Card 2 (Trace It):** Step-by-step questions to mentally step through your loops and variables.
3. **Card 3 (Where to Look):** A highlighted amber zone in the editor showing where logic breaks down.
4. **Card 4 (Diagnostic Experiments):** Actionable checks (e.g. *"Log variable X before entering the loop"*).
5. **Card 5 (Hypothesis Tester):** Type your guess (e.g., *"Is index out of bounds?"*) $\rightarrow$ get instant **Hot 🔥 / Colder ❄️** feedback.
6. **Card 6 (Progressive Hints):** 
   - *Level 1:* High-level nudge
   - *Level 2:* Narrowed focal point
   - *Level 3:* Concrete comparison
7. **Card 7 (The Reveal):** Unlocks the root cause and fix only after you have explored all 3 hints.

---

## ⚡ Quick Start (Run it in 2 minutes)

### Prerequisites
- [Node.js](https://nodejs.org/) (version 18 or above)
- [npm](https://www.npmjs.com/)

### 1. Clone & Install
```bash
git clone https://github.com/your-username/debug-buddy.git
cd debug-buddy
npm run install:all
