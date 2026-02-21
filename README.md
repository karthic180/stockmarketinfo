# Stock Market Information

A lightweight, multi‑interface market data application featuring both a **web dashboard** and a **terminal interface**.
Designed to be clean, reliable, and easy to use — ideal for learning, experimentation, and portfolio demonstration.

This project showcases:

* API integration
* Offline‑first design
* Caching and fallback logic
* Web UI development with Streamlit
* CLI application design
* Configuration‑driven architecture
* Clean, maintainable Python code

All code is original and copyright‑free.

---

## Features

### 🌐 Web Dashboard

* Clean, tab‑based navigation
* Welcome page with instructions
* Market overview (local & global indices)
* Symbol lookup with fuzzy matching
* Watchlist management
* Exit tab that signals the launcher to close
* Automatic fallback to cached data when offline
* Data sourced from Yahoo Finance (via `yfinance`)

### 💻 Terminal Interface

* Simple, readable layout
* Local and global market views
* Symbol lookup with LIVE/CACHED status
* Watchlist with price and percentage change
* Clear data status line:

  * **LIVE** when online
  * **CACHED** when offline
  * Timestamp of last successful update
  * Market delay notice

---

## Data Reliability & Source Information

This application retrieves market data from **Yahoo Finance** using the `yfinance` library.

Because of how financial data providers operate:

* **Prices may be delayed by up to 15 minutes**
* **Live data is used whenever available**
* **Cached data is used automatically when live data cannot be retrieved**
* **The interface clearly indicates whether data is LIVE or CACHED**
* **Timestamps show when the last successful update occurred**

This ensures the application remains usable even without an internet connection.

---

## System Checks & Fallback Logic

Before launching the web interface, the application performs several checks:

* Python environment validation
* Streamlit availability
* Port availability (8501)
* Internet connectivity
* DNS resolution
* Yahoo Finance reachability
* Cache freshness

If any critical check fails, the launcher automatically falls back to the **terminal interface**, ensuring the application always remains functional.

---

## Project Structure

```text
├── run.py               # Launcher: diagnostics, menu, cache warm
├── web_app.py           # Streamlit web UI
├── terminal_app.py      # CLI interface
├── quotes_api.py        # Data access + caching + connectivity checks
├── fuzzy.py             # Fuzzy matching + index ticker mapping
├── settings.json        # Configuration for markets, UI, diagnostics, cache
├── cache.json           # Auto-created cache file (ignored in git)
├── requirements.txt     # Python dependencies
├── README.md            # Project documentation
└── LICENSE              # MIT license
```

---

## Getting Started

### Option A — Clone the repository (recommended)

```bash
git clone https://github.com/<your-username>/market-terminal.git
cd market-terminal
```

### Option B — If you downloaded this project as a ZIP file

If you clicked “Download ZIP” on GitHub:

* Extract the ZIP file somewhere on your computer
* Open VS Code
* Go to File → Open Folder
* Select the extracted market-terminal folder
* Open a terminal inside VS Code (Terminal → New Terminal)
* Install dependencies:

```bash
pip install -r requirements.txt
```

* Run the launcher:

```bash
python run.py
```

This works the same as cloning the repo — no Git knowledge required.

---

### Running the Application

1. (Optional) Create a virtual environment

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
```

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Launch the application

```bash
python run.py
```

You’ll see a menu:

```text
1) Launch Web Interface
2) Launch Terminal Mode
3) Exit
```

If the web interface is blocked (missing Streamlit, port in use, network issues), the launcher automatically falls back to the terminal mode.

---

## How It Works

### `run.py`

* Performs environment diagnostics
* Warms the cache on startup
* Launches web or terminal interface
* Avoids opening the browser if the web UI is unavailable

### `quotes_api.py`

* Wraps yfinance API calls
* Provides cached versions of all data functions
* Includes connectivity checks
* Ensures the app always returns data (live or cached)

### `web_app.py`

* Streamlit‑based dashboard
* Tabs for Welcome, Markets, Watchlist, Exit
* Uses cached data when live data is unavailable
* Clean, instructional layout

### `terminal_app.py`

* Text‑based interface
* Shows LIVE/CACHED status and timestamps
* Supports symbol lookup and watchlist

---

## Why I Did This

The idea behind this project was to combine multiple concepts into one unified solution for better market data tracking and learning. By integrating multiple interfaces, I could explore both the **technical** (API integration, data management, caching) and the **design** (user-friendly interfaces, fault tolerance) aspects of development. The web UI lets me experiment with Streamlit and its ease of use for building interactive dashboards, while the terminal interface ensures that the app remains functional when facing internet issues or missing dependencies.

I wanted to build a tool that could help users learn about the stock market in a practical way — offering both immediate (live data) and historical (cached data) insights, which is useful for scenarios like backtesting, portfolio monitoring, or just staying informed while working offline.

---

## What I Learned

This project was an opportunity to dive deeper into:

1. **API integration**: Integrating with Yahoo Finance through `yfinance` taught me how to retrieve and handle real-time and cached market data.
2. **Caching & offline-first design**: I learned how to implement caching to ensure data availability even without a connection, which is a vital skill for building robust, user-friendly applications.
3. **CLI and Web UI development**: Building a web-based interface with Streamlit and a terminal interface exposed me to diverse ways of creating user interfaces, ensuring accessibility across different environments.
4. **Configuration-driven architecture**: Organizing the app to be flexible through configuration files helped me develop cleaner, more maintainable code.
5. **Problem-solving**: Implementing fallback logic, automatic checks, and graceful error handling taught me how to make software resilient against unexpected issues, a key feature for production-level systems.

I now have a better understanding of how to combine real-time data with offline capabilities and how to design user-friendly interfaces that can run in different environments. This project also helped improve my understanding of working with APIs, managing dependencies, and ensuring the application’s reliability under different network conditions.

---

## Future Improvements

This project is intentionally lightweight, but there are many opportunities to extend it:

🔧 **Technical Enhancements**

* Add asynchronous data fetching for smoother updates
* Add configurable refresh intervals in the web UI
* Add persistent watchlist storage (JSON or SQLite)
* Add a background scheduler to refresh cache automatically
* Add error logging and diagnostics output to a log file

📊 **Data & Visualization**

* Add mini‑charts or sparklines for indices
* Add historical price charts using yfinance history data
* Add volume, open/high/low, and other metrics
* Add sector performance summaries

🌍 **Market Coverage**

* Add cryptocurrency data
* Add commodities (gold, oil, etc.)
* Add forex pairs
* Add ETF and mutual fund lookups

🧭 **User Experience**

* Add a dark mode toggle
* Add keyboard shortcuts in the terminal interface
* Add a “Recently Viewed Symbols” list
* Add a “Compare Symbols” feature

🚀 **Deployment**

* Package as a standalone executable
* Deploy the web UI to Streamlit Cloud or a cloud provider
* Add Docker support

---

## License

This project is licensed under the MIT License.
See LICENSE for details.

