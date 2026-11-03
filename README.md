# InfoExtract v2 — Mobile-first Hybrid Web App

## What is included
- Mobile-first responsive interface
- Camera capture (`capture="environment"`) and gallery upload
- Browser-side OCR with Tesseract.js (Arabic, Bangla, English; optional Hindi/Urdu)
- Optional AI structuring and English translation through a private server endpoint
- AI consent checkbox: only OCR text is sent to the AI endpoint; the image stays in the browser
- Editable fields, separate copy buttons for values only, copy all, TXT export
- Scroll view and one-field-at-a-time details view
- Dark mode and installable PWA shell

## Run on your computer
1. Install Node.js (LTS) from https://nodejs.org/
2. Extract this folder.
3. Open a terminal inside the `InfoExtract_v2` folder.
4. Run `npm install`
5. Copy `.env.example` to `.env` and add your API key if you want AI features.
6. Run `npm start`
7. Open `http://localhost:3000` in Chrome.

Without an API key, browser OCR, manual editing, individual copy, copy-all and TXT export still work. AI structuring/translation needs an OpenAI API key and API billing; ChatGPT subscription does not automatically include API usage.

## Use on a phone
To use camera capture and install as a PWA, deploy this project to an HTTPS host. Keep the API key only in the host's server-side environment variables. Never put it in `public/` or frontend JavaScript. On the phone, open the HTTPS URL in Chrome/Safari and choose Add to Home Screen / Install App.

## Privacy
- OCR is performed in the browser.
- If the user checks the AI consent box, the recognized OCR text is sent to the configured AI provider via the server. The image itself is not sent by this app's AI route.
- Do not use real identity documents until you have reviewed the AI provider's data controls and deployed the app with appropriate privacy/security measures.
- This starter has no user accounts or permanent document storage.

## Important limitations
- OCR and AI can make mistakes. Verify names, dates, ID numbers and nationality before using them.
- The AI endpoint currently uses OpenAI Responses API with structured JSON output. Model can be changed with `OPENAI_MODEL` in `.env`.
- PWA offline caching covers the app shell only. OCR language data and AI features require internet on first use / when requested.
