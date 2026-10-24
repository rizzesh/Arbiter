
# Text to Cards

Paste a poster, WhatsApp forward, email or posting and get an organized card with dates, venue, money, eligibility, links and next actions. Uses the Gemini API with structured JSON output. No model training.

## Run

```bash
pip install -r requirements.txt
cp .env.example .env        # then paste your key into .env
uvicorn main:app --reload
```

Open http://localhost:8000 and click **Try a sample**.

## Files

- `main.py`: FastAPI app, Gemini prompt and schema, date/urgency/link post-processing
- `index.html`: single-page card UI (no build step)

## Tuning

- Change the model with `GEMINI_MODEL` in `.env`.
- Edit `SYSTEM_PROMPT` in `main.py` to adjust extraction rules.
- Add or rename fields in the `Item` model; the UI reads `details` for anything type-specific.

## Next phases

1. Calendar: turn `dates` (ISO) into an `.ics` download or Google Calendar link.
2. Images: send the image to Gemini as an extra `Part` in `call_gemini`.