# Lectern — PDF Audio Reader

Drop in a PDF and have it read aloud in your browser: play/pause, skip
sentence by sentence, scrub a progress rail, and watch elapsed/remaining
time update live as it reads.

**Live site:** https://niro-tech98.github.io/pdf-audio-reader/

Everything runs client-side — text extraction ([pdf.js](https://mozilla.github.io/pdf.js/))
and speech (the browser's built-in [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API))
both happen locally. No PDF is ever uploaded anywhere, so anyone can open
the link and read their own document privately.

## Notes & limitations

- Works on text-based PDFs. Scanned/image-only pages have no extractable
  text, so they can't be read aloud.
- Voice quality and selection depend on your browser/OS's installed
  speech voices (Chrome, Edge, and Safari all ship a reasonable set).
- Reading position and voice/speed preferences are saved per browser via
  `localStorage`, keyed by filename + size — reopening the same file in
  the same browser resumes where you left off. The PDF itself isn't
  stored anywhere.

## Development

This is a single static page (`index.html`) with no build step. A GitHub
Actions workflow (`.github/workflows/deploy-pages.yml`) publishes it to
GitHub Pages on every push.

To enable the live link the first time, GitHub Pages must be turned on
for this repository: **Settings → Pages → Source: GitHub Actions**. The
workflow will then deploy automatically after that's set once. The repo
also needs to be public (or on a GitHub plan that supports Pages for
private repos).
