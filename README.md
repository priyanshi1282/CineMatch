# 🎬 CineMatch — Personal Film Intelligence Assistant

A conversational AI assistant that helps you discover 
critically acclaimed films you have never heard of. 
Built using the OpenAI Responses API as part of 
COMP47980: Generative AI and Language Models at 
University College Dublin.

---

## What it does

CineMatch is a domain-specific film assistant that 
recommends hidden gem films from a curated database 
of 223 obscure titles, fetches live data from external 
APIs, and analyses your personal watch history to 
build a taste profile. It is designed to surface 
films that mainstream platforms like Netflix and 
IMDb consistently overlook.

---

## Features

- Recommends genuinely obscure films using a custom 
  hidden gem scoring metric (IMDb rating + vote count 
  obscurity)
- Checks real-time weather in your city and matches 
  it to a film mood
- Fetches live film details via TMDB API
- Retrieves complete awards records via OMDb API
- Analyses your personal watch history CSV to find 
  taste patterns, genre biases, and your hidden gem 
  score
- Runs as a clean Gradio chat interface with a 
  shareable public URL

---

## Tech Stack

| Component | Tool |
|---|---|
| LLM Framework | OpenAI Responses API |
| RAG | OpenAI Vector Store + File Search |
| Film Data | TMDB API |
| Awards Data | OMDb API |
| Weather | Open-Meteo API (no key needed) |
| Data Processing | Python, Pandas |
| UI | Gradio |
| Environment | Google Colab |

---

## Setup

### 1. Clone or open the notebook in Google Colab

### 2. Add API keys as Colab Secrets

Go to the key icon in the left sidebar and add:

| Secret Name | Where to get it |
|---|---|
| OPENAI_API_KEY | platform.openai.com |
| TMDB_API_KEY | themoviedb.org/settings/api |
| OMDB_API_KEY | omdbapi.com (free tier) |

Toggle Notebook access ON for each key.

### 3. Mount Google Drive

The notebook will prompt you to connect your Drive. 
Create a folder called CineMatch in your Drive root 
before running.

### 4. Run all cells in order

The notebook will fetch film data, build the vector 
store, and launch the Gradio interface automatically. 
Full run takes approximately 5 minutes.

---

## How to use it

Once Gradio launches, try these prompts:

- "I love dark psychological films, I am in Dublin 
  tonight"
- "Tell me everything about the film Oldboy"
- "Did City of God win any major awards?"
- "Find me the most obscure hidden gem in your 
  database with a score above 8"

To analyse your watch history, upload a CSV with 
these columns:
title, year, genre, my_rating, times_watched


---

## Project Structure
CineMatch/ <br>
├── CineMatch.ipynb # Main notebook <br>
├── cinematch_dataset.csv # 223 hidden gem films <br>
└── API_Keys.pdf # (Removed, enter your own keys)


---

## Hidden Gem Score

Every film in the database has a hidden gem score 
calculated as:
score = (rating/10 * 0.6) +
((1 - votes/10000) * 0.4) * 10


A film rated 8.2 with 1,047 votes scores higher than 
a film rated 8.5 with 2 million votes. This metric 
does not exist in any mainstream recommendation 
platform.

---

## Data Source

Film data was compiled programmatically from the 
TMDB Discover API filtering for ratings above 7.0 
and vote counts between 1,000 and 10,000. This 
ensures every film in the database is critically 
verified but genuinely obscure.

---

## Built by

Priyanshi | MSc Student | University College Dublin  
COMP47980 Generative AI and Language Models, 2026
