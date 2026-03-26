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
  App.jsx              # Root component — holds transactions state, wires components
  Summary.jsx          # Displays income, expenses, balance (calculates from transactions)
  TransactionForm.jsx  # Form to add a new transaction (owns its own form state)
  TransactionList.jsx  # Filterable table of transactions (owns filter state)
  App.css              # Component styles
  main.jsx             # React entry point
  index.css            # Global styles
index.html
vite.config.js
```

## Architecture

- **State ownership**: `transactions` array lives in `App` and is passed down as props
- **TransactionForm** manages its own local form state (`description`, `amount`, `type`, `category`) and calls `onAdd(transaction)` when submitted
- **TransactionList** manages its own local filter state (`filterType`, `filterCategory`) and receives `transactions` as a prop
- **Summary** receives `transactions` and computes `totalIncome`, `totalExpenses`, and `balance` internally
- `categories` is defined locally in both `TransactionForm` and `TransactionList` (not yet shared)

## Common Commands

```bash
npm run dev       # Start dev server (localhost:5173)
npm run build     # Production build
npm run preview   # Preview production build
npm run lint      # Run ESLint
```

## Key Concepts

- **Transactions** have: `id`, `description`, `amount` (number), `type` (`"income"` | `"expense"`), `category`, `date`
- **Categories**: food, housing, utilities, transport, entertainment, salary, other
- Filtering is done client-side by type and category

## Notes

- No routing — single page
- No state management library — plain `useState`
- No tests configured yet
