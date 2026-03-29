# Travel AI

Travel AI is a Streamlit-based trip planning assistant powered by OpenAI. It takes your travel preferences, optional video reels, and budget to generate style-matched place recommendations and a structured day-by-day itinerary.

## Features

- **Multi-step wizard UI** — Guided flow for city selection, date ranges, traveler count, transport preferences, and travel style.
- **Video reel ingestion** — Upload short travel clips; the app extracts audio, transcribes it, and uses a multimodal LLM to pull out preferences and locations.
- **Style-based recommendations** — For each destination, an AI agent returns places tailored to your travel style (e.g., romantic, adventurous, foodie).
- **Budget optimization** — Scores and ranks recommended places by estimated cost and review quality to fit your total budget.
- **Itinerary generation** — Produces a structured day-by-day trip plan with times, transport modes, costs, and tips.
- **Export** — Download the final trip plan as a JSON file.

## Prerequisites

- Python 3.11+
- An OpenAI API key
- [FFmpeg](https://ffmpeg.org/download.html) installed on your system

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/travel-ai.git
   cd travel-ai
   ```

2. **Install the dependencies:**

   ```bash
   pip install streamlit openai moviepy opencv-python pillow
   ```

## Configuration

Create a `.streamlit/secrets.toml` file (it is gitignored) and add your API key:

```toml
OPENAI_API_KEY = "your-key-here"
```

## Running the App

```bash
streamlit run main.py
```

## Project Structure

```
travel-ai/
├── main.py                          # Streamlit app entry point and wizard flow
├── agents/
│   ├── style_agent.py               # Place recommendations per city based on travel style
│   ├── budget_agent.py              # Cost/review scoring and budget-fitted place selection
│   ├── multiple_reels.py            # Video reel pipeline: transcription, montage, summarization
│   ├── process_video.py             # (WIP) Single-video processing
│   └── logistics/
│       ├── logistics.py             # Itinerary generation
│       └── visualize_logistics.py   # Streamlit rendering of the trip plan
```
