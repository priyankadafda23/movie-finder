# 🎬 Movie Finder App

A sleek and responsive movie search application built with **SvelteKit**, styled with **Bootstrap**, and powered by the **TMDB API**. Users can search for movies by name and also see trending movies on the homepage.


## 🌟 Features

- 🔍 **Search** movies by name using TMDB’s Search API
- 🔥 **Trending Movies** shown on initial load using TMDB’s Trending API
- 🎨 Beautiful **dark theme** UI using Bootstrap
- 🃏 Movie cards with:
        - Poster
        - Title
        - Rating with star icon
- 🖱️ Hover effects that **lift** movie cards
- 📱 Fully responsive layout
- 🎯 Center-aligned Movie Finder heading and inputs
- 📦 Clean and organized Svelte components


## 🚀 Getting Started

### 1. Install Dependencies
        npm install

### 2. Run the App
        npm run dev

    Then open (http://localhost:5173) in your browser.


## 📁 Project Structure 
    │
    ├── src/
    │   ├── lib/
    │   │       ├── components/
    │   │       │    ├── SearchBar.svelte
    │   │       │    └── MovieCard.svelte
    │   │       └── store.js
    │   ├── routes/
    │   │       ├── movie/
    │   │       │      └── [id]/
    │   │       │       └── +page.svelte
    │   │       ├── +page.svelte
    │   │       └── +layout.svelte
    │   ├── app.css
    │   └── app.html
    ├── static/
    ├── README.md
    ├── package.json
    └──     :

## 💅 Styling & UI
    ~ Uses Bootstrap 5.3 via CDN
    ~ Font customization and dark background
    ~ Spacing and layout managed using Bootstrap grid & flex utilities
    ~ Smooth card hover animation


## 📌 Todo / Future Improvements
    ~ Add movie detail page with more info
    ~ Pagination for search results
    ~ Save favorite movies locally
    ~ Implement search bar filtering
    ~ Add more APIs for different movie sources
    ~ Improve responsiveness on smaller screens
    ~ Add loading animation for API requests


## 🤝 Acknowledgements
    ~ The Movie Database (TMDB) for API
    ~ Svelte for the UI framework
    ~ Bootstrap for styling


Developed with ❤️ by Priyanka Dafda