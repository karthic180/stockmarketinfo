# Stock Market Information

A lightweight, multi-interface market data application featuring both a **web dashboard** and a **terminal interface**.
Designed to be clean, reliable, and easy to use — ideal for learning, experimentation, and portfolio demonstration.

## This project showcases:

* API integration
* Offline-first design
* Caching and fallback logic
* Web UI development with Streamlit
* CLI application design
* Configuration-driven architecture
* Clean, maintainable Python code

All code is original and copyright-free.

---

## Features

### Web Dashboard

* **Clean, tab-based navigation**
* **Welcome page** with instructions
* **Market overview** (local & global indices)
* **Symbol lookup** with fuzzy matching
* **Watchlist management**
* **Exit tab** that signals the launcher to close
* **Automatic fallback** to cached data when offline
* Data sourced from **Yahoo Finance** (via `yfinance`)

### Terminal Interface

* **Simple, readable** Bloomberg-style layout
* **Local and global market views**
* **Symbol lookup** with LIVE/CACHED status
* **Watchlist with price and percentage change**
* **Clear data status line**:

  * **LIVE** when online
  * **CACHED** when offline
  * Timestamp of last successful update
  * Market delay notice

### Smart Caching System

* **Automatically warms the cache** on startup
* **Stores**:

  * Index data
  * Quote data
  * Last update timestamp
* **Uses cached data** when:

  * Internet is unavailable
  * Yahoo Finance cannot be reached
  * API calls fail
* Ensures the app **always works** offline

### Configuration-Driven

All behavior is controlled through `settings.json`, including:

* Local and global index lists
* Default market mode
* UI preferences
* Diagnostics toggles
* Cache settings

No Python code needs to be edited to change markets or UI behavior.

---

## Project Structure

```
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

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/market-terminal.git
cd market-terminal
```

### 2. (Optional) Create a virtual environment

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the launcher

```bash
python run.py
```

You’ll see a menu:

```
1) Launch Web Interface
2) Launch Terminal Mode
3) Exit
```

If the web interface is blocked (missing Streamlit, port in use, network issues), the launcher automatically falls back to the terminal mode.

---

### How It Works

#### run.py

* Performs environment diagnostics
* Warms the cache on startup
* Launches the web or terminal interface
* Avoids opening the browser if the web UI is unavailable

#### quotes_api.py

* Wraps `yfinance` API calls
* Provides cached versions of all data functions
* Includes connectivity checks
* Ensures the app always returns data (live or cached)

#### web_app.py

* **Streamlit-based dashboard**
* Tabs for **Welcome**, **Markets**, **Watchlist**, **Exit**
* Uses cached data when live data is unavailable
* Clean, instructional layout

#### terminal_app.py

* Text-based interface
* Shows **LIVE/CACHED** status and timestamps
* Supports symbol lookup and watchlist

---

## Why This Project Is in My Portfolio

This project demonstrates:

* Practical API usage
* Offline-first design
* Error-resilient architecture
* Clean UI/UX in both web and terminal environments
* Configuration-driven development
* Python best practices
* Real-world problem solving (fallbacks, caching, diagnostics)

It’s a great example of building something robust, user-friendly, and technically interesting.

---

## License

This project is licensed under the **MIT License**.
See `LICENSE` for details.

---

### Code Considerations

* **Consistency**: Standardize variable names, functions, and format across all files. E.g., use `snake_case` consistently for variable names.
* **Error Handling**: Ensure robust handling of API failures, particularly when fallback data is used.
* **Documentation**: Expand the README to include instructions on testing, contribution, and potential expansion ideas.

## Future Improvements
This project is intentionally lightweight, but there are many opportunities to extend it:

Technical Enhancements
Add asynchronous data fetching for smoother updates

Add configurable refresh intervals in the web UI

Add persistent watchlist storage (JSON or SQLite)

Add a background scheduler to refresh cache automatically

Add error logging and diagnostics output to a log file

 Data & Visualization
Add mini‑charts or sparklines for indices

Add historical price charts using yfinance history data

Add volume, open/high/low, and other metrics

Add sector performance summaries

 Market Coverage
Add cryptocurrency data

Add commodities (gold, oil, etc.)

Add forex pairs

Add ETF and mutual fund lookups

 User Experience
Add a dark mode toggle

Add keyboard shortcuts in the terminal interface

Add a “Recently Viewed Symbols” list

Add a “Compare Symbols” feature

 Deployment
Package as a standalone executable

Deploy the web UI to Streamlit Cloud or Azure

Add Docker support

These improvements can help demonstrate deeper engineering skills and make the project even more impressive in interviews.
