# Versante AI Products

## Slide 1

VERSANTE

Intelligent. Stigma-Free.

Community-First.

Digital Health Ecosystem

From anonymous AI health navigation to coordinated case management --- Versante powers stigma-free, intelligent public health ecosystems.

OSMe Buddy

AI-powered health companion for anonymous screening, education, and navigation

VersanteConnect

Case management and population health intelligence platform for providers and public health teams.

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image1.png "Image 0")

## Slide 2

PRODUCT 01

OSMe Buddy

LIVE / PILOT DEPLOYMENTS

What It Is

AI-powered digital health companion enabling individuals to access anonymous, stigma-free screening, health education, and support through conversational AI. Designed to improve early detection, outreach, and linkage to care across public health ecosystems.

5 SCREENING DOMAINS

Oral

Health

Sexual

Health

Mental

Health

Behavioral

Risk

Preventive

Care

Wellness

& Prevention

Key Capabilities

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image2.png "Image 0")

Conversational Health Screening

Chat-based assessments guide users through risk evaluation across all screening domains

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image3.png "Image 1")

Anonymous & Private Access

Users engage without sharing personal identity --- no login, no stigma

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image4.png "Image 2")

Chance Score Risk Assessment

Dynamic risk scoring engine that identifies potential health concerns and flags priority follow-up

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image5.png "Image 3")

Resource & Testing Navigation

Links users to testing services, care providers, and community health programs

Output: Personalized health insights, risk indicators, and recommended next actions --- while organizations gain aggregate risk intelligence for outreach and intervention planning.

## Slide 3

PRODUCT 02

VersanteConnect

IN DEVELOPMENT

What It Is

A public health intelligence and case management platform enabling organizations to monitor risk signals, coordinate care, and manage outreach efforts --- powered by insights from OSMe Buddy interactions.

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image6.png "Image 0")

Role-Based Access

Case manager, clinician, administrator, and analyst roles with distinct permissions and workflows

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image7.png "Image 1")

Population Health Dashboard

Aggregated insights from community interactions and screening activity across OSMe Buddy

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image8.png "Image 2")

Risk Monitoring

Identify trends and potential intervention points across populations in real time

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image9.png "Image 3")

Care Coordination

Manage outreach, referrals, and follow-ups across community health programs

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image10.png "Image 4")

Integrated Data Intelligence

Combines AI screening insights from OSMe Buddy with organizational workflows and data

![preencoded.png](C:\Users\VISHAL~1\AppData\Local\Temp\conv_pm06kr9n\media/ppt/media/image11.png "Image 5")

Outcome Reporting

Track engagement, screening patterns, and intervention effectiveness across programs

## Slide 4

ROADMAP

Ecosystem Launch --- Month 7

MONTH 7

Month 1

Month 3

Month 6

Month 7

PHASE 1  ·  Months 1 -- 3

OSMe Buddy Customization

Configure screening domains and CBO-specific branding

Integrate Chance Score engine and

anonymous access flow

Deploy AI companion guidance and

resource navigation

Multilingual support and

accessibility compliance

Pilot testing with CBO outreach

workers and supervisors

Aggregate risk data pipeline to VersanteConnect

Mobile-responsive screens and QA

PHASE 2  ·  Months 4 -- 6

VersanteConnect Build-Out

Case management dashboards and role-based access

Population health dashboard and

risk intelligence engine

Care coordination: referrals,

outreach, and follow-ups

Provider workflow integration and

public health reporting

Outcome reporting and

intervention effectiveness tracking

UAT

+ DEMO

Month 7

Monitor & Iterate

Full ecosystem demo

Partner feedback

cycles

Scale outreach

programs

Ongoing monitoring

& iteration

🎯 Month 7

Launch

## Slide 5

TECHNOLOGY

Stack & Services

⚙  AWS CodeCommit  ·  versante-ecosystem

⬡  FRONTEND

React 18

UI Framework

TypeScript

Type Safety

Tailwind CSS

Styling + Responsive

⬡  BACKEND

Python 3.11

Programming Language

FastAPI

REST API Framework

⬡  DATABASE & STORAGE

RDS PostgreSQL

Users · Screenings · Risk Scores · Referrals · Outreach

S3 File Storage

Health Content · Media · Exports · Org Reports

☁  AWS BEDROCK

Claude 3 Sonnet

AI model powering all conversational health screening

→ Anonymous health screening chat

→ Chance Score risk calculation

→ Resource & navigation guidance

Bedrock Knowledge Base

Stores health content + screening logic

→ Document chunking

→ Embedding generation

→ Vector storage & similarity search

Bedrock Guardrails

Keeps AI medically aligned & responsible

→ Block out-of-scope health claims

→ Allow only vetted health content

Bedrock Agents

Context-aware AI --- knows:

→ Current screening domain & risk level

→ User journey & next best action

OpenSearch Serverless  ·  Vector store for Bedrock KB  ·  AWS-managed, no setup required

EMAIL

AWS SES

Sends insights

as PDF to

care team

email on

completion
