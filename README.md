
# 🌍 Travel Tracker

A full-stack web app to visually track your travel journey. Mark the countries you've visited on a world map rendered using **SVG**, with backend storage powered by **PostgreSQL**.

## 🛠 Tech Stack

- **Node.js** – JavaScript runtime
- **Express.js** – Web framework
- **EJS** – Templating engine
- **PostgreSQL** – Relational database for storing visited countries
- **SVG** – Scalable Vector Graphics for rendering the world map
- **CSS / Custom Styles** – For map styling and interaction

## ✨ Features

- 🗺️ **Interactive SVG World Map** – Each country is an SVG `<path>` with hover info
- 📍 **Mark Countries Visited** – Enter a country name to highlight it on the map
- 🧑‍🤝‍🧑 **Multi-user Support** – Switch between users/family members with custom colors
- 📋 View list of visited countries (optional UI feature)
- 🧠 Intelligent server logic that syncs map and database

## 📸 How It Works

- The map is an inline **SVG element**, each country defined by a `<path>` with an `id` (country code) and `title` (country name).
- When you add a country via the input form, it's stored in PostgreSQL and dynamically styled (e.g., filled/highlighted) using EJS and CSS.
- Users can switch profiles via a user tab interface, each with their own travel data.

## 🚀 Getting Started

### Prerequisites

- Node.js (v14+)
- PostgreSQL installed and running
- npm (Node package manager)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Nipun-Gupta-codes/Travel-Tracker.git
   cd Travel-Tracker
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up PostgreSQL**

   - Create a database:
     ```sql
     CREATE DATABASE travel_tracker;
     ```

   - Example table structure:
     ```sql
     CREATE TABLE users (
       id SERIAL PRIMARY KEY,
       name TEXT NOT NULL,
       color TEXT NOT NULL
     );

     CREATE TABLE visited_countries (
       id SERIAL PRIMARY KEY,
       user_id INTEGER REFERENCES users(id),
       country_code VARCHAR(5),
       country_name TEXT
     );
     ```

4. **Create a `.env` file**
   ```
   DB_HOST=localhost
   DB_PORT=5432
   DB_USER=your_username
   DB_PASSWORD=your_password
   DB_NAME=travel_tracker
   ```

5. **Run the application**
   ```bash
   npm start
   ```

6. Open [http://localhost:3000](http://localhost:3000) in your browser.


## 🧩 Key Components

- **SVG World Map:** Located inside `index.ejs`, each country is identified using `path` elements with `id` as ISO codes.
- **User Tabs:** Rendered dynamically from DB users, with forms to switch or add members.
- **Add Country:** Simple POST form with server-side validation and database update.

## 🧱 Possible Enhancements

- 🔒 Add user authentication (e.g., login/session)
- 📊 Travel stats dashboard
- 🗂️ Country filters by continent or year visited
- 📍 Use Leaflet.js or D3 for dynamic map interaction
- 💾 Export travel data to CSV or PDF

## 🤝 Contributing

Pull requests are welcome. Feel free to fork the project and submit improvements!


Made with ❤️ by traveler, for travelers.
