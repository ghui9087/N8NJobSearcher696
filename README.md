# N8NJobSearcher696
This project is an automated job discovery and evaluation workflow built with n8n, designed to intelligently scrape job postings, analyze job descriptions using Google Gemini, and rank opportunities based on how well they match a candidate’s resume.

The workflow continuously searches multiple job platforms (such as Indeed and LinkedIn), validates job seniority using AI, compares job requirements against a provided resume, assigns a match score, and sends only high-quality matches to Discord. A PostgreSQL database is used to prevent duplicates and maintain a history of analyzed postings.

Unlike traditional job alerts, this system uses AI to reason about job descriptions rather than relying solely on keyword filters, dramatically improving signal-to-noise ratio and reducing manual review time.
