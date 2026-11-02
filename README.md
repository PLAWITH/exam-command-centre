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

**Choosing the AI model:** Preferences → *Choose the AI model* lists every model on Groq's free plan (GPT-OSS 120B, GPT-OSS 20B, Qwen 3.8 27B and GPT-OSS Safeguard 20B), plus any other model your key can use. You can also switch from the menu at the top of Pip's chat, or ask Pip "use the fast model". If Groq switches a model off, the site moves to the next best one by itself.

## Google sign-in and sync (optional)

People can press **Sign in with Google** in Preferences, and their progress (every syllabus, timetable, notes, quiz and mock history) is saved to their Google account and synced across their devices. It's separate from Claude, and Groq keys are never uploaded. Each person can only read their own data.

### Google sign-in setup (site owner, one time, free)

1. Go to <https://console.firebase.google.com> → **Add project** (Google Analytics can be off).
2. **Build → Authentication → Get started → Sign-in method → Google → Enable → Save.**
3. **Authentication → Settings → Authorized domains → Add domain:** `plawith.github.io` (your GitHub Pages domain).
4. **Build → Firestore Database → Create database** (production mode, any nearby location).
5. In Firestore, open **Rules**, replace them with the following, and press **Publish**:

   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /users/{uid}/{document=**} {
         allow read, write: if request.auth != null && request.auth.uid == uid;
       }
     }
   }
   ```

6. **Project settings (⚙) → Your apps → Web (</>)** → register an app (no hosting needed) → copy the `firebaseConfig` values.
7. Paste them into `firebase-config.js` in this repository (replace `null`) and commit.

The free Spark plan is plenty for a class of students.

## Privacy

There is no server of our own. Your progress, notes and any uploaded syllabus stay in your browser, unless you sign in with Google, in which case they are also saved in your own account's private storage in the site's Firebase project. Use **Preferences → Export progress** to back up.
