# CLAUDE.md

## Project Overview

**Finance Tracker** — a React single-page app for tracking personal income and expenses. Built with Vite + React 19.

## Tech Stack

- **Framework**: React 19 (JSX)
- **Build tool**: Vite 7
- **Linting**: ESLint 9
- **Styling**: Plain CSS (`App.css`, `index.css`)
- **No backend / no database** — state is in-memory only (no persistence across page reloads)

## Project Structure

```
src/
  App.jsx       # Main component — all app logic lives here
  App.css       # Component styles
  main.jsx      # React entry point
  index.css     # Global styles
index.html
vite.config.js
```

## Common Commands

```bash
npm run dev       # Start dev server (localhost:5173)
npm run build     # Production build
npm run preview   # Preview production build
npm run lint      # Run ESLint
```

## Key Concepts

- **Transactions** have: `id`, `description`, `amount` (string), `type` (`"income"` | `"expense"`), `category`, `date`
- **Categories**: food, housing, utilities, transport, entertainment, salary, other
- Filtering is done client-side by type and category
- Amounts are stored as strings — be careful with arithmetic (parseFloat needed)

## Notes

- No routing — single page
- No state management library — plain `useState`
- No tests configured yet
