# BranchCare AI

A Flask + SQLite branch and employee issue-management prototype with **real OpenAI API-powered issue categorization**.

## Features
- Employee registration/login and demo administrator login
- Submit branch issues with category and priority
- AI-assisted category, priority, and summary suggestions
- Admin dashboard to view issues and update status
- SQLite persistence; passwords are hashed

## Setup (Windows)
1. Install Python 3.10 or newer.
2. Extract the ZIP and open a terminal in this folder.
3. Create and activate a virtual environment:
   ```powershell
   py -m venv .venv
   .venv\Scripts\Activate.ps1
   ```
4. Install dependencies:
   ```powershell
   pip install -r requirements.txt
   ```
5. Copy `.env.example` to `.env`. Put your OpenAI API key in `OPENAI_API_KEY`. Keep `.env` private; never commit or share it.
6. Start the app:
   ```powershell
   python app.py
   ```
7. Visit http://127.0.0.1:5000

## Demo accounts
- Admin: `admin@branchcare.local` / `Admin@123`
- Employee: `employee@branchcare.local` / `Employee@123`

Change demo passwords and `FLASK_SECRET_KEY` before deployment. The database is created automatically on first run.

## AI behavior
The **Suggest with AI** button sends the issue description to the OpenAI Responses API and uses the returned JSON to suggest a category, priority, and summary. This is a real API integration, not keyword-based pretend AI. The employee reviews the suggestions and submits the issue themselves. If no API key is configured, ordinary issue submission still works, but AI suggestions show a configuration message.

## Production notes
This is an educational prototype, not a hardened production service. Before public deployment add HTTPS, CSRF protection, rate limiting, secure cookie settings, stronger admin provisioning, audit logging, backups, and access controls scoped to branch policy. Do not submit passwords, personal data, or confidential company information to an external AI service without authorization.
