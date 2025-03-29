# 🛍️ Product Support Chatbot with Gemini


## 📋 Table of Contents
- [Features](#-features)
- [Setup](#-setup)
- [Usage](#-usage)
- [Data Collection](#-data-collection)
- [Feedback System](#-feedback-system)
- [Exporting Data](#-exporting-data)
- [Statistics](#-statistics)
- [Implementation](#-implementation-details)
- [Support](#-support)

## ✨ Features
| Feature | Description |
|---------|-------------|
| 💬 Interactive Chat | Real-time conversation interface |
| 🧠 Gemini AI | Powered by Gemini 1.5 Pro model |
| 📝 Feedback Collection | Thumbs up/down rating system |
| 📊 Analytics | Real-time usage statistics |
| 💾 Data Export | Export conversations to Excel |
| ⏱️ Performance Tracking | Response latency measurement |
| 🛡️ Safety | Built-in content safeguards |

## 🚀 Setup

### Prerequisites
- Google Colab account
- [Gemini API key](https://ai.google.dev/)

### Installation
1. Open the notebook in [Google Colab](https://colab.research.google.com/)
2. Run the installation cell:
```bash
!pip install openai langchain streamlit pandas google-generativeai
genai.configure(api_key="YOUR_API_KEY_HERE")
```

## 🎯 Usage

### Starting a Session
1. Launch the notebook in Google Colab
2. Run all cells to initialize the chatbot
3. The interactive interface will appear with:
   - Text input field at the top
   - Conversation history panel
   - Feedback controls at the bottom

### Example Interaction
```python
YOU: "How do I reset my device to factory settings?"
BOT: "To reset your device: 1) Go to Settings... [detailed instructions]"
```
## 📝 Data Collection

The system automatically tracks and stores the following metrics for every interaction:

| Metric | Data Type | Description | Example Value |
|--------|-----------|-------------|---------------|
| `id` | UUID | Unique interaction identifier | "a1b2c3d4-e5f6-..." |
| `timestamp` | ISO-8601 | Exact time of interaction | "2024-06-18T14:30:45Z" |
| `prompt` | String | User's original question | "How to reset device?" |
| `response` | String | AI-generated answer | "Press reset button for 5s..." |
| `latency` | Float | Response time in seconds | 1.452 |
| `feedback` | Enum | User rating ("Good"/"Bad") | "Good" |
| `comments` | String | Optional feedback notes | "Step 3 was unclear" |

## 💬 Feedback System

### 🛠️ Core Components
```python
# Feedback UI Implementation
feedback_components = {
    "buttons": {
        "positive": {"emoji": "👍", "label": "Helpful", "color": "#4CAF50"},
        "negative": {"emoji": "👎", "label": "Unhelpful", "color": "#F44336"}
    },
    "comment_box": {
        "placeholder": "What could we improve? (Optional)",
        "max_length": 500
    }
}
```
sequenceDiagram
    participant User
    participant UI
    participant Database
    
    User->>UI: Submits feedback (👍/👎)
    UI->>User: Shows confirmation
    UI->>Database: Records:
        - Timestamp
        - Interaction ID
        - Rating
        - Comments (if any)
    Database->>UI: Acknowledges save
    UI->>User: Updates stats display

🔄 Feedback Analysis (Last 30 Days)
---------------------------------
Total Ratings: 1,243
Positive: 87% (1,081)
Negative: 13% (162)

Top Improvement Areas:
1. Accuracy (42%)
2. Clarity (33%)
3. Completeness (25%)

Recent Comments:
- "The steps worked perfectly!"
- "Missing info about model XYZ"

