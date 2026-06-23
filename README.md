# Intelligent Excuse Generator

An AI-powered system built in Python (Google Colab) that generates context-aware, scenario-specific excuses with supporting proof documents, multi-language output, and text-to-speech delivery.

## Features

- **AI Excuse Generation** — uses `google/flan-t5-large` via Hugging Face Transformers to generate detailed, scenario-specific excuses based on user input
- **Automatic Scenario Classification** — classifies input into medical, parental, official, or travel categories to select the appropriate proof type
- **Supporting Proof Generation**
  - PDF documents (medical certificates, parental notes, official letters, travel delay certificates) generated via `pdfkit`
  - Fake chat screenshots rendered using `Pillow (PIL)`
  - Fake location maps with random coordinates using `folium` and `Faker`
- **Multi-Language Support** — translates excuses and documents into 7 languages (English, Hindi, French, Spanish, German, Chinese, Arabic) using `googletrans`
- **Text-to-Speech Output** — converts the generated excuse to audio using `gTTS`, playable directly in the notebook
- **Excuse History & Favourites** — logs all generated excuses with scenario, language, and timestamp to a local JSON file; supports saving favourites
- **Smart Ranking System** — users rate excuses (1–5 stars); system tracks average ratings per scenario/language and surfaces the top-ranked excuses

## Tech Stack

| Component | Library |
|---|---|
| AI Text Generation | Hugging Face Transformers (`flan-t5-large`) |
| Translation | `googletrans` |
| Text-to-Speech | `gTTS` |
| PDF Generation | `pdfkit`, `wkhtmltopdf` |
| Chat Screenshots | `Pillow (PIL)` |
| Location Maps | `folium`, `Faker` |
| UI | `ipywidgets` (Google Colab) |
| Data Storage | JSON (Colab filesystem) |

## How to Run

1. Open the notebook in Google Colab
2. Run all cells from top to bottom (Runtime → Run all)
3. The first cell installs all dependencies automatically
4. Use the interactive widget UI to enter a scenario, select a language, and generate an excuse

```python
# Dependencies are installed automatically in Cell 1:
!pip install transformers ipywidgets pdfkit pillow folium faker gtts googletrans==4.0.0-rc1
!apt-get install -y wkhtmltopdf
```

## Example

**Input scenario:** `"missed a work meeting due to illness"`

**Output:**
- Generated excuse text (e.g., "I sincerely apologize for missing today's meeting — I had a sudden onset of fever and was advised by my doctor to rest.")
- Downloadable medical certificate PDF with AI-generated content
- Fake chat screenshot with a doctor
- Audio playback of the excuse in the selected language

## Project Structure

```
intelligent_excuse_generator.ipynb   # Main notebook (all code in one file)
excuse_history.json                  # Auto-generated: stores excuse history
excuse_rankings.json                 # Auto-generated: stores user ratings
excuse_audio.mp3                     # Auto-generated: TTS audio output
```

> Note: The `.json` and `.mp3` files are generated at runtime and do not need to be uploaded.

---

*Built by Eklavya Joshi | IIT Kharagpur*
