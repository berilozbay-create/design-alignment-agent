# Architecture — design-alignment-agent (MVP)

Frontend (later) → Cloud Run (FastAPI) → Firestore (nam5) → Gemini (Vertex AI)

Gemini split calls:
1. Style commentary
2. Constraint extraction (text → JSON)
3. 4 image generation (512px)
4. Per-card editorial commentary
5. Final brief