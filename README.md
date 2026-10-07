# 🔎 FoundIt – Lost & Found Board

A lightweight, single-file web app that helps students on a hostel or campus community post lost and found items, get automatically matched, and return belongings safely, without sharing contact details with strangers.

> **Live demo:** `https://<your-username>.github.io/foundit/` *(replace after enabling GitHub Pages)*
> **Repository:** `https://github.com/<your-username>/foundit`

---

## 📌 Project Details

| | |
|---|---|
| **Project name** | FoundIt – Lost & Found Board |
| **Brief description** | A campus lost and found board where users post lost or found items with photos, category, location, colour and date. The app scores every lost post against every found post and surfaces likely matches. Contact details stay hidden until the finder verifies the real owner through a secret question. |
| **Problem solved** | Lost items in hostels and campuses are usually reported through scattered WhatsApp groups and notice boards, so owners never find them and finders don't know whom to contact. |
| **AI/ML technologies** | Rule-based weighted similarity scoring (smart matching engine), implemented in vanilla JavaScript. No external ML library or API is used yet. See [AI/ML approach](#-aiml-approach) and [Roadmap](#-roadmap-true-aiml-upgrades). |
| **Other tools** | HTML5, CSS3 (custom properties, light/dark theme), vanilla JavaScript, Canvas API (client-side photo compression), `localStorage` |
| **GitHub / Live demo** | `https://github.com/<your-username>/foundit` · `https://<your-username>.github.io/foundit/` |

---

## ✨ Features

- **Two post types:** "I lost something" and "I found something".
- **12 item categories:** Electronics, Stationery, ID & Cards, Wallet, Keys, Bags, Books & Notes, Clothing, Bottles & Lunchbox, Accessories, Sports Gear, Other.
- **Campus locations:** Atrium, Audi, Chamber of Secrets, Academic Block, Admin Block, NCH, Mess, Nescafe, Other.
- **Photo upload:** up to 3 photos per post, compressed in the browser before saving.
- **Automatic match suggestions:** a "Possible match" badge and a match-percentage list appear as soon as you post.
- **Owner verification:** finders add a question only the owner can answer; claims are approved or rejected by the finder.
- **Privacy by design:** contact details unlock only after a claim is approved.
- **Drop-off points:** finders can mark where the item is held (with me, Admin Block office, Security desk).
- **Urgent flag** for important lost items.
- **Lifecycle handling:** mark as returned, delete a post, and auto-archive of open posts after 30 days.
- **Search and filters** by keyword, category and location, plus tabs for All / Lost / Found / Mine / Done.
- **Live stats:** lost and still looking, found and waiting, returned, busiest spot.
- **Responsive, accessible UI** with dark and light mode, keyboard focus states and Esc-to-close dialogs.

---

## 🧠 AI/ML Approach

FoundIt uses a **weighted feature-similarity matcher** to pair lost and found posts. Each pair of opposite-type, open posts gets a score out of 100:

| Signal | Points |
|---|---|
| Same category | +35 |
| Same location | +25 |
| Dates within 2 days (or within 5 days) | +15 (or +8) |
| Same colour (ignored if "Not sure") | +15 |
| Title keyword overlap | +10 |

Pairs scoring **50 or above** are shown as possible matches, ranked by score. This is a transparent, explainable heuristic, which suits a small campus dataset where there is no training data and users should be able to see why two items matched.

> **Note:** this is classical rule-based scoring, not a trained machine learning model. The roadmap below lists the genuine ML upgrades.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, vanilla JavaScript (no frameworks) |
| Matching engine | Custom weighted scoring function |
| Storage | Browser `localStorage` (no backend needed) |
| Image handling | Canvas API for client-side resizing and compression |
| Fonts | Google Fonts: Bricolage Grotesque, Instrument Sans |
| Hosting | GitHub Pages (static) |

---

## 🚀 Getting Started

No build step and no dependencies.

```bash
git clone https://github.com/<your-username>/foundit.git
cd foundit
# open index.html in your browser
```

Or serve it locally:

```bash
python -m http.server 8000
# visit http://localhost:8000
```

### Deploy on GitHub Pages

1. Rename `FoundIt_-_Lost___Found_Board.html` to `index.html`.
2. Push to GitHub.
3. Go to **Settings → Pages**, select the `main` branch and the `/ (root)` folder, then save.
4. Your live demo link appears after a minute.

---

## 📖 How It Works

1. **Post:** choose Lost or Found, fill in item, category, place, colour and date, and add photos. Finders add a verification question.
2. **Get matched:** the app scores the new post against all open posts of the opposite type and shows likely matches.
3. **Verify and return:** the owner answers the finder's question; the finder approves the claim; contact details unlock; the item is marked returned.

---

## ⚠️ Current Limitations

- Data lives in each user's browser (`localStorage`), so posts are not shared between devices. A shared backend is needed for real multi-user use.
- The "finder approves your claim" step is auto-simulated for the built-in demo posts.
- Matching uses exact category, location and colour equality, so it cannot recognise synonyms or similar-looking items.

---

## 🗺️ Roadmap: True AI/ML Upgrades

- [ ] **Image similarity:** compare item photos using pretrained embeddings (e.g. MobileNet / CLIP via TensorFlow.js) for visual matching.
- [ ] **Auto-categorisation:** predict category and colour from an uploaded photo using an image classifier.
- [ ] **Semantic text matching:** replace keyword overlap with sentence embeddings so "black earbuds case" matches "AirPods box".
- [ ] **Fuzzy and TF-IDF title matching** as a lightweight first step.
- [ ] **Duplicate and spam detection** for repeated or fake posts.
- [ ] **Backend:** Firebase or Supabase for shared posts, authentication and notifications.
- [ ] **Email or push alerts** when a new post matches yours.

---

## 📁 Project Structure

```
foundit/
├── index.html      # complete app: markup, styles and logic in one file
└── README.md
```

---

## 🤝 Contributing

Pull requests and ideas are welcome. Open an issue to discuss a change first.

## 📄 License

Released under the [MIT License](LICENSE).

---

Built to make sure lost things find their way back. 💙
