Architecture Content Ingestion Automation

Developer Overview & Introduction

# 🎯 What You're Building

You're building an automated pipeline that syncs enterprise architecture documentation from SharePoint and Microsoft Teams into a GitHub repository as Markdown files\. Think of it as a "content bridge" that keeps GitHub in sync with the source systems\.

__The Flow:__

SharePoint/Teams → Your Pipeline → GitHub → Downstream Systems  
                   \(Monitor, Convert, Publish\)

# 📋 The Problem We're Solving

__Current State:__

- Architecture docs live in SharePoint sites and Teams channels
- Downstream systems \(Architecture Portal, AI chatbot, Cortex search\) need this content
- Manual copy/paste is slow, error\-prone, and doesn't scale

__Your Solution:__

- Automatically monitor SharePoint/Teams for changes
- Convert documents to Markdown format
- Publish to GitHub repository
- Downstream systems pick up changes automatically

# 🏗️ High\-Level Architecture

__SOURCE SYSTEMS \(Read\-only \- Don't modify these\)__

- SharePoint Sites: IT Architecture, Enterprise Docs, Q4 Planning
- Microsoft Teams: Engineering Team, Design Channel, Architecture Channel

__YOUR PIPELINE COMPONENTS \(This is what you're building\)__

__1️⃣ FILE MONITOR__

- Poll SharePoint/Teams APIs
- Discover new/modified files
- Microsoft Graph API integration

__2️⃣ CHANGE DETECTOR__

- Calculate MD5 checksums
- Compare with previous state
- Skip unchanged files \(efficiency\)

__3️⃣ JOB CONVERTER__

- Extract content from source files
- Convert DOCX/PDF/PPTX → Markdown
- Preserve metadata \(source, date, etc\.\)

__4️⃣ GITHUB PUBLISHER__

- Create/update files in GitHub repo
- Organize in clean folder structure
- Commit with traceable history

__5️⃣ STATE TRACKER__

- SQLite database of processed files
- Stores checksums, timestamps
- Prevents duplicate processing

__6️⃣ LOGGER__

- Track all operations
- Error handling and reporting
- Performance metrics

__GITHUB REPOSITORY__

architecture\-docs/  
├── sharepoint/  
│   ├── it\-architecture/  
│   │   ├── design\-patterns\.md  
│   │   └── api\-guidelines\.md  
│   └── enterprise\-docs/  
│       └── security\-standards\.md  
└── teams/  
    └── engineering/  
        └── architecture/  
            └── meeting\-notes\-2026\-02\-13\.md

__DOWNSTREAM SYSTEMS \(Already exist \- You just validate they still work\)__

- Architecture Portal
- AI Chatbot
- Cortex Search

# 🎬 How It Works \(Simple Example\)

*Scenario: Someone updates a Word document in SharePoint*

__Monitor \(every 15 minutes\)__

- Your pipeline polls SharePoint API
- Finds: "design\-patterns\.docx" was modified

__Detect Change__

- Calculate MD5: abc123\.\.\.
- Compare with database: old hash: xyz789\.\.\.
- Result: File changed\! ✅

__Convert__

- Download: design\-patterns\.docx
- Extract content using mammoth\.js
- Output: design\-patterns\.md \(Markdown\)

__Publish__

- GitHub path: sharepoint/it\-architecture/design\-patterns\.md
- Commit message: \[Ingestion\] Update: design\-patterns\.md
- Push to GitHub

__Update State__

- Save new MD5: abc123\.\.\.
- Timestamp: 2026\-02\-13T10:30:00Z

__Trigger Downstream__

- GitHub Actions runs automatically
- Portal rebuilds with new content
- AI chatbot reindexes
- Done\! 🎉

# 🛠️ Tech Stack \(What You'll Use\)

__Core Technologies__

- Node\.js 18\+ \- Main runtime environment
- JavaScript/TypeScript \- Programming language
- SQLite \- State tracking database

__Key Libraries__

\# Microsoft integrations  
npm install @microsoft/microsoft\-graph\-client  \# SharePoint/Teams API  
  
\# GitHub integration  
npm install @octokit/rest  \# GitHub API client  
  
\# Document conversion  
npm install mammoth         \# DOCX → Markdown  
npm install pdf\-to\-markdown \# PDF → Markdown  
  
\# Database  
npm install better\-sqlite3  \# Lightweight SQL database  
  
\# Utilities  
npm install dotenv          \# Environment variables  
npm install winston         \# Logging

__System Tools__

- pandoc \- Universal document converter
- LibreOffice \- Fallback for complex conversions
- Git \- Version control

# 📂 Project Structure \(What You'll Build\)

architecture\-ingestion/  
├── src/  
│   ├── main\.js                      \# ← Start here \(orchestrator\)  
│   ├── sources/  
│   │   ├── SharePointMonitor\.js     \# Poll SharePoint for files  
│   │   └── TeamsMonitor\.js          \# Poll Teams for files  
│   ├── detection/  
│   │   ├── ChangeDetector\.js        \# MD5 checksum logic  
│   │   └── StateManager\.js          \# SQLite database operations  
│   ├── conversion/  
│   │   ├── JobConverter\.js          \# Route to right converter  
│   │   ├── DocxConverter\.js         \# DOCX → Markdown  
│   │   ├── PdfConverter\.js          \# PDF → Markdown  
│   │   └── PptxConverter\.js         \# PPTX → Markdown  
│   ├── publishing/  
│   │   ├── GitHubPublisher\.js       \# Push to GitHub  
│   │   └── PathMapper\.js            \# Generate GitHub paths  
│   └── utils/  
│       ├── logger\.js                \# Winston logger setup  
│       └── retry\.js                 \# Retry failed operations  
├── tests/  
│   ├── unit/                        \# Test individual components  
│   └── integration/                 \# Test full pipeline  
├── data/  
│   ├── state\.db                     \# SQLite database  
│   └── logs/                        \# Log files  
├── \.env                             \# Secrets \(don't commit\!\)  
├── config\.json                      \# Configuration  
├── package\.json  
└── README\.md

# 🔑 Key Concepts You Need to Know

__1\. Microsoft Graph API__

- Single API to access SharePoint, Teams, OneDrive, etc\.
- Uses OAuth 2\.0 for authentication
- You'll need: Tenant ID, Client ID, Client Secret

__2\. MD5 Checksums \(Change Detection\)__

- Hash of file content
- Same content = same hash
- Different content = different hash
- Prevents reprocessing unchanged files

__3\. Markdown Conversion__

- Goal: Convert Word/PDF/PowerPoint to plain text with formatting
- Preserves: Headers, lists, links, basic formatting
- Loses: Complex layouts, proprietary features

__4\. GitHub API \(Octokit\)__

- Create/update files in repositories
- Files are base64 encoded
- Each operation creates a commit

__5\. Idempotency \(Run it multiple times safely\)__

- Same input = same output
- No duplicates or corruption
- Critical for reliability

# 📅 Timeline \(7 Weeks\)

__Week__

__What You're Building__

__Key Deliverable__

1

Setup & Planning

Access to systems, dev environment ready

2

File Monitor \+ Basic Converter

Can list files from SharePoint/Teams

3

Change Detection \+ State Tracking

Only processes changed files

4

GitHub Publisher

Files appear in GitHub automatically

5

End\-to\-End Pipeline

Full workflow works start to finish

6

 Integration \+ Validation

Downstream systems working

7

Documentation \+ Handoff

Production\-ready, documented

# ⚡ Quick Start \(Your First Task\)

__Week 1 \- Get Up and Running__

__1\. Clone the starter repo \(or create new\):__

mkdir architecture\-ingestion  
cd architecture\-ingestion  
npm init \-y

__2\. Install dependencies:__

npm install @microsoft/microsoft\-graph\-client @octokit/rest  
npm install mammoth better\-sqlite3 dotenv winston

__3\. Create \.env file \(get these from Lilly team\):__

\# Microsoft Graph API  
MICROSOFT\_TENANT\_ID=xxx  
MICROSOFT\_CLIENT\_ID=xxx  
MICROSOFT\_CLIENT\_SECRET=xxx  
  
\# GitHub  
GITHUB\_TOKEN=ghp\_xxx  
GITHUB\_OWNER=eli\-lilly  
GITHUB\_REPO=architecture\-docs  
  
\# SharePoint Sites \(comma\-separated\)  
SHAREPOINT\_SITES=site\-id\-1,site\-id\-2

__4\. Test Microsoft Graph connection:__

// test\-graph\.js  
const client = require\('@microsoft/microsoft\-graph\-client'\);  
require\('isomorphic\-fetch'\);  
  
// Get token using client credentials flow  
const getAccessToken = async \(\) => \{  
  // You'll implement this with MSAL library  
\};  
  
const graphClient = Client\.init\(\{  
  authProvider: async \(done\) => \{  
    const token = await getAccessToken\(\);  
    done\(null, token\);  
  \}  
\}\);  
  
// List SharePoint sites  
const sites = await graphClient\.api\('/sites'\)\.get\(\);  
console\.log\('Sites:', sites\.value\);

# 🎯 Success Criteria \(How You Know It Works\)

__Week 2 Check:__

- Can connect to SharePoint API
- Can list files from configured sites
- Can download a test file
- Can convert DOCX to Markdown

__Week 4 Check:__

- Can detect when a file changes
- Only processes changed files \(skips unchanged\)
- Can publish Markdown to GitHub
- GitHub folder structure is clean

__Week 7 \(Final\):__

- End\-to\-End Test: Update a Word doc in SharePoint → See it in GitHub within 15 minutes
- No Manual Steps: Fully automated, no human intervention
- Reliable: Handles errors gracefully, logs everything
- Downstream Works: Architecture Portal updates automatically

# 🚨 Things to Watch Out For

__Common Pitfalls:__

__API Rate Limits__

- Microsoft Graph: ~2,000 requests/hour
- GitHub: ~5,000 requests/hour
- Solution: Batch operations, cache responses

__Large Files__

- Some PDFs/DOCX are 50\+ MB
- Solution: Stream processing, timeout handling

__Authentication Expiry__

- Tokens expire \(typically 1 hour\)
- Solution: Refresh tokens automatically

__Conversion Failures__

- Corrupted files, unsupported formats
- Solution: Try\-catch, log and skip, don't crash

__Duplicate Processing__

- Running pipeline twice shouldn't duplicate content
- Solution: Check state database before processing

# 🤔 Key Questions to Ask Lilly Team \(Week 1\)

__Access:__

- What are the SharePoint site IDs we should monitor?
- Can you create a service account with read\-only access?

__Scope:__

- How many files are we talking about? \(100s, 1000s, 10,000s?\)
- What file types are most common? \(DOCX, PDF, both?\)
- Are there folders we should exclude?

__GitHub:__

- What's the exact repository name?
- Any branch protection rules?
- Who should be the commit author?

__CATS:__

- Do you have CATS API documentation?
- Who's our technical contact for CATS?

__Performance:__

- How often should this run? \(every 15 min, hourly, daily?\)
- What's the expected change rate? \(10 files/day, 100 files/day?\)

# 📚 Learning Resources

__Microsoft Graph API:__

- Docs: https://learn\.microsoft\.com/en\-us/graph/
- SharePoint: https://learn\.microsoft\.com/en\-us/graph/api/resources/sharepoint
- Authentication: https://learn\.microsoft\.com/en\-us/graph/auth\-v2\-service

__GitHub API:__

- Octokit Docs: https://octokit\.github\.io/rest\.js/
- Creating/Updating Files: https://docs\.github\.com/en/rest/repos/contents

__Document Conversion:__

- Mammoth\.js: https://github\.com/mwilliamson/mammoth\.js
- Pandoc: https://pandoc\.org/MANUAL\.html

