## N8NJobSearcher696
This project is an automated job discovery and evaluation workflow built with n8n, designed to intelligently scrape job postings, analyze job descriptions using Google Gemini, and rank opportunities based on how well they match a candidate’s resume.

The workflow continuously searches multiple job platforms (such as Indeed and LinkedIn), validates job seniority using AI, compares job requirements against a provided resume, assigns a match score, and sends only high-quality matches to Discord. A PostgreSQL database is used to prevent duplicates and maintain a history of analyzed postings.

Unlike traditional job alerts, this system uses AI to reason about job descriptions rather than relying solely on keyword filters, dramatically improving signal-to-noise ratio and reducing manual review time.

### Key Features

- Multi-site job scraping via Python (JobSpy)
- AI-based seniority validation (Gemini)
- Resume-to-job semantic matching
- Intelligent scoring & filtering
- Discord notifications for strong matches
- PostgreSQL deduplication & storage
- Config-driven customization
- Designed for low API usage efficiency

### Customizable Configuration

Users can easily adapt the workflow by modifying the Config node:

- ExperienceLevel – Accepted seniority levels
- JobsToScrape – Number of jobs per search
- HomeLocation – Target job location
- MaxCommuteMinutes – Commute tolerance
- JobKeywords – Job search terms
- TargetLanguage – Language preference
- SitesToFindJobs – Job platforms to scan

### Installation

#### Install Docker
Ensure Docker is installed on your system.

Download from:

https://www.docker.com/products/docker-desktop

After installation, verify:
```
docker --version
docker compose version
```

#### Prepare Docker Environment
Copy the Docker configuration files from the repository into your working directory.

#### Build & Start Containers
Run:
```
docker compose up --build -d
```
### First-Run Warning
The first launch may take **several minutes** depending on:
- Your network speed
- Docker image download size
- System performance

Docker must download base images and dependencies, which is normal.

Subsequent runs will be significantly faster.

#### Access the n8n Web Interface
By default, n8n runs on:  http://localhost:5678

#### Open the Import Menu
Inside n8n:

1. Click Workflows

2. Click Import from File

#### Select the Workflow JSON
Choose the exported workflow file from this repository: ``` n8n_workflow.json```

### Important Steps
Importing a workflow does NOT import credentials.

You must manually configure:

- Google Gemini credentials
- PostgreSQL connection
- Discord webhook

Open each node showing a warning icon and select/create credentials.

### Config

#### JobKeywords
Defines what jobs are searched.
Example:
```
["software engineer", "cyber security"]
```

#### ExperienceLevel
Controls what seniority levels are accepted after AI validation.
Example: 
```["internship", "entry"]```

Other valid values: 
```["internship", "entry", "associate", "mid_senior", "director", "executive"]```

#### SitesToFindJobs
Controls which scraping branches are active.
Example:
```
["indeed", "linkedin"]
```
Possible values:
```
"indeed", "linkedin", "zip_recruiter", "google", "glassdoor", "bayt", "naukri", "bdjobs"
```

#### JobsToScrape
How many jobs do you want from each scraping node.
Example: 40

#### HomeLocation
Used for job scraping & commute logic.
Example:
```
Seattle, WA
New York, NY
Austin, TX
```


