# Book-Land 📚

A single-page book search web app built with vanilla **HTML, CSS and JavaScript**.
Book-Land lets you search 2,000+ books, view covers, details, reviews and
read links powered by the **Google Books API**. It also includes a chatbot
("MgAlien"), a favourites system and account (sign-up / login / password reset) flows.

> Group project for the HTML & CSS course, extended with JavaScript.
> Live site: https://book-land-y-dev.netlify.app/

## Features

- 🔎 Real-time book search via the Google Books API
- 🖼️ Book cover previews, author/title info and preview links
- 🤖 Built-in chatbot ("MgAlien")
- ⭐ Reviews and favourites system
- 👥 About / team page
- 🔐 Sign-up, login and password-reset flows
- 📱 Fully responsive layout

## Tech Stack

| Layer      | Technology |
| ---------- | ---------- |
| Markup     | HTML5      |
| Styling    | CSS3 (custom + image hover effects) |
| Behaviour  | Vanilla JavaScript (ES6) |
| Data       | Google Books API |
| Icons      | Font Awesome 6 |
| Fonts      | Google Fonts (Bricolage Grotesque, REM) |

## Project Structure

```text
bookland/
├── index.html              # Main single page (home, search, about, chatbot, auth)
├── pages/
│   ├── login.html          # Login screen
│   ├── reset-password.html # Request password reset (sends 6-digit code)
│   ├── verify-code.html    # Enter 6-digit code + set new password
│   └── new-password.html   # Alternate new-password screen
├── assets/
│   ├── css/
│   │   ├── home.css         # Core styles for the main page
│   │   └── imagehover.css   # Image hover effect library
│   ├── js/
│   │   └── home.js          # App logic + Google Books API integration
│   └── images/              # Logo, fallback cover, book art, misc assets
└── README.md
```

## Performance Optimizations

The site has been tuned for fast first paint and low network cost:

- **Resource hints** — `preconnect` / `dns-prefetch` to Google Fonts,
  cdnjs (Font Awesome) and `books.google.com` so connections are opened
  before the browser discovers those assets.
- **Non-render-blocking CSS** — Font Awesome is loaded with
  `media="print" onload="this.media='all'"` (with a `<noscript>` fallback)
  so it no longer blocks first paint.
- **Optimized hero images** — the LCP cover uses `fetchpriority="high"` and
  `decoding="async"`; the duplicate decorative copies use `loading="lazy"`.
- **Removed flaky third-party redirects** — the social sign-up icons and the
  book-cover fallback previously pointed at `rb.gy` short links (extra
  redirects = slower, unreliable). They now use self-contained Font Awesome
  brand icons and a local `noresults.png` fallback.
- **Deferred JavaScript** — `Home.js` is loaded with `defer`.

## Running Locally

No build step is required — it is a static site.

```bash
# from the project root
python3 -m http.server 8000
# then open http://localhost:8000
```

Or just open `index.html` directly in a browser.

## Deployment

The site is static and can be deployed to any static host
(Netlify, GitHub Pages, Vercel, etc.) by publishing the repository root.

## Team — Y-Dev

Designed and developed by the Y-Dev team, University of Computer Studies (Pyay).
