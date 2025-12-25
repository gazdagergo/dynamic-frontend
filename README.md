# Dynamic UI Chat Application

A conversational interface where Claude dynamically generates UI components based on the conversation context.

## Project Vision

This is a POC for a chat application where:
- The UI is **dynamically generated** by Claude (no hardcoded dialogue UI)
- Users can interact through **buttons, checkboxes, inputs, and text**
- Each response can mix text and interactive UI components
- User interactions (clicks, selections) become part of the conversation

## Tech Stack

- **Frontend:** Pure HTML, CSS, and JavaScript (no build process)
- **Backend:** Python serverless functions (Vercel)
- **Deployment:** Vercel
- **AI:** Claude API with streaming support
- **Future:** AlpineJS (Iteration 2), Tailwind CSS (Iteration 5)

## Project Structure

```
dynamic-frontend/
├── index.html              # Frontend application (root)
├── api/
│   └── chat.py             # Serverless API proxy
├── vercel.json             # Vercel deployment config
├── requirements.txt        # Python dependencies
├── .env.example            # Environment variables template
└── README.md
```

## Iterations

### ✅ Iteration 1: Basic Text Chat (CURRENT)

**What's Working:**
- Text-only chat interface
- Claude API integration with streaming
- Backend API proxy (solves CORS)
- Message history
- User and assistant messages
- Vercel deployment ready

**How to Test Locally:**

Unfortunately, local testing requires the API key to be in environment variables, which is hard to set up locally. The recommended approach is to deploy to Vercel and test there.

**How to Deploy:**

1. **Fork/Clone this repo**

2. **Deploy to Vercel:**
   ```bash
   # Install Vercel CLI
   npm i -g vercel

   # Deploy
   vercel
   ```

3. **Set Environment Variable in Vercel:**
   - Go to your project in Vercel dashboard
   - Settings → Environment Variables
   - Add: `ANTHROPIC_API_KEY` = `sk-ant-...` (your API key)
   - Redeploy

4. **Test:**
   - Visit your Vercel URL
   - Start chatting with Claude
   - Messages stream in real-time

**Files:**
- `public/index.html` - Frontend application
- `api/chat.py` - Backend API proxy (handles CORS and API key)

---

### 🔲 Iteration 2: Component Rendering System

**Planned Features:**
- JSON response parsing
- Component registry and factory
- System prompt for structured output
- First dynamic component: button
- User action tracking

**Architecture:**
```javascript
// Claude returns:
{
  "message": "Would you like to start?",
  "components": [
    {"type": "button", "label": "Start Quiz", "value": "start"}
  ]
}
```

---

### 🔲 Iteration 3: Button Components

**Planned Features:**
- `button` component
- `button-group` component
- Click handlers
- Visual feedback

**Example Use Case:**
```
Assistant: "Let's start a quiz!"
[Button: Start Quiz]

User clicks button →