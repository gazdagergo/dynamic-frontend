# Dynamic UI Chat Application

A conversational interface where Claude dynamically generates UI components based on the conversation context.

## Project Vision

This is a POC for a chat application where:
- The UI is **dynamically generated** by Claude (no hardcoded dialogue UI)
- Users can interact through **buttons, checkboxes, inputs, and text**
- Each response can mix text and interactive UI components
- User interactions (clicks, selections) become part of the conversation

## Tech Stack

- **No build process** - Pure HTML, CSS, and JavaScript
- **AlpineJS** - Lightweight reactivity (added in Iteration 2)
- **Tailwind CSS** - Styling (added in Iteration 5)
- **Claude API** - AI backend with streaming support

## Iterations

### ✅ Iteration 1: Basic Text Chat (CURRENT)

**What's Working:**
- Text-only chat interface
- Claude API integration with streaming
- Message history
- User and assistant messages
- API key management (stored locally)

**How to Test:**
1. Open `index.html` in a browser
2. Enter your Anthropic API key (starts with `sk-ant-`)
3. Start chatting with Claude
4. Messages stream in real-time

**Files:**
- `index.html` - Complete working chat app

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