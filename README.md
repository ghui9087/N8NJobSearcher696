# N8NJobSearcher696
This project is an automated job discovery and evaluation workflow built with n8n, designed to intelligently scrape job postings, analyze job descriptions using Google Gemini, and rank opportunities based on how well they match a candidate’s resume.

The workflow continuously searches multiple job platforms (such as Indeed and LinkedIn), validates job seniority using AI, compares job requirements against a provided resume, assigns a match score, and sends only high-quality matches to Discord. A PostgreSQL database is used to prevent duplicates and maintain a history of analyzed postings.

Unlike traditional job alerts, this system uses AI to reason about job descriptions rather than relying solely on keyword filters, dramatically improving signal-to-noise ratio and reducing manual review time.

Key Features

• Multi-site job scraping via Python (JobSpy)
• AI-based seniority validation (Gemini)
• Resume-to-job semantic matching
• Intelligent scoring & filtering
• Discord notifications for strong matches
• PostgreSQL deduplication & storage
• Config-driven customization
• Designed for low API usage efficiency

Customizable Configuration

Users can easily adapt the workflow by modifying the Config node:

• ExperienceLevel – Accepted seniority levels
• JobsToScrape – Number of jobs per search
• HomeLocation – Target job location
• MaxCommuteMinutes – Commute tolerance
• JobKeywords – Job search terms
• TargetLanguage – Language preference
• SitesToFindJobs – Job platforms to scan
