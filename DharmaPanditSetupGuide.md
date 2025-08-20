# Dharma AI Pandit Setup Guide

This guide will help you set up your immersive Dharma AI Pandit Ji with video avatar and voice, step by step (even a 2-year-old can follow!).

---

## 1. Choose Your AI API

- **Recommended:** OpenAI (ChatGPT), Google Gemini, or any chatbot API.
- **For video avatar:** D-ID (https://www.d-id.com/) is easy to use and supports real-time talking avatars.

---

## 2. Get Your API Keys

- **AI Chat API:**
  - Sign up at [OpenAI](https://platform.openai.com/) or [Google Gemini](https://ai.google.com/).
  - Create a new API key and copy it.
- **D-ID Video Avatar API:**
  - Sign up at [D-ID](https://www.d-id.com/).
  - Get your API key from the dashboard.

---

## 3. Add Your API Keys to Code

- Open `pandit.html`.
- Find the comment: `// const API_KEY = 'YOUR_API_KEY_HERE';`
- Paste your API key there (replace `'YOUR_API_KEY_HERE'`).
- For D-ID, follow their docs to embed the video avatar (usually an iframe or SDK snippet).

---

## 4. Connect to the AI API

- Replace the `getPanditResponse()` function in `pandit.html` with code that sends your question to the AI API and gets the answer.
- Example (OpenAI):

```js
async function getPanditResponse(query) {
  const response = await fetch('https://api.openai.com/v1/chat/completions', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer YOUR_API_KEY_HERE'
    },
    body: JSON.stringify({
      model: 'gpt-3.5-turbo',
      messages: [{role: 'user', content: query}]
    })
  });
  const data = await response.json();
  return data.choices[0].message.content;
}
```

---

## 5. Add the Video Avatar

- Use D-ID's embed code or SDK to show the talking avatar in the `#pandit-video` div.
- Pass the AI's response text to the avatar so it speaks.
- See D-ID docs: https://docs.d-id.com/docs

---

## 6. Test Everything

- Open `pandit.html` in your browser.
- Type a question or use the voice button.
- The AI Pandit should answer and speak.
- The video avatar should talk (if D-ID is set up).

---

## 7. (Optional) Add More Features

- Connect to a database of mantras/rituals.
- Add live Pandit video call (Twilio/Agora).
- Improve UI with images, chants, etc.

---

## Troubleshooting

- If something doesn't work, check your API keys and internet connection.
- Read the docs for your chosen API (OpenAI, D-ID, etc.).
- Ask for help if stuck!

---

## You Did It!

Your Dharma AI Pandit Ji is ready to guide users with immersive video and voice. 🙏
