# Job Alert Automation (Playwright + AI Scoring + Google Sheets + Email)

This project is an end-to-end **job scraping automation pipeline** built using **Python + Playwright**.  
It scrapes job postings from job portals, validates relevance using **AI/LLM scoring**, stores high-quality job matches into **Google Sheets**, prevents duplicates, and sends **email notifications** automatically.

This automation helps job seekers save time by filtering only the most relevant jobs based on their background and target role.

---

## 🚀 Key Features
- Automated job portal scraping using **Playwright**
- Extract job posting details:
- Timestamp
- Job Title
- Company
- Description (truncated)
- Apply Before
- Posted On
- Official Website
- Hiring Timezone
- Location Requirements
- Match Score (1–9)
- AI Analysis
- Job Link
- AI/LLM job relevance validation
  - Scores each job from **1–9**
  - Saves only jobs with score **>= 7**
- Deduplication system (prevents saving the same job twice)
- Stores results in **Google Sheets**
- Sends automatic email notifications for high-score jobs
- Scheduler-ready pipeline (can be run daily/hourly)

---

## 🛠 Tech Stack
- Python
- Playwright
- Google Sheets API (`gspread`)
- LLM / AI scoring (OpenAI / Gemini)
- Pandas
- SMTP Email automation
- dotenv (`.env`)

---



## ⚙️ Installation & Setup

### 1) Clone Repository
```bash
git clone https://github.com/AqilaFadia/job-alert-automation-playwright.git
cd job-alert-automation-playwright
```

### 2) Install Dependencies
```bash
pip install -r requirements.txt
```
### 3) Install Playwright Browsers
```bash
playwright install
```


## AI / LLM API KEY
```bash
OPENAI_API_KEY=your_api_key_here
```

## Job Scoring Settings
```bash
MIN_SCORE=7
```

📌 Google Sheets Setup
#### Step 1: Create Service Account Credentials
- Go to Google Cloud Console
```bash
https://console.cloud.google.com/
```
- Create a project
- Enable:
```bash
Google Sheets API
Google Drive API
```
- Create a Service Account
- Generate JSON key file

Save it as:

credentials.json

### AI Scoring Logic (Job Validation)

The system uses AI to evaluate job relevance based on the candidate profile.

Example scoring logic:
```bash
Score 9 = Perfect match (high relevance)
Score 7–8 = Good match (recommended)
Score 1–6 = Low relevance (ignored)
```

Only jobs with score >= MIN_SCORE will be saved.

### How to Run
Run Once
```bash
python main.py
```
Run Automatically (Scheduler)

If you want to run the pipeline periodically:
```bash
python scheduler.py
```
Example scheduler interval:


⚠️ Notes
Some job portals may block scraping due to anti-bot protection.
Scraping logic may require adjustments if the website layout changes.
AI scoring depends on API availability and rate limits.
