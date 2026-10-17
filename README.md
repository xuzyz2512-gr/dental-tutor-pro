# Dental Tutor Pro

Study app for dental students: AI tutor (Gemini), MCQ quiz, flashcards, notes, study planner, progress page. Zero npm dependencies; needs Node 18+.

## Run locally
    GEMINI_API_KEY=your-key npm start    # http://localhost:3000
Without `GEMINI_API_KEY` the app runs and the tutor returns a clear "not configured" message. See `.env.example`.

## Test
    npm test    # API tests with a mocked Gemini (no key or network needed)

## Environment variables
- `GEMINI_API_KEY` (required for the tutor; server-side only, never sent to the browser)
- `GEMINI_MODEL` (default `gemini-2.5-flash`; check Google's docs for current model names)
- `PORT` (set by the host; default 3000)

## Deploy (Render free web service)
Connect the repo; Render reads `render.yaml`. Add `GEMINI_API_KEY` in the Render dashboard. Health check: `/health`.

## Limitations
- Notes, planner, quiz and flashcard progress live in the browser (localStorage): per device, lost if browser data is cleared. There are no accounts.
- Free hosts sleep when idle and have no persistent disk.
- Sample questions and flashcards are original examples, not from any official exam. Add more in `data/content.json`.
- Rate limiting is in-memory (20 tutor requests/min per IP) and resets on restart.
- Lessons and offline mode are not built yet.
