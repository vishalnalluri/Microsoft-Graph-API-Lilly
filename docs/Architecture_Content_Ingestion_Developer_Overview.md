# Architecture Content Ingestion Developer Overview

Developer Overview & Introduction

# 🎯 What You're Building

You're building an automated pipeline that syncs enterprise architecture documentation from SharePoint and Microsoft Teams into a GitHub repository as Markdown files. Think of it as a "content bridge" that keeps GitHub in sync with the source systems.

**The Flow:**

SharePoint/Teams → Your Pipeline → GitHub → Downstream Systems\
(Monitor, Convert, Publish)

# 📋 The Problem We're Solving

**Current State:**

- Architecture docs live in SharePoint sites and Teams channels

- Downstream systems (Architecture Portal, AI chatbot, Cortex search) need this content

- Manual copy/paste is slow, error-prone, and doesn't scale

**Your Solution:**

- Automatically monitor SharePoint/Teams for changes

- Convert documents to Markdown format

- Publish to GitHub repository

- Downstream systems pick up changes automatically

# 🏗️ High-Level Architecture

**SOURCE SYSTEMS (Read-only - Don't modify these)**

- SharePoint Sites: IT Architecture, Enterprise Docs, Q4 Planning

- Microsoft Teams: Engineering Team, Design Channel, Architecture Channel

**YOUR PIPELINE COMPONENTS (This is what you're building)**

**1️⃣ FILE MONITOR**

- Poll SharePoint/Teams APIs

- Discover new/modified files

- Microsoft Graph API integration

**2️⃣ CHANGE DETECTOR**

- Calculate MD5 checksums

- Compare with previous state

- Skip unchanged files (efficiency)

**3️⃣ JOB CONVERTER**

- Extract content from source files

- Convert DOCX/PDF/PPTX → Markdown

- Preserve metadata (source, date, etc.)

**4️⃣ GITHUB PUBLISHER**

- Create/update files in GitHub repo

- Organize in clean folder structure

- Commit with traceable history

**5️⃣ STATE TRACKER**

- SQLite database of processed files

- Stores checksums, timestamps

- Prevents duplicate processing

**6️⃣ LOGGER**

- Track all operations

- Error handling and reporting

- Performance metrics

**GITHUB REPOSITORY**

architecture-docs/\
├── sharepoint/\
│ ├── it-architecture/\
│ │ ├── design-patterns.md\
│ │ └── api-guidelines.md\
│ └── enterprise-docs/\
│ └── security-standards.md\
└── teams/\
└── engineering/\
└── architecture/\
└── meeting-notes-2026-02-13.md

**DOWNSTREAM SYSTEMS (Already exist - You just validate they still work)**

- Architecture Portal

- AI Chatbot

- Cortex Search

# 🎬 How It Works (Simple Example)

*Scenario: Someone updates a Word document in SharePoint*

**Monitor (every 15 minutes)**

- Your pipeline polls SharePoint API

- Finds: "design-patterns.docx" was modified

**Detect Change**

- Calculate MD5: abc123...

- Compare with database: old hash: xyz789...

- Result: File changed! ✅

**Convert**

- Download: design-patterns.docx

- Extract content using mammoth.js

- Output: design-patterns.md (Markdown)

**Publish**

- GitHub path: sharepoint/it-architecture/design-patterns.md

- Commit message: \[Ingestion\] Update: design-patterns.md

- Push to GitHub

**Update State**

- Save new MD5: abc123...

- Timestamp: 2026-02-13T10:30:00Z

**Trigger Downstream**

- GitHub Actions runs automatically

- Portal rebuilds with new content

- AI chatbot reindexes

- Done! 🎉

# 🛠️ Tech Stack (What You'll Use)

**Core Technologies**

- Node.js 18+ - Main runtime environment

- JavaScript/TypeScript - Programming language

- SQLite - State tracking database

**Key Libraries**

\# Microsoft integrations\
npm install @microsoft/microsoft-graph-client \# SharePoint/Teams API\
\
\# GitHub integration\
npm install @octokit/rest \# GitHub API client\
\
\# Document conversion\
npm install mammoth \# DOCX → Markdown\
npm install pdf-to-markdown \# PDF → Markdown\
\
\# Database\
npm install better-sqlite3 \# Lightweight SQL database\
\
\# Utilities\
npm install dotenv \# Environment variables\
npm install winston \# Logging

**System Tools**

- pandoc - Universal document converter

- LibreOffice - Fallback for complex conversions

- Git - Version control

# 📂 Project Structure (What You'll Build)

architecture-ingestion/\
├── src/\
│ ├── main.js \# ← Start here (orchestrator)\
│ ├── sources/\
│ │ ├── SharePointMonitor.js \# Poll SharePoint for files\
│ │ └── TeamsMonitor.js \# Poll Teams for files\
│ ├── detection/\
│ │ ├── ChangeDetector.js \# MD5 checksum logic\
│ │ └── StateManager.js \# SQLite database operations\
│ ├── conversion/\
│ │ ├── JobConverter.js \# Route to right converter\
│ │ ├── DocxConverter.js \# DOCX → Markdown\
│ │ ├── PdfConverter.js \# PDF → Markdown\
│ │ └── PptxConverter.js \# PPTX → Markdown\
│ ├── publishing/\
│ │ ├── GitHubPublisher.js \# Push to GitHub\
│ │ └── PathMapper.js \# Generate GitHub paths\
│ └── utils/\
│ ├── logger.js \# Winston logger setup\
│ └── retry.js \# Retry failed operations\
├── tests/\
│ ├── unit/ \# Test individual components\
│ └── integration/ \# Test full pipeline\
├── data/\
│ ├── state.db \# SQLite database\
│ └── logs/ \# Log files\
├── .env \# Secrets (don't commit!)\
├── config.json \# Configuration\
├── package.json\
└── README.md

# 🔑 Key Concepts You Need to Know

**1. Microsoft Graph API**

- Single API to access SharePoint, Teams, OneDrive, etc.

- Uses OAuth 2.0 for authentication

- You'll need: Tenant ID, Client ID, Client Secret

**2. MD5 Checksums (Change Detection)**

- Hash of file content

- Same content = same hash

- Different content = different hash

- Prevents reprocessing unchanged files

**3. Markdown Conversion**

- Goal: Convert Word/PDF/PowerPoint to plain text with formatting

- Preserves: Headers, lists, links, basic formatting

- Loses: Complex layouts, proprietary features

**4. GitHub API (Octokit)**

- Create/update files in repositories

- Files are base64 encoded

- Each operation creates a commit

**5. Idempotency (Run it multiple times safely)**

- Same input = same output

- No duplicates or corruption

- Critical for reliability

# 📅 Timeline (7 Weeks)

| **Week** | **What You're Building** | **Key Deliverable** |
|----|----|----|
| 1 | Setup & Planning | Access to systems, dev environment ready |
| 2 | File Monitor + Basic Converter | Can list files from SharePoint/Teams |
| 3 | Change Detection + State Tracking | Only processes changed files |
| 4 | GitHub Publisher | Files appear in GitHub automatically |
| 5 | End-to-End Pipeline | Full workflow works start to finish |
| 6 | Integration + Validation | Downstream systems working |
| 7 | Documentation + Handoff | Production-ready, documented |

# ⚡ Quick Start (Your First Task)

**Week 1 - Get Up and Running**

**1. Clone the starter repo (or create new):**

mkdir architecture-ingestion\
cd architecture-ingestion\
npm init -y

**2. Install dependencies:**

npm install @microsoft/microsoft-graph-client @octokit/rest\
npm install mammoth better-sqlite3 dotenv winston

**3. Create .env file (get these from Lilly team):**

\# Microsoft Graph API\
MICROSOFT_TENANT_ID=xxx\
MICROSOFT_CLIENT_ID=xxx\
MICROSOFT_CLIENT_SECRET=xxx\
\
\# GitHub\
GITHUB_TOKEN=ghp_xxx\
GITHUB_OWNER=eli-lilly\
GITHUB_REPO=architecture-docs\
\
\# SharePoint Sites (comma-separated)\
SHAREPOINT_SITES=site-id-1,site-id-2

**4. Test Microsoft Graph connection:**

// test-graph.js\
const client = require('@microsoft/microsoft-graph-client');\
require('isomorphic-fetch');\
\
// Get token using client credentials flow\
const getAccessToken = async () =\> {\
// You'll implement this with MSAL library\
};\
\
const graphClient = Client.init({\
authProvider: async (done) =\> {\
const token = await getAccessToken();\
done(null, token);\
}\
});\
\
// List SharePoint sites\
const sites = await graphClient.api('/sites').get();\
console.log('Sites:', sites.value);

# 🎯 Success Criteria (How You Know It Works)

**Week 2 Check:**

- Can connect to SharePoint API

- Can list files from configured sites

- Can download a test file

- Can convert DOCX to Markdown

**Week 4 Check:**

- Can detect when a file changes

- Only processes changed files (skips unchanged)

- Can publish Markdown to GitHub

- GitHub folder structure is clean

**Week 7 (Final):**

- End-to-End Test: Update a Word doc in SharePoint → See it in GitHub within 15 minutes

- No Manual Steps: Fully automated, no human intervention

- Reliable: Handles errors gracefully, logs everything

- Downstream Works: Architecture Portal updates automatically

# 🚨 Things to Watch Out For

**Common Pitfalls:**

**API Rate Limits**

- Microsoft Graph: ~2,000 requests/hour

- GitHub: ~5,000 requests/hour

- Solution: Batch operations, cache responses

**Large Files**

- Some PDFs/DOCX are 50+ MB

- Solution: Stream processing, timeout handling

**Authentication Expiry**

- Tokens expire (typically 1 hour)

- Solution: Refresh tokens automatically

**Conversion Failures**

- Corrupted files, unsupported formats

- Solution: Try-catch, log and skip, don't crash

**Duplicate Processing**

- Running pipeline twice shouldn't duplicate content

- Solution: Check state database before processing

# 🤔 Key Questions to Ask Lilly Team (Week 1)

**Access:**

- What are the SharePoint site IDs we should monitor?

- Can you create a service account with read-only access?

**Scope:**

- How many files are we talking about? (100s, 1000s, 10,000s?)

- What file types are most common? (DOCX, PDF, both?)

- Are there folders we should exclude?

**GitHub:**

- What's the exact repository name?

- Any branch protection rules?

- Who should be the commit author?

**CATS:**

- Do you have CATS API documentation?

- Who's our technical contact for CATS?

**Performance:**

- How often should this run? (every 15 min, hourly, daily?)

- What's the expected change rate? (10 files/day, 100 files/day?)

# 📚 Learning Resources

**Microsoft Graph API:**

- Docs: https://learn.microsoft.com/en-us/graph/

- SharePoint: https://learn.microsoft.com/en-us/graph/api/resources/sharepoint

- Authentication: https://learn.microsoft.com/en-us/graph/auth-v2-service

**GitHub API:**

- Octokit Docs: https://octokit.github.io/rest.js/

- Creating/Updating Files: https://docs.github.com/en/rest/repos/contents

**Document Conversion:**

- Mammoth.js: https://github.com/mwilliamson/mammoth.js

- Pandoc: https://pandoc.org/MANUAL.html


---

## Additional Content

Architecture Content Ingestion Automation

Developer Overview & Introduction

🎯 What You're Building

You're building an automated pipeline that syncs enterprise architecture documentation from SharePoint and Microsoft Teams into a GitHub repository as Markdown files. Think of it as a "content bridge" that keeps GitHub in sync with the source systems.

The Flow:

SharePoint/Teams → Your Pipeline → GitHub → Downstream Systems

(Monitor, Convert, Publish)

📋 The Problem We're Solving

Current State:

Architecture docs live in SharePoint sites and Teams channels

Downstream systems (Architecture Portal, AI chatbot, Cortex search) need this content

Manual copy/paste is slow, error-prone, and doesn't scale

Your Solution:

Automatically monitor SharePoint/Teams for changes

Convert documents to Markdown format

Publish to GitHub repository

Downstream systems pick up changes automatically

🏗️ High-Level Architecture

SOURCE SYSTEMS (Read-only - Don't modify these)

SharePoint Sites: IT Architecture, Enterprise Docs, Q4 Planning

Microsoft Teams: Engineering Team, Design Channel, Architecture Channel

YOUR PIPELINE COMPONENTS (This is what you're building)

1️⃣ FILE MONITOR

Poll SharePoint/Teams APIs

Discover new/modified files

Microsoft Graph API integration

2️⃣ CHANGE DETECTOR

Calculate MD5 checksums

Compare with previous state

Skip unchanged files (efficiency)

3️⃣ JOB CONVERTER

Extract content from source files

Convert DOCX/PDF/PPTX → Markdown

Preserve metadata (source, date, etc.)

4️⃣ GITHUB PUBLISHER

Create/update files in GitHub repo

Organize in clean folder structure

Commit with traceable history

5️⃣ STATE TRACKER

SQLite database of processed files

Stores checksums, timestamps

Prevents duplicate processing

6️⃣ LOGGER

Track all operations

Error handling and reporting

Performance metrics

GITHUB REPOSITORY

architecture-docs/

├── sharepoint/

│   ├── it-architecture/

│   │   ├── design-patterns.md

│   │   └── api-guidelines.md

│   └── enterprise-docs/

│       └── security-standards.md

└── teams/

└── engineering/

└── architecture/

└── meeting-notes-2026-02-13.md

DOWNSTREAM SYSTEMS (Already exist - You just validate they still work)

Architecture Portal

AI Chatbot

Cortex Search

🎬 How It Works (Simple Example)

Scenario: Someone updates a Word document in SharePoint

Monitor (every 15 minutes)

Your pipeline polls SharePoint API

Finds: "design-patterns.docx" was modified

Detect Change

Calculate MD5: abc123...

Compare with database: old hash: xyz789...

Result: File changed! ✅

Convert

Download: design-patterns.docx

Extract content using mammoth.js

Output: design-patterns.md (Markdown)

Publish

GitHub path: sharepoint/it-architecture/design-patterns.md

Commit message: [Ingestion] Update: design-patterns.md

Push to GitHub

Update State

Save new MD5: abc123...

Timestamp: 2026-02-13T10:30:00Z

Trigger Downstream

GitHub Actions runs automatically

Portal rebuilds with new content

AI chatbot reindexes

Done! 🎉

🛠️ Tech Stack (What You'll Use)

Core Technologies

Node.js 18+ - Main runtime environment

JavaScript/TypeScript - Programming language

SQLite - State tracking database

Key Libraries

# Microsoft integrations

npm install @microsoft/microsoft-graph-client  # SharePoint/Teams API

# GitHub integration

npm install @octokit/rest  # GitHub API client

# Document conversion

npm install mammoth         # DOCX → Markdown

npm install pdf-to-markdown # PDF → Markdown

# Database

npm install better-sqlite3  # Lightweight SQL database

# Utilities

npm install dotenv          # Environment variables

npm install winston         # Logging

System Tools

pandoc - Universal document converter

LibreOffice - Fallback for complex conversions

Git - Version control

📂 Project Structure (What You'll Build)

architecture-ingestion/

├── src/

│   ├── main.js                      # ← Start here (orchestrator)

│   ├── sources/

│   │   ├── SharePointMonitor.js     # Poll SharePoint for files

│   │   └── TeamsMonitor.js          # Poll Teams for files

│   ├── detection/

│   │   ├── ChangeDetector.js        # MD5 checksum logic

│   │   └── StateManager.js          # SQLite database operations

│   ├── conversion/

│   │   ├── JobConverter.js          # Route to right converter

│   │   ├── DocxConverter.js         # DOCX → Markdown

│   │   ├── PdfConverter.js          # PDF → Markdown

│   │   └── PptxConverter.js         # PPTX → Markdown

│   ├── publishing/

│   │   ├── GitHubPublisher.js       # Push to GitHub

│   │   └── PathMapper.js            # Generate GitHub paths

│   └── utils/

│       ├── logger.js                # Winston logger setup

│       └── retry.js                 # Retry failed operations

├── tests/

│   ├── unit/                        # Test individual components

│   └── integration/                 # Test full pipeline

├── data/

│   ├── state.db                     # SQLite database

│   └── logs/                        # Log files

├── .env                             # Secrets (don't commit!)

├── config.json                      # Configuration

├── package.json

└── README.md

🔑 Key Concepts You Need to Know

1. Microsoft Graph API

Single API to access SharePoint, Teams, OneDrive, etc.

Uses OAuth 2.0 for authentication

You'll need: Tenant ID, Client ID, Client Secret

2. MD5 Checksums (Change Detection)

Hash of file content

Same content = same hash

Different content = different hash

Prevents reprocessing unchanged files

3. Markdown Conversion

Goal: Convert Word/PDF/PowerPoint to plain text with formatting

Preserves: Headers, lists, links, basic formatting

Loses: Complex layouts, proprietary features

4. GitHub API (Octokit)

Create/update files in repositories

Files are base64 encoded

Each operation creates a commit

5. Idempotency (Run it multiple times safely)

Same input = same output

No duplicates or corruption

Critical for reliability

📅 Timeline (7 Weeks)

Week

What You're Building

Key Deliverable

1

Setup & Planning

Access to systems, dev environment ready

2

File Monitor + Basic Converter

Can list files from SharePoint/Teams

3

Change Detection + State Tracking

Only processes changed files

4

GitHub Publisher

Files appear in GitHub automatically

5

End-to-End Pipeline

Full workflow works start to finish

6

Integration + Validation

Downstream systems working

7

Documentation + Handoff

Production-ready, documented

⚡ Quick Start (Your First Task)

Week 1 - Get Up and Running

1. Clone the starter repo (or create new):

mkdir architecture-ingestion

cd architecture-ingestion

npm init -y

2. Install dependencies:

npm install @microsoft/microsoft-graph-client @octokit/rest

npm install mammoth better-sqlite3 dotenv winston

3. Create .env file (get these from Lilly team):

# Microsoft Graph API

MICROSOFT_TENANT_ID=xxx

MICROSOFT_CLIENT_ID=xxx

MICROSOFT_CLIENT_SECRET=xxx

# GitHub

GITHUB_TOKEN=ghp_xxx

GITHUB_OWNER=eli-lilly

GITHUB_REPO=architecture-docs

# SharePoint Sites (comma-separated)

SHAREPOINT_SITES=site-id-1,site-id-2

4. Test Microsoft Graph connection:

// test-graph.js

const client = require('@microsoft/microsoft-graph-client');

require('isomorphic-fetch');

// Get token using client credentials flow

const getAccessToken = async () => {

// You'll implement this with MSAL library

};

const graphClient = Client.init({

authProvider: async (done) => {

const token = await getAccessToken();

done(null, token);

}

});

// List SharePoint sites

const sites = await graphClient.api('/sites').get();

console.log('Sites:', sites.value);

🎯 Success Criteria (How You Know It Works)

Week 2 Check:

Can connect to SharePoint API

Can list files from configured sites

Can download a test file

Can convert DOCX to Markdown

Week 4 Check:

Can detect when a file changes

Only processes changed files (skips unchanged)

Can publish Markdown to GitHub

GitHub folder structure is clean

Week 7 (Final):

End-to-End Test: Update a Word doc in SharePoint → See it in GitHub within 15 minutes

No Manual Steps: Fully automated, no human intervention

Reliable: Handles errors gracefully, logs everything

Downstream Works: Architecture Portal updates automatically

🚨 Things to Watch Out For

Common Pitfalls:

API Rate Limits

Microsoft Graph: ~2,000 requests/hour

GitHub: ~5,000 requests/hour

Solution: Batch operations, cache responses

Large Files

Some PDFs/DOCX are 50+ MB

Solution: Stream processing, timeout handling

Authentication Expiry

Tokens expire (typically 1 hour)

Solution: Refresh tokens automatically

Conversion Failures

Corrupted files, unsupported formats

Solution: Try-catch, log and skip, don't crash

Duplicate Processing

Running pipeline twice shouldn't duplicate content

Solution: Check state database before processing

🤔 Key Questions to Ask Lilly Team (Week 1)

Access:

What are the SharePoint site IDs we should monitor?

Can you create a service account with read-only access?

Scope:

How many files are we talking about? (100s, 1000s, 10,000s?)

What file types are most common? (DOCX, PDF, both?)

Are there folders we should exclude?

GitHub:

What's the exact repository name?

Any branch protection rules?

Who should be the commit author?

CATS:

Do you have CATS API documentation?

Who's our technical contact for CATS?

Performance:

How often should this run? (every 15 min, hourly, daily?)

What's the expected change rate? (10 files/day, 100 files/day?)

📚 Learning Resources

Microsoft Graph API:

Docs: https://learn.microsoft.com/en-us/graph/

SharePoint: https://learn.microsoft.com/en-us/graph/api/resources/sharepoint

Authentication: https://learn.microsoft.com/en-us/graph/auth-v2-service

GitHub API:

Octokit Docs: https://octokit.github.io/rest.js/

Creating/Updating Files: https://docs.github.com/en/rest/repos/contents

Document Conversion:

Mammoth.js: https://github.com/mwilliamson/mammoth.js

Pandoc: https://pandoc.org/MANUAL.html

| Week | What You're Building | Key Deliverable |

| --- | --- | --- |

| 1 | Setup & Planning | Access to systems, dev environment ready |

| 2 | File Monitor + Basic Converter | Can list files from SharePoint/Teams |

| 3 | Change Detection + State Tracking | Only processes changed files |

| 4 | GitHub Publisher | Files appear in GitHub automatically |

| 5 | End-to-End Pipeline | Full workflow works start to finish |

| 6 | Integration + Validation | Downstream systems working |

| 7 | Documentation + Handoff | Production-ready, documented |