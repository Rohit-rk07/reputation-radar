# Credentials needed (no values stored here)

| n8n credential type | Used by | Notes |
|---|---|---|
| SerpAPI | Search Web for Mentions, Search News (recent) | Google web and Google News search |
| Google Gemini (PaLM) API | Primary / Secondary Match, Classify, Draft Response | Model `gemini-3.6-flash` |
| Header Auth | Fetch Full Page (Firecrawl) | Name `Authorization`, Value `Bearer <Firecrawl key>` |
| Google Sheets OAuth2 | All Sheets nodes, both workflows | One spreadsheet, three tabs |
| SMTP | Send Weekly Brief Email | From and to address set in the node |