# GitStat — GitHub Profile Stats

A clean, minimal single-file web app that fetches and displays comprehensive GitHub profile statistics for any public user.

---

## Features

### Profile Overview
- Avatar, name, bio, location, company, blog, and Twitter/X link
- Followers / following ratio
- Account age badge
- Dynamic badges: Open to Work, Veteran, follower count, star count, gists
- Copy profile URL and GitHub Sponsors link

### Key Stats (8 cards with animated counters)
- Public repositories
- Total stars across all repos
- Total forks + watcher count
- Followers and following
- Open issues across all repos
- Average repo size (KB)
- Public gists

### Highlights
- Most starred repository
- Most forked repository
- First repo ever created
- Most recently active repo
- Total code size across all repos
- Member since year

### Tech Stack
- Top languages — color-coded bar chart
- Topics & tags cloud — pulled from all repo topics
- Licenses used — ranked bar chart
- Push activity by day — weekday vs weekend bar chart

### Contributions
- Current streak, longest streak, active repos (last 30 days)
- 52-week contribution heatmap (light/dark mode aware)

### Repositories
- Top 10 repos sorted by stars
- Stars, forks, open issues, language, license, last push time
- Topics shown per repo
- Fork badge on forked repos

### Compare Mode
- Enter a second username to compare side-by-side
- Highlights the winner in each category (followers, stars, forks, gists, account age, etc.)

### UX
- Dark / light mode toggle (respects system preference)
- Animated number counters on load
- Export stats as `.txt` file
- Smooth entrance animations
- Responsive layout (mobile-friendly)

---

## Tech Stack

| Layer | Choice |
|-------|--------|
| Markup | HTML5 |
| Styling | Vanilla CSS with CSS custom properties |
| Logic | Vanilla JavaScript (ES2020+) |
| Fonts | DM Sans + DM Mono (Google Fonts) |
| Data | GitHub REST API v3 (public, no auth required) |

No frameworks. No build step. No dependencies.

---

## Getting Started

### 1. Clone or download

```bash
git clone https://github.com/your-username/gitstat.git
cd gitstat
```

### 2. Open in browser

```bash
open index.html
```

Or serve it locally:

```bash
npx serve .
# or
python3 -m http.server 8080
```

### 3. Search a profile

Enter any public GitHub username and click **Analyze →**

---

## API Usage

This app uses the **unauthenticated GitHub REST API**, which allows:

- **60 requests/hour** per IP address

Each profile search makes **2 API calls**:
1. `GET /users/{username}` — profile data
2. `GET /users/{username}/repos?per_page=100&sort=stars` — repository data

Compare mode makes an additional 2 calls for the second user.

### Rate Limit Note

If you hit the rate limit, the app will show a "User not found" error. Wait a few minutes and try again, or authenticate requests by hosting with a backend proxy.

---

## File Structure

```
gitstat/
└── index.html      # Everything — HTML, CSS, JS in one file
```

---

## Screenshots

| Light Mode | Dark Mode |
|------------|-----------|
| Search a user, see full stats | Toggle 🌙 in the top-right |

---

## Known Limitations

| Feature | Status |
|---------|--------|
| Total commits | Not available via public REST API |
| Private repos | Not accessible without OAuth |
| Contribution streak | Estimated (GitHub GraphQL API required for exact data) |
| Rate limit | 60 req/hr unauthenticated |

---

## Roadmap

- [ ] GitHub OAuth login for authenticated requests (6000 req/hr)
- [ ] Real contribution data via GitHub GraphQL API
- [ ] Export as image (html2canvas)
- [ ] Shareable URL with pre-filled username (`?user=torvalds`)
- [ ] Organization profile support

---

## License

MIT — free to use, modify, and distribute.

---

*Built with the GitHub REST API · No tracking · No ads · No backend*
