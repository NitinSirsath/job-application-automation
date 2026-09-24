# AI-Native Job Application Framework

Welcome to the AI-Native Job Application Framework! This repository contains zero executable code. It consists entirely of structured markdown prompts, configuration templates, and tracking files designed to instruct an Advanced AI Agent (equipped with browser automation and web search) to apply for jobs on your behalf.

This framework is tailored for Software Engineers (specifically Frontend/React developers) but is easily adaptable for any role.

## 🚀 Workflow

1. **Clone the repository.**
2. **Setup your Personal Data:**
   - Go to the `/personal_data` directory.
   - Copy `profile_template.md` to `profile.md`.
   - Copy `form_answers_template.md` to `form_answers.md`.
   - Copy `credentials_template.md` to `credentials.md`.
   - Fill out the newly created files with your actual details. (These files are ignored by git to protect your privacy).
   - Ensure your resume is placed as `/personal_data/resume.pdf`.
3. **Configure the AI Agent:**
   - Edit the `🚀_ENTRY_PROMPT.md` file to set your session goal (e.g., apply on specific platforms, use discovery mode).
4. **Launch the Agent:**
   - Point your AI Agent (capable of reading files and browser automation) to `🚀_ENTRY_PROMPT.md` and start the run!

---

## 🤖 AI Model Selection Guide

When using this framework with an AI coding assistant or agent platform, selecting the right model for the task is crucial for balancing capability, speed, and cost.

**When to use Heavy / Reasoning Models (e.g., Gemini Pro, Claude Sonnet, GPT-4o):**
- Use these models when you are **generating your initial personal data** or **modifying the complex strategy files** in the `/instructions` directory. 
- Heavy models are better at understanding nuanced instructions, formatting your profile effectively, and planning advanced strategies.

**When to use Fast / Lightweight Models (e.g., Gemini Flash, Claude Haiku, GPT-4o-mini):**
- **CRITICAL:** You MUST switch to a fast model for the **actual execution/browser automation** phase (when the agent is actively filling out forms and clicking buttons). 
- Browser automation requires hundreds of sequential steps and DOM inspections. Using a heavy model for this will be incredibly slow and extremely expensive due to token costs. Fast models are perfectly capable of executing the standard application steps defined in this framework.
