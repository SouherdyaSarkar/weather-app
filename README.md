# 🌤️ Weather Forecast App

A simple, good-looking weather app built with **HTML, CSS and vanilla JavaScript**. Type in any city name and get the current weather instantly: temperature, what it feels like, humidity, min/max temperature, wind speed and a matching weather icon. Data comes from the [OpenWeatherMap](https://openweathermap.org/) API.

---

## ✨ Features

- 🔍 Search weather by city name
- 🌡️ Current temperature (°C) and "feels like" temperature
- 💧 Humidity, 🌬️ wind speed, and 🔺🔻 min / max temperature
- 🖼️ Weather icon that changes with the conditions (clouds, clear, rain, drizzle, mist, snow, haze)
- ⚠️ Friendly error message for invalid city names
- 🎨 Gradient card UI with a custom background, using the Poppins and Playwrite IT Moderna Google Fonts

---

## 🛠️ Tech Stack

| Layer      | Technology                                  |
| ---------- | ------------------------------------------- |
| Structure  | HTML5                                       |
| Styling    | CSS3 (Flexbox, gradients, Google Fonts)     |
| Logic      | JavaScript (ES6, `async/await`, Fetch API)  |
| Data       | OpenWeatherMap "Current Weather" API        |

---

## 📁 Project Structure

```
weather-app/
├── index.html        # Page markup
├── style.css         # Styles
├── app.js            # API call + DOM updates
└── images/           # All icons and the background image
    ├── 3.jpg         # Page background
    ├── search.png
    ├── humidity.png
    ├── wind.png
    ├── clouds.png
    ├── clear.png
    ├── rain.png
    ├── drizzle.png
    ├── mist.png
    ├── snow.png
    └── haze.png
```

> Make sure every image listed above exists in the `images/` folder, or the matching icon won't load.

---

## 🚀 Getting Started

### Prerequisites

- A modern web browser (Chrome, Edge, Firefox, Safari)
- A free **OpenWeatherMap API key**
- *(Optional)* [VS Code](https://code.visualstudio.com/) with the **Live Server** extension

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

### 2. Get an OpenWeatherMap API key

1. Create a free account at [openweathermap.org](https://openweathermap.org/api).
2. Go to **My API keys** in your profile and copy your key.
3. New keys can take a short while (up to a couple of hours) to activate, so if you get errors right away, wait and try again.

### 3. Add your API key

Open `app.js` and replace the value of `apiKey` with your own key:

```js
const apiKey = "YOUR_API_KEY_HERE";
```

### 4. Run the app

**Option A: open the file directly**
Double-click `index.html` and it opens in your browser.

**Option B: use VS Code Live Server (recommended)**
1. Open the project folder in VS Code.
2. Right-click `index.html` and choose **Open with Live Server**.

**Option C: use a simple local server**

```bash
# Python 3
python -m http.server 5500

# or Node.js
npx serve .
```

Then visit `http://localhost:5500`.

---

## 🧭 How to Use

1. Type a city name (for example `Kolkata`) into the search box.
2. Click the search button.
3. The weather card appears with the current conditions.
4. If the city isn't found, an **"Invalid city name"** message is shown instead.

---

## ⚙️ How It Works

1. The user enters a city and clicks the search button, which calls `weatherCheck()`.
2. The app sends a request to the OpenWeatherMap endpoint:

   ```
   https://api.openweathermap.org/data/2.5/weather?units=metric&q={city}&appid={apiKey}
   ```

3. If the API returns `404`, the weather card is hidden and the error message is shown.
4. Otherwise, the JSON response is parsed and the DOM is updated with the city name, temperature, humidity, min/max temperature, wind speed and description.
5. The icon is chosen from `data.weather[0].main` (Clouds, Clear, Rain, Drizzle, Mist, Snow, Haze).

---

## 🔐 Security Note: Protect Your API Key

Because this is a front-end only project, your API key is visible to anyone who opens the browser's developer tools. To reduce the risk:

- **Never commit your real key to a public repository.** Keep a placeholder in the committed code, or load the key from a separate file that is listed in `.gitignore`.
- **Regenerate your key** from the OpenWeatherMap dashboard if it was ever pushed to GitHub or shared publicly.
- For production use, send requests through a small **backend proxy** (Node/Express, Cloudflare Workers, etc.) so the key stays on the server.

---

## 🐞 Known Issues & Improvements

- [ ] **Wind speed unit:** with `units=metric` the API returns wind speed in **m/s**, but the app labels it `km/hr`. Either change the label to `m/s` or multiply by `3.6`.
- [ ] **Unhandled weather types:** conditions such as `Thunderstorm`, `Smoke`, `Fog` or `Dust` don't have an icon yet, so the previous icon stays on screen. Add a default icon.
- [ ] **Pressure** is queried in the code (`.pressurev`) but not shown in the UI.
- [ ] Pressing **Enter** doesn't trigger a search. Add a `keypress` listener on the input.
- [ ] Handle **network errors and other status codes** (401 invalid key, 429 rate limit) with `try/catch`.
- [ ] Fix the markup in `index.html`: the `</div>` closing the search container sits inside the `<button>`, and the class name `min&maxtemp` should be renamed to something like `min-max-temp`.
- [ ] Add a **7-day forecast** and a "use my location" button (Geolocation API).

---

## 🤝 Contributing

Contributions, issues and feature requests are welcome. Fork the repo, create a branch, and open a pull request.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🙏 Acknowledgements

- [OpenWeatherMap](https://openweathermap.org/) for the weather data
- [Google Fonts](https://fonts.google.com/) for Poppins and Playwrite IT Moderna
