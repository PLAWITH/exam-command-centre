# Exam Command Centre

A crayon-on-paper exam preparation website: study planner, syllabus tracker, revision notes, quizzes, flashcards, mock exams, progress analytics, and **Pip**, a little paper helper with legs.

Everything is in one file, `index.html`. It needs no server or build step and works offline once loaded. Progress is saved in your own browser.

## Use it

- **Online:** turn on GitHub Pages for this repository (Settings → Pages → Deploy from a branch → `main` / root), then open `https://<your-username>.github.io/<repo-name>/`.
- **Offline:** download `index.html` and open it in any browser.

## What's inside

- **Built-in syllabus (default):** November 2026 exams with hand-written notes, 265 quiz questions, 161 flashcards and 21 mock papers (three per subject). Papers can be paused (the paper is hidden while paused) and printed or saved as PDF, with an optional answer key.
- **Study planner:** respects the daily study limit, rest days, holidays and preparatory leave. You can edit, drag, add, delete and reschedule sessions, take a day off, or regenerate the plan.
- **Study button:** opens the notes, practice questions and flashcards for that session on one screen.
- **Pip:** handles maths, number-base conversions with working, definitions, exam countdowns, and commands like "quiz me on surds" or "take 9 Nov off".

## Optional AI (your own Groq key)

AI is off by default. To switch it on:

1. Get a free API key at <https://console.groq.com/keys>.
2. In the site, go to **Preferences → AI with your own Groq key**, paste the key, then press **Save and test**.

With a key, Pip answers anything in your own words and can do things in the site for you. You can also **upload your own syllabus**: a PDF of your date sheet and syllabus is read by AI, you check it, and the site builds your own timetable. AI then writes notes, questions, flashcards and mock papers for your topics. The built-in syllabus stays as the default, and you can switch between them in Preferences.

**About your key:** it is stored only in your browser's local storage, is never included in exports, and is sent only to `api.groq.com`. Use your own key and don't share it. Groq's free tier has rate limits; if you hit one, wait a minute.

Default models: `llama-3.3-70b-versatile` (text) and `meta-llama/llama-4-scout-17b-16e-instruct` (scanned pages and photos). You can change both in Preferences if Groq renames them.

## Privacy

There is no backend. Your progress, notes and any uploaded syllabus stay in your browser. Use **Preferences → Export progress** to back up.
