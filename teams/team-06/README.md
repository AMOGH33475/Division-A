# AI Comic Strip Generator 📰🎨

A serverless, fully free AI application that transforms news headlines into beautiful 4-panel comic strips. Built for a 12-hour hackathon, this app uses Hugging Face's Free Serverless Inference API to combine Large Language Models and text-to-image diffusion into a seamless Streamlit experience.

## ✨ Features
- **Zero Paid APIs**: Runs 100% on Hugging Face's free tier.
- **Llama 3 Scriptwriting**: Uses `meta-llama/Meta-Llama-3-8B-Instruct` to dynamically generate a 4-panel JSON comic script from any headline, complete with character dialogue and detailed scene descriptions.
- **Stable Diffusion Art**: Generates high-quality, editorial-style comic panels using `stabilityai/stable-diffusion-xl-base-1.0`.
- **Dynamic Layout Engine**: Uses Pillow (PIL) to automatically stitch images, calculate text wrapping, and overlay classic comic book speech bubbles with tails.
- **Robust Error Handling**: Includes automatic API retries and hardcoded fallback templates so the demo never crashes.

## 🛠️ Technology Stack
- **Frontend**: Streamlit
- **AI Models**: Llama-3-8B-Instruct (Text), SDXL 1.0 (Image)
- **API Client**: `huggingface_hub`
- **Image Processing**: Pillow (PIL)
- **Data**: Pandas (for reading local news CSVs)

## 🚀 Setup & Installation

### 1. Prerequisites
- Python 3.9+
- A [Hugging Face](https://huggingface.co/) account and API Token (with Inference permissions).

### 2. Install Dependencies
```bash
pip install streamlit requests huggingface_hub Pillow pandas
```

### 3. Add API Key
Create a `.streamlit/secrets.toml` file in the root directory and add your token:
```toml
hf_api_token = "hf_YOUR_TOKEN_HERE"
```

### 4. Run the App
```bash
python -m streamlit run app.py
```
Then open `http://localhost:8501` in your browser!

## 💡 How it Works
1. **Selection**: User picks a category (Politics, Science, Sports) and a headline from `news_sample.csv`.
2. **Prompting**: The app sends a highly constrained prompt to Llama 3 to output a JSON array of 4 panels (dialogue + visual prompts).
3. **Generation**: The app calls SDXL to generate the raw images, using a strict negative prompt to maintain professional illustration quality.
4. **Compositing**: The layout engine resizes the images, draws speech bubbles based on text length, overlays the dialogue, and stitches them into a 2x2 grid.

## ⚠️ Note on API Limits
This app relies on Hugging Face's free monthly serverless inference quota. If you see a `402 Payment Required` error in the logs, it means your token has exhausted its free monthly credits. Generate a new token or upgrade your Hugging Face account to continue generating comics.
