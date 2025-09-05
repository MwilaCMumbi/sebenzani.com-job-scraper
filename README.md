# Sebenzani.com - Zambian Job Aggregator

A fully automated web application that scrapes and displays recent Zambian job listings from LinkedIn. This project was built to solve the challenge of centralizing job market information for Zambia, providing a clean, simple, and up-to-date interface for job seekers.

**Live Application:** Hosted on Google Sites at [Your Google Sites URL Here]

---

## 🚀 Core Features

- **Automated Data Scraping:** A daily-triggered Google Apps Script automatically scrapes LinkedIn for jobs posted in Zambia within the last week.
- **Dynamic Frontend:** A clean, mobile-friendly user interface built with HTML, CSS, and vanilla JavaScript, served directly by Google Apps Script.
- **Centralized Database:** Google Sheets acts as a simple, effective, and free database to store and serve the scraped job data.
- **No-Code Content Management:** The "About Us" and "Contact Us" pages are powered by a dedicated Google Sheet, allowing for content updates without touching the code.
- **Embeddable Architecture:** The app is designed with `XFrameOptionsMode.ALLOWALL` to be seamlessly embedded into other platforms like Google Sites.

---

## 🛠️ Technology Stack

- **Backend Logic:** Google Apps Script (JavaScript in the Google Cloud environment)
- **Frontend UI:** HTML5, CSS3, Vanilla JavaScript (served via `HtmlService`)
- **Database:** Google Sheets
- **Automation:** Time-driven Triggers in Google Apps Script
- **Hosting/Embedding:** Google Sites

---

## 📂 Project Structure

This repository contains the core source code for the application.

- **`/Code.gs`**: This is the backend server-side script. It contains all the logic for:
  - Scraping the LinkedIn job page (`runJobScraper`).
  - Serving the main web application (`doGet`).
  - Providing the job and content data to the frontend (`getPublicJobData`, `getPageContent`).

- **`/Index.html`**: This is the frontend single-page application. It contains:
  - The HTML structure for all pages (Jobs, About Us, Contact Us).
  - The CSS for professional and responsive styling.
  - The client-side JavaScript for fetching data from the backend and rendering it on the page.

---

## 🔧 How It Works

1.  **Automation:** A daily trigger executes the `runJobScraper()` function in `Code.gs`.
2.  **Scraping:** The script fetches the LinkedIn jobs page for Zambia, parses the HTML to extract job details (Title, Company, Link, Date), and builds a clean data array.
3.  **Data Storage:** The script clears the `Jobs` sheet in the Google Sheet and writes the new data into it.
4.  **User Visit:** When a user visits the Google Sites URL, the embedded Apps Script web app is loaded.
5.  **Serving the App:** The `doGet()` function in `Code.gs` is executed, serving the `Index.html` file.
6.  **Data Fetching:** The JavaScript in `Index.html` runs, calling the `getPublicJobData()` and `getPageContent()` functions on the backend.
7.  **Rendering:** The backend functions read the data from the `Jobs` and `Content` sheets and return it to the frontend, which then dynamically builds the job cards and content pages for the user to see.

This serverless architecture is efficient, scalable, and completely free to operate.
