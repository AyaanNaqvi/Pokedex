Pokédex – Vue.js Frontend Challenge

An interactive Pokédex built with Vue 3 + Vite that fetches live Pokémon data from the PokéAPI and displays it inside a custom Pokédex interface.

Features

- Random Pokémon generator
- Official Pokémon artwork display
- Pokémon name, type, and HP stats
- Dynamic background based on Pokémon type
- Moves viewer with pagination (3 moves at a time)
- Pokédex power toggle (on/off screen)
- Custom Pokémon-style font
- Animated UI inspired by the original Pokédex

Tech Stack

- Vue 3
- Vite
- JavaScript
- CSS
- PokéAPI

API

Data is fetched from:

https://pokeapi.co/

How It Works

1. A random Pokémon ID is generated.
2. Data is fetched from the PokéAPI.
3. The UI updates with:
   - Pokémon artwork
   - Name
   - Type
   - HP
4. Background visuals change dynamically depending on Pokémon type.
5. Moves can be browsed in groups of three.

Run Locally

Clone the repository:

git clone https://github.com/AyaanNaqvi/Pokedex.git
cd pokedex

Install dependencies:

npm install

Start development server:

npm run dev

Build project:

npm run build

Live Demo

https://YOUR_RENDER_LINK_HERE

Notes

This project was built as part of a frontend internship challenge to demonstrate:

- API integration
- UI design
- Vue state management
- interactive component behavior
