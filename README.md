# PulseTag - AI-Driven Hashtag Generator

<img width="1022" height="777" alt="Screenshot 2026-02-03 114308" src="https://github.com/user-attachments/assets/88795d2d-fce4-484b-8cf7-382d81b9f3c1" />

A powerful web application that analyzes your social media posts in real-time, suggesting the top trending hashtags to maximize post reach and engagement. Perfect for influencers and marketers who want to stay ahead of the trend curve.

## Why OpenRouter?

This application uses OpenRouter.ai to provide **free access** to state-of-the-art language models. No need for paid API keys - just sign up for a free account and start generating hashtags immediately! OpenRouter gives you access to models like Llama 3.2, Gemma 2, and Phi-3 at no cost.

## Features

- **Multi-Platform Support**: Works with LinkedIn and X/Twitter posts
- **AI-Powered Analysis**: Uses advanced LLMs to generate contextually relevant hashtags
- **Three-Tier Hashtag Strategy**:
  - **Safe**: High-volume, broad tags for baseline visibility
  - **Rising**: Trending, mid-volume tags for current relevance
  - **Niche**: Specific, low-competition tags for high-intent audiences
- **Interactive UI**: Click to add hashtags, edit posts in real-time
- **One-Click Copy**: Export your enhanced post with hashtags instantly

## Tech Stack

- **Frontend**: Next.js 16, TypeScript, Tailwind CSS, Lucide React
- **Backend**: Python 3.11+, FastAPI
- **Scraping**: Playwright, BeautifulSoup4
- **AI**: OpenRouter API with free LLM models (Llama 3.2, Gemma 2, Phi-3)
- **Containerisation**: Docker & Docker Compose

## Quick Start

### Prerequisites

- Docker and Docker Compose installed on your system
- OpenRouter API key (free at https://openrouter.ai/keys)

### 1. Clone the Repository

```bash
git clone https://github.com/bradmca/pulse-tag.git
cd pulse-tag
```

### 2. Configure Environment Variables

Create a `.env` file in the `/backend` directory:

```bash
cp backend/.env.example backend/.env
```

Edit the `.env` file with your credentials:

```env
# Get your free API key from https://openrouter.ai/keys
OPENROUTER_API_KEY=sk-or-v1-your-key-here
# Optional: Choose a model (defaults to Llama 3.2 3B)
OPENROUTER_MODEL=meta-llama/llama-3.2-3b-instruct:free
# Optional: LinkedIn cookies for bypassing login walls
LINKEDIN_COOKIES=...
```

### 3. Start the Application

**Option 1: Using Setup Script (Recommended)**

- On Windows: Run `.\setup.ps1` in PowerShell
- On macOS/Linux: Run `chmod +x setup.sh && ./setup.sh`

**Option 2: Manual Docker Compose**

```bash
docker-compose up --build
```

The application will be available at:
- Frontend: http://localhost:3000
- Backend API: http://localhost:8000
- API Documentation: http://localhost:8000/docs

## Manual Setup (Alternative)

### Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Install Playwright browsers
playwright install chromium

# Create .env file with your OpenAI API key
cp .env.example .env
# Edit .env with your API key

# Run the server
uvicorn main:app --reload
```

### Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Run the development server
npm run dev
```

## Usage Guide

1. **Paste a Post URL**: Copy and paste a LinkedIn or X/Twitter post URL into the input field
2. **Generate Tags**: Click "Generate Tags" to analyze the post
3. **Review Hashtags**: View suggested hashtags in three categories
4. **Add Hashtags**: Click on any hashtag to add it to your post
5. **Edit & Copy**: Modify your post text if needed, then copy to clipboard

## API Endpoints

### Analyze Post
```
POST /api/analyze
Content-Type: application/json

{
  "url": "https://www.linkedin.com/posts/..."
}
```

### Health Check
```
GET /api/health
```

## Development

### Project Structure

```
pulse-tag/
├── backend/
│   ├── main.py          # FastAPI application
│   ├── scraper.py       # Social media scraper
│   ├── ai_engine.py     # AI hashtag generator
│   ├── requirements.txt # Python dependencies
│   └── Dockerfile       # Backend Docker config
├── frontend/
│   ├── src/app/
│   │   └── page.tsx     # Main React component
│   ├── package.json     # Node.js dependencies
│   └── Dockerfile       # Frontend Docker config
├── docker-compose.yml   # Container orchestration
└── README.md           # This file
```

### Environment Variables

#### Backend (.env)
- `OPENROUTER_API_KEY`: Your OpenRouter API key (required) - get free at https://openrouter.ai/keys
- `OPENROUTER_MODEL`: The model to use (optional, defaults to meta-llama/llama-3.2-3b-instruct:free)
  - Free options include:
    - meta-llama/llama-3.2-3b-instruct:free
    - meta-llama/llama-3.2-1b-instruct:free
    - google/gemma-2-9b-it:free
    - microsoft/phi-3-medium-128k-instruct:free
- `LINKEDIN_COOKIES`: LinkedIn cookies for bypassing login walls (optional)

## Troubleshooting

### LinkedIn Scraping Issues
If LinkedIn blocks the scraper:
1. Log in to LinkedIn in Chrome
2. Use a browser extension to export cookies (e.g., "Get cookies.txt")
3. Format the cookies as `key1=value1; key2=value2; ...`
4. Add them to your `.env` file as `LINKEDIN_COOKIES`

### Common Issues

1. **CORS Errors**: Ensure the backend is running and CORS is configured for localhost:3000
2. **Playwright Browser Issues**: Run `playwright install chromium` in the backend directory
3. **OpenRouter API Errors**: Verify your API key is valid and check OpenRouter status

## Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Quick Links
- [Code of Conduct](CODE_OF_CONDUCT.md)
- [Security Policy](SECURITY.md)
- [Changelog](CHANGELOG.md)
- [Issue Templates](.github/ISSUE_TEMPLATE/)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

If you encounter any issues or have questions:
- Create an issue on GitHub
- Check the troubleshooting section above
- Review the API documentation at http://localhost:8000/docs

**⭐ If this project helps you, please give it a star!**
---

Built with ❤️ by [Brad McA](https://github.com/bradmca)
