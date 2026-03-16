# Design Alignment Agent

An AI-assisted interior design exploration system built for the Google Gemini Hackathon.

Live Demo  
https://design-alignment-agent-71566893016.us-central1.run.app/demo

Health Endpoint  
https://design-alignment-agent-71566893016.us-central1.run.app/health


## Problem

Interior design discovery is difficult because most users cannot clearly describe their taste using text prompts.

People usually know what they like **when they see it**, not when they try to describe it.

Traditional AI design tools rely heavily on prompting, which creates a gap between the user’s intent and the generated result.


## Solution

The Design Alignment Agent helps users discover their design direction through **visual selection rounds** instead of text prompts.

The system presents multiple interior directions.  
Each user selection refines the design space.

After a few rounds, the system converges to a coherent interior design brief.


## Demo Flow

1. **Style Discovery**

User sees a grid of interior styles (Minimalist, Japandi, Industrial, etc.).

The user selects the style that best matches their preference.

---

2. **Style Commentary**

Gemini generates a structured explanation including:

- VIBE
- KEY RULES
- WATCH OUTS
- NEXT EXPLORATION

This explains the design language before exploration begins.

---

3. **Round 1 – Direction Exploration**

The system generates **three design directions**.

Each option includes:

- generated interior image
- title
- design commentary
- design attributes

User selects the direction they prefer.

---

4. **Round 2 – Taste Refinement**

The system refines the selected direction with three new variations.

The variations explore changes in:

- material tonality
- wood finishes
- textiles
- wall / floor treatments
- carpet textures

Furniture layout remains consistent so the user focuses on **material language**.

---

5. **Final Proposal**

The system produces a final design brief summarizing the converged direction.


## Architecture


User (Browser)
↓
FastAPI Backend (Cloud Run)
↓
Gemini Planning + Image Generation
↓
Firestore Session Storage
↓
Generated Interior Options


The backend orchestrates multi-round design exploration using Gemini as the reasoning and generation engine.


## Technology Stack

Backend
- Python
- FastAPI
- Firestore

AI
- Gemini models
- Vertex AI image generation

Infrastructure
- Google Cloud Run

Frontend
- HTML
- JavaScript


## Repository Structure


backend/
main.py
round_service.py
selection_service.py
final_brief_service.py
image_generation_service.py
prompt_builders.py
design_direction_planner.py
static/

docs/

ARCHITECTURE.md


## Running Locally

Start the backend server:


cd backend
venv\Scripts\activate
uvicorn main:app --reload


Then open:


http://127.0.0.1:8000/demo


## Notes

For demo stability the system currently runs **two refinement rounds**.

The architecture supports deeper exploration but the demo is intentionally kept short.


## Hackathon

Built for the **Google Gemini Hackathon** as an exploration of visual preference alignment 
