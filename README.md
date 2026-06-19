# 📄 AI Resume Analyzer & Career Assistant

> **Analyze your resume, improve your ATS score, identify missing skills, and get personalized career recommendations — in seconds.**

![Project Banner](https://img.shields.io/badge/AI-Powered-6366F1?style=for-the-badge)
[![License](https://img.shields.io/badge/License-MIT-10B981?style=for-the-badge)](https://github.com/Manognapothu/AI_Resume_Analyzer_And_Career_Assistant/blob/main/LICENSE)
[![Deployment](https://img.shields.io/badge/Deploy-Vercel-black?style=for-the-badge&logo=vercel)](https://ai-resume-analyzer-mu-henna.vercel.app/)
[![Built For](https://img.shields.io/badge/Built%20for-Digital%20Heroes-F59E0B?style=for-the-badge)](https://digitalheroesco.com)

---

## 📌 Project Description

**AI Resume Analyzer & Career Assistant** is a free, AI-powered web application that helps students and job seekers understand their resume quality, improve ATS (Applicant Tracking System) compatibility, discover missing skills, and get a personalized career roadmap — all in one place.

Users upload their PDF resume, and the app instantly returns:
- An **ATS compatibility score** out of 100
- **Detected technical and soft skills**
- **Missing skills** tailored to their target role
- **Actionable improvement suggestions**
- **Recommended job roles** based on their skill set
- A **career roadmap** for any target job they enter
- A **downloadable report** of the full analysis

---

## ✨ Features

| Feature | Description |
|---|---|
| 📤 PDF Upload | Drag-and-drop or click-to-upload resume in PDF format |
| 🎯 ATS Score | Visual score ring with sub-category breakdowns |
| 👤 Candidate Profile | Extracts name and infers target role from resume |
| 📝 Resume Summary | AI-generated professional summary of the resume |
| 🔍 Skills Detection | Identifies technical and soft skills from resume text |
| ❌ Missing Skills | Suggests high-demand skills absent from the resume |
| 💡 Improvement Tips | 5 actionable suggestions to improve the resume |
| 💼 Role Recommendations | Top matching job titles with percentage fit |
| 🗺️ Career Assistant | Enter any target role → get required skills, roadmap, interview tips |
| 📥 Download Report | Export full analysis as a text report |
| 📱 Responsive Design | Works on desktop, tablet, and mobile |

---

## 🛠️ Technologies Used

### Frontend
- **HTML5** — Semantic structure
- **CSS3** — Custom properties, grid, flexbox, animations
- **Vanilla JavaScript (ES6+)** — All interactivity and logic

### AI & Processing
- **Anthropic Claude API** (`claude-sonnet-4-6`) — Resume analysis and career roadmap generation
- **PDF.js** (`v3.11.174`) — Client-side PDF text extraction (no server needed)
- **Fallback Analysis Engine** — Keyword-based scoring when API is unavailable

### Fonts & Icons
- **Sora** (Google Fonts) — Display headings
- **Inter** (Google Fonts) — Body text

### Deployment
- **Vercel** — Zero-config static deployment (free tier)

---

## 📁 Project Structure

```
ai-resume-analyzer/
│
├── index.html          # Main application (single-file SPA)
├── README.md           # Project documentation
│
└── (optional for expansion)
    ├── assets/
    │   ├── favicon.ico
    │   └── og-image.png
    └── api/
        └── analyze.js  # Optional: server-side proxy for API key security
```

> **Note:** The current build is a single `index.html` file — all CSS and JavaScript are inline for simplicity and Vercel compatibility.

---

## 🚀 Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Safari, Edge)
- An **Anthropic API key** — get one free at [console.anthropic.com](https://console.anthropic.com)
- [Node.js](https://nodejs.org/) (optional, only if running a local dev server)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/ai-resume-analyzer.git
   cd ai-resume-analyzer
   ```

2. **Add your API key**

   Open `index.html` and find the `fetch` call to the Anthropic API (search for `api.anthropic.com`). The app calls the API directly from the browser — no backend needed for development.

   > ⚠️ **Security note:** For production, proxy the API call through a serverless function (e.g., Vercel API route) so your key is never exposed in the browser.

3. **Run locally**

   Simply open `index.html` in your browser — no build step required.

   Or use a simple local server:
   ```bash
   # Using Python
   python -m http.server 3000

   # Using Node.js (npx)
   npx serve .
   ```

   Then visit `http://localhost:3000`

---

## ☁️ Deployment on Vercel

### Option 1 — Deploy from GitHub (Recommended)

1. Push the project to a **public GitHub repository**
2. Go to [vercel.com](https://vercel.com) and sign in with GitHub
3. Click **"Add New Project"** → select your repository
4. Leave all settings as default (no build command needed)
5. Click **"Deploy"**

Your app will be live at `https://your-project-name.vercel.app` in under 60 seconds.

### Option 2 — Deploy via Vercel CLI

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy from project root
vercel

# Follow the prompts — select defaults for all options
```

### Option 3 — Drag & Drop

1. Go to [vercel.com/new](https://vercel.com/new)
2. Drag and drop your project folder directly into the browser

---

## 🔑 API Configuration

The app uses the **Anthropic Claude API** for intelligent resume analysis. Usage notes:

| Setting | Value |
|---|---|
| Model | `claude-sonnet-4-6` |
| Max tokens | `1000` per request |
| Requests per analysis | 1 (resume analysis) + 1 (career assistant, on demand) |
| Fallback | Keyword-based analysis if API is unavailable |

### Securing Your API Key (Production)

Create a Vercel serverless function to proxy requests:

```js
// api/analyze.js
export default async function handler(req, res) {
  const response = await fetch('https://api.anthropic.com/v1/messages', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'x-api-key': process.env.ANTHROPIC_API_KEY,
      'anthropic-version': '2023-06-01'
    },
    body: JSON.stringify(req.body)
  });
  const data = await response.json();
  res.json(data);
}
```

Set your key in Vercel:
```
Dashboard → Project Settings → Environment Variables → ANTHROPIC_API_KEY
```

---

## 📸 Screenshots

> deploy link: [your-project-name.vercel.app](https://ai-resume-analyzer-mu-henna.vercel.app/)

---


## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the project
2. Create your feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👩‍💻 Developer

**Created by Manogna Pothu**

📧 Email: manognapothu24@gmail.com

🦸 [Built for Digital Heroes](https://digitalheroesco.com)

---

## 🙏 Acknowledgements

- [Anthropic Claude](https://anthropic.com) — AI analysis engine
- [PDF.js](https://mozilla.github.io/pdf.js/) — Client-side PDF parsing by Mozilla
- [Google Fonts](https://fonts.google.com) — Sora & Inter typefaces
- [Digital Heroes Co.](https://digitalheroesco.com) — Project inspiration

---

*Free to use · No data stored · Privacy-first*
