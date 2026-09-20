# Reputation Radar

AI-assisted reputation monitoring and weekly briefing workflow built for the Growpido AI & Automation Engineer task.

## Track

**Track A: Reputation Radar**

The system monitors public web and news search results for mentions of Nidhi Hooda and Growpido, verifies entity identity, classifies sentiment and reputational risk, and produces a weekly exception-based brief.

## Workflow

1. **Search and dedupe**
   - Google web search and Google News via SerpAPI
   - Previously seen URLs are filtered out
2. **Identity verification**
   - Gemini scores whether a result is actually about Nidhi Hooda or Growpido
   - High-confidence matches continue directly
   - Uncertain matches are fetched with Firecrawl and checked again
3. **Failure and ambiguity handling**
   - Search failures are logged
   - Unreadable AI output defaults to a manual-check state rather than silently dropping the item
   - Unverified results containing crisis-related keywords are routed for review
4. **Sentiment and risk**
   - Sentiment: positive, negative, neutral
   - Risk: ignore, watch, respond_now
5. **Human approval**
   - A response draft can be generated for urgent verified mentions
   - Drafts are stored in a Pending Approval sheet
   - Nothing is posted automatically
6. **Weekly brief**
   - Builds a short exception-based email brief from the Mentions Log and Pending Approval sheet

## Files

- `workflow/Reputation Radar — Scan & Classify.json`
- `workflow/Reputation Radar — Weekly Brief.json`

The workflow exports in this public repository have credential objects and private connection identifiers removed. Configure your own credentials and Google Sheet when importing them into n8n.

## Live n8n workflow

https://rohitr07.app.n8n.cloud/workflow/Ro3JolZOLcOZdTKA

The live workflow is included for walkthrough/reference. The exported JSON is provided so the workflow can also be inspected or imported into another n8n instance.

## Required services

- n8n
- SerpAPI
- Google Gemini
- Firecrawl
- Google Sheets
- SMTP/email provider

## Important safety behavior

The system is designed as a monitoring and drafting workflow, not an autonomous posting system. Generated responses remain pending human approval.

## Sample run

A sample weekly brief produced during testing is included in the submission materials. The displayed test run reported 6 total mentions, 0 negative mentions, 0 items needing review, and 0 pending approvals.

## Setup

1. Import the two JSON workflows into n8n.
2. Configure credentials for SerpAPI, Gemini, Firecrawl, Google Sheets, and SMTP.
3. Replace the Google Sheet placeholder with your own sheet.
4. Create the required sheets: `Seen URLs`, `Mentions Log`, and `Pending Approval`.
5. Test the scan workflow manually.
6. Test the weekly brief workflow.
7. Activate the schedules after verifying the output.
