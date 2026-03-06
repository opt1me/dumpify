# Capture — Brain Dump Tool

A voice-first personal organisation tool. Speak or type a brain dump, and it structures your thoughts into categorised, actionable tasks. Works as a standalone HTML file or as an installable Progressive Web App (PWA).

---

## Features

- **Voice capture** — speak your thoughts using your browser's built-in speech recognition (Chrome/Edge on Android and desktop)
- **AI structuring** — sends your dump to an AI provider of your choice and returns a clean, categorised task list
- **Offline parsing** — keyword-based local parsing with no API required, works anywhere
- **Custom categories** — define your own categories with names, colours, and keywords
- **History** — every structured dump is saved locally in your browser
- **PWA installable** — add to your Android home screen for a native app feel
- **Export** — download all your captures as JSON
- **Bring your own API key** — supports Anthropic (Claude), OpenAI, and Azure OpenAI

---

## Hosting on GitHub Pages

1. Fork or create a new GitHub repository
2. Upload all files to the repository root:
   - `index.html`
   - `manifest.json`
   - `sw.js`
3. Go to **Settings → Pages** in your repository
4. Set source to **Deploy from a branch**, branch **main**, folder **/ (root)**
5. Wait ~60 seconds, then visit `https://yourusername.github.io/your-repo-name`

Once hosted on HTTPS, Chrome on Android will offer an **Add to home screen** prompt automatically.

---

## API Configuration

Open the app and go to **Settings → AI Provider**. Choose your provider and enter your credentials. Keys are stored only in your browser's local storage and never sent anywhere except directly to your chosen API endpoint.

### Anthropic (Claude)
- Get an API key at [console.anthropic.com](https://console.anthropic.com)
- Recommended model: Claude Sonnet 4

### OpenAI
- Get an API key at [platform.openai.com](https://platform.openai.com)
- Recommended model: GPT-4o

### Azure OpenAI (recommended for work use)
- Enter your Azure endpoint, API key, deployment name, and API version
- All data is processed within your Azure tenant — nothing leaves your organisation

If no provider is configured, the app falls back to offline keyword-based parsing automatically.

---

## Custom Categories

Go to **Settings → Categories** to:
- Rename any category
- Pick a colour
- Add comma-separated keywords used by the offline parser

The AI structuring prompt is built dynamically from your categories, so it always classifies into your own buckets.

---

## Privacy

- All captures are stored in your browser's local storage only
- No data is sent to any server unless you configure an AI provider and click "Structure this"
- API keys are stored locally in your browser and never transmitted anywhere except your chosen API endpoint
- When using Azure OpenAI, data stays within your Azure tenant

---

## Browser Support

| Browser | Voice capture | AI structuring | Offline parse | PWA install |
|---|---|---|---|---|
| Chrome (Android) | ✅ | ✅ | ✅ | ✅ |
| Edge (desktop) | ✅ | ✅ | ✅ | ✅ |
| Chrome (desktop) | ✅ | ✅ | ✅ | ✅ |
| Safari (iOS) | ⚠️ Limited | ✅ | ✅ | ✅ |
| Firefox | ❌ | ✅ | ✅ | ❌ |

Voice capture requires microphone permission. On first use, your browser will prompt you to allow access.

---

## Local Development

No build step required. Just open `index.html` in Chrome or Edge. Note that microphone access via `getUserMedia` may be restricted on `file://` URLs in some browsers — hosting on a local server or GitHub Pages resolves this.

```bash
# Simple local server using Python
python3 -m http.server 8080
# Then open http://localhost:8080
```

---

## Roadmap ideas

- Weekly summary view
- Email yourself the structured list
- Recurring task detection
- Calendar integration
- React Native / Play Store build
