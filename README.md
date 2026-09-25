# AI-Native Job Application Framework

Welcome to the AI-Native Job Application Framework! This repository contains zero executable code. It consists entirely of structured markdown prompts, configuration templates, and tracking files designed to instruct an AI agent equipped with browser automation and web search to apply for jobs on your behalf.

Works for any role; set your target job titles during setup.

## 🚀 Workflow

1. **Download the repository folder.**
2. **Open the folder in your AI app** with its browser tool turned on.
3. Type `start`.
4. Answer the setup questions one topic at a time. The agent saves your answers into the personal files and creates the tracking files.
5. Sign in to the job sites you selected in the agent's browser.
6. When setup is complete, the agent gives a model suggestion.
7. **Open a new chat on the suggested model and type `start`.**
8. The agent applies only to sites listed under **Where to apply** in `personal_data/profile.md`, using the matching strategy file and the project's daily limits.

Job sites limit automated applying by volume and speed, so this framework enforces strict daily limits.

On Claude, you will be asked to approve each submit.

---

## 🤖 AI Model Selection Guide

Do not hard-code model names or versions. The right model lineup changes over time.

The AI works out which app and model it is running on and suggests models from that same vendor's CURRENT lineup, using its own knowledge or the app's model picker.

**Fast / light tier:**
- LinkedIn, Indeed, Naukri, and Wellfound quick apply.

**Mid tier:**
- Workday, company direct apply, and discovery mode.

**Default / strongest tier:**
- Setup and initial personal-data configuration.

At `START`, if the current model is heavier than the task needs, use a lighter model from the same vendor. If it is too light for Workday or direct apply, use the mid tier.

If the same form step fails on 3 jobs in a row, stop that workflow and suggest switching to the mid tier.

Start a **NEW chat** after setup instead of switching models mid-chat. All answers are saved in files, so nothing is lost.
