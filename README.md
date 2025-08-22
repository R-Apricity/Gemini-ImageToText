Gemini-ImageToText

An Express server that turns an image URL into a detailed prompt using Google’s Gemini (gemini-2.5-flash). It uploads the image via the Google AI File API and returns a single-paragraph prompt-like description.

Features
- Image URL input with MIME validation
- Uses Google AI Studio API via `@google/generative-ai`
- Temporary on-disk upload for server-side file upload
- Simple REST endpoint: `GET /doreq?imgurl=...`

Prerequisites
- Node.js 18+ (ESM + top-level await)
- A Google AI Studio API key with access to Gemini models

Setup
1. Install dependencies:
   - `npm install`
2. Provide your API key:
   - Create `.env` with: `API_KEY=your_google_api_key`
3. Optional: set server port with `PORT` (defaults to `2500`).

Run
- Start the server:
  - `node index.js`
- Health check:
  - `curl http://localhost:2500/`

API
- `GET /doreq?imgurl=<public_image_url>`
  - Returns: `{ repsonse: string }` (note: key name is `repsonse` in current code)

Example
```
curl --get \
  --data-urlencode "imgurl=https://upload.wikimedia.org/wikipedia/commons/3/3f/Fronalpstock_Aussicht.jpg" \
  http://localhost:2500/doreq
```

Environment
- `API_KEY`: Google AI Studio API key (required)
- `PORT`: Server port (default `2500`)

Notes
- This service uses a temporary directory under the OS temp folder for transient image storage before upload.
- Logging is enabled via `morgan`. CORS is allowed for all origins by default.

Repository
- Current origin (before change): https://github.com/KuntilBogel/Test-GEMINI/
- Target (requested): https://github.com/R-Apricity/Gemini-ImageToText

