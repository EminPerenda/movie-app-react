# 🎬 Movie App

A modern movie discovery app built with React and Vite. Search thousands of movies via **The Movie Database (TMDB) API**, and see a live "Trending Movies" list powered by **Appwrite**, which tracks what people are searching for in real time.

## ✨ Features

- 🔍 **Live search** — Debounced search-as-you-type against the TMDB API
- 🔥 **Trending movies** — Automatically surfaces the most-searched titles, powered by an Appwrite database
- 🎞️ **Movie details at a glance** — Poster, rating, language, and release year for every result
- ⚡ **Fast & modern stack** — Vite + React 19 + Tailwind CSS 4
- 💅 **Responsive UI** — Clean, dark-themed interface that works across screen sizes

## 🛠️ Tech Stack

| Category | Technology |
|---|---|
| Framework | [React 19](https://react.dev/) |
| Build Tool | [Vite](https://vite.dev/) |
| Styling | [Tailwind CSS 4](https://tailwindcss.com/) |
| Backend / Database | [Appwrite](https://appwrite.io/) |
| Movie Data | [TMDB API](https://developer.themoviedb.org/docs) |
| Utilities | [react-use](https://github.com/streamich/react-use) (debouncing) |
| Linting | [oxlint](https://oxc.rs/) |

## 📋 Prerequisites

- [Node.js](https://nodejs.org/) v18 or later
- npm (bundled with Node.js)
- A [TMDB API key](https://developer.themoviedb.org/docs/getting-started) (free)
- An [Appwrite](https://appwrite.io/) project with a database configured to store search metrics

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd movie-app-react
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env.local` file in the project root and add the following:

```env
VITE_TMDB_API_KEY=your_tmdb_api_read_access_token
VITE_APPWRITE_PROJECT_ID=your_appwrite_project_id
VITE_APPWRITE_DATABASE_ID=your_appwrite_database_id
VITE_APPWRITE_COLLECTION_ID=your_appwrite_collection_id
```

> **Note:** The Appwrite collection referenced above should include the following attributes: `searchTerm` (string), `count` (integer), `movie_id` (integer), and `poster_url` (string).

### 4. Run the development server

```bash
npm run dev
```

The app will be available at `http://localhost:5173`.

## 📦 Available Scripts

| Command | Description |
|---|---|
| `npm run dev` | Starts the local development server with hot module reloading |
| `npm run build` | Builds the app for production into the `dist/` folder |
| `npm run preview` | Serves the production build locally for a final check |
| `npm run lint` | Runs oxlint to check for code issues |

## 📁 Project Structure

```
movie-app-react/
├── public/                    # Static assets (icons, images)
├── src/
│   ├── assets/                # App-level images and icons
│   ├── components/
│   │   ├── MovieCard.jsx      # Displays an individual movie's poster, rating, and info
│   │   ├── Search.jsx         # Search input with change handler
│   │   └── Spinner.jsx        # Loading indicator
│   ├── appwrite.js            # Appwrite client setup and search-tracking logic
│   ├── App.jsx                # Main application component and data-fetching logic
│   ├── App.css / index.css    # Global and component styling
│   └── main.jsx                # App entry point
├── .env.local                  # Environment variables (not committed)
├── vite.config.js              # Vite configuration
└── package.json
```

## ⚙️ How It Works

1. On load, the app fetches currently popular movies from TMDB and displays the top trending searches from Appwrite.
2. As the user types in the search bar, the query is debounced (500ms) and sent to the TMDB search endpoint.
3. Each successful search updates a counter in the Appwrite database, which powers the "Trending Movies" section for all users.

## 🔒 Environment Variables

This project keeps all sensitive keys out of source control. Ensure `.env.local` is present locally and never committed — it's already excluded via `.gitignore`.
