# Should I Sleep or Code Tonight?

A fun web app that helps you decide whether to sleep or code tonight — with a 50/50 chance determined by RNG (random number generation).

[Try it now!](https://penguinerza.github.io/sleep-or-code)

## What It Does

1. Click the **"The answer is..."** button.
2. A drum roll plays while suspense builds.
3. The app randomly picks one of two verdicts:
   - **Sleep 😴** — accompanied by a sleeping-cat GIF and a celebratory sound.
   - **Code 👨‍💻** — accompanied by a coding-cat GIF, a vine-boom sound effect, and keyboard typing sounds.
4. If the verdict is "Code", a **"Try again?"** button eventually appears so you can keep hoping for sleep.

> Maybe you'll find something if you really don't want to code...

## Tech Stack

- **[SvelteKit](https://kit.svelte.dev/)** — frontend framework
- **[Tailwind CSS](https://tailwindcss.com/)** — utility-first styling
- **[Howler.js](https://howlerjs.com/)** — audio playback for sound effects
- **[Vite](https://vitejs.dev/)** — build tool
- Deployed to **GitHub Pages** via `gh-pages`

## Running Locally

```bash
# Install dependencies
npm install

# Start the dev server
npm run dev
```

Then open [http://localhost:5173](http://localhost:5173) in your browser.

## Building & Deploying

```bash
# Build for production
npm run build

# Deploy to GitHub Pages
npm run deploy
```
