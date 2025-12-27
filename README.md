# N8N AI Automation Workflows

This repository contains exported workflows for **n8n**, focusing on AI-powered automation using Google Gemini. These workflows demonstrate how to integrate LLMs with external services like Discord, Gmail, and Google Search to automate intelligence gathering and analysis tasks.

## Workflows

### 1. Chrome Extension Backend with AI (Trading Assistant)
**File:** `chrome extension backend with AI.json`

This workflow acts as a backend service for a Chrome extension (or any webhook client) to analyze financial charts using computer vision and advanced prompt engineering.

#### Workflow Diagram
```mermaid
graph LR
    A["Webhook<br/>(Receive Image)"] -->|POST| B["Google Gemini<br/>(Vision Analysis)"]
    B -->|"Trading Plan"| C["Discord<br/>(Notify Channel)"]
    C --> D["Respond to Webhook<br/>(Return Analysis)"]
    
    style A fill:#ff6d5a,stroke:#333,stroke-width:2px,color:white
    style B fill:#88aaff,stroke:#333,stroke-width:2px,color:white
    style C fill:#5865F2,stroke:#333,stroke-width:2px,color:white
    style D fill:#22bb33,stroke:#333,stroke-width:2px,color:white
```

#### Details
*   **Trigger:** Webhook (`POST`) receiving an image/screenshot.
*   **AI Logic:** Uses **Google Gemini** (Vision capabilities) with a "Hedge Fund CIO" persona. It performs a "Quantamental" analysis combining technical analysis (market structure, order flow) with a "Red Team" stress test to provide a balanced trading plan.
*   **Output:**
    *   Sends a structured analysis (Direction, Entry, Stop Loss, Take Profit, Reasoning) to a **Discord** channel.
    *   Returns the analysis text to the webhook caller.

---

### 2. SI-OS Intel Daily Collection (Daily News Summarizer)
**File:** `SI-OS Intel Daily Collection DATA Summarizer and sent to my Gamil (Gemini Edition).json`

A daily scheduled automation that acts as a personal "Chief Intelligence Officer," scraping financial news and generating a high-quality HTML summary email.

#### Workflow Diagram
```mermaid
graph LR
    A["Schedule Trigger<br/>(Daily 21:00)"] --> B["SerpApi<br/>(Google News Search)"]
    B -->|"News JSON"| C["Google Gemini<br/>(Filter & Summarize)"]
    C -->|"HTML Report"| D["Gmail<br/>(Send Email)"]

    style A fill:#22bb33,stroke:#333,stroke-width:2px,color:white
    style B fill:#ffbd2e,stroke:#333,stroke-width:2px,color:black
    style C fill:#88aaff,stroke:#333,stroke-width:2px,color:white
    style D fill:#ea4335,stroke:#333,stroke-width:2px,color:white
```

#### Details
*   **Trigger:** Scheduled Timer (Daily at 21:00).
*   **Process:**
    1.  **Search:** Uses **SerpApi** to fetch the latest Google News results for "financial" topics.
    2.  **Filter & Summarize:** Uses **Google Gemini** to process the raw search results. It filters specifically for **Macro Economics**, **Crypto**, and **AI Tech**, ensuring news is within the last 24 hours.
    3.  **Format:** Generates a clean, styled HTML report with an executive summary and categorized links.
*   **Output:** Sends the HTML report via **Gmail**.

---

### 3. Project Crypto ChainLink News Broadcast
**File:** `Project_Crypto_ChainLinkNews_boardcast.json`

A sophisticated dual-track intelligence workflow that monitors the Chainlink ecosystem, combining news aggregation with deep technical video analysis.

#### Workflow Diagram
```mermaid
graph TD
    A["Schedule Trigger"] --> B1["SerpApi<br/>(Google News)"]
    A --> B2["SerpApi<br/>(YouTube Search)"]
    
    B1 --> C1["Google Gemini<br/>(Institutional Filter)"]
    C1 --> D1["Gmail<br/>(Weekly Dashboard)"]
    
    B2 --> C2["Google Gemini<br/>(Video Analysis)"]
    C2 --> C3["Google Gemini<br/>(HTML Architect)"]
    C3 --> D2["Gmail<br/>(Technical Intel)"]

    style A fill:#22bb33,stroke:#333,stroke-width:2px,color:white
    style B1 fill:#ffbd2e,stroke:#333,stroke-width:2px,color:black
    style B2 fill:#ff0000,stroke:#333,stroke-width:2px,color:white
    style C1 fill:#88aaff,stroke:#333,stroke-width:2px,color:white
    style C2 fill:#88aaff,stroke:#333,stroke-width:2px,color:white
    style C3 fill:#88aaff,stroke:#333,stroke-width:2px,color:white
    style D1 fill:#ea4335,stroke:#333,stroke-width:2px,color:white
    style D2 fill:#ea4335,stroke:#333,stroke-width:2px,color:white
```

#### Details
*   **Trigger:** Scheduled periodic execution.
*   **Dual-Track Intelligence:**
    1.  **News Track:** Filters Google News for high-signal institutional developments (CCIP, RWA, ETF, Swift integrations) using **Google Gemini**.
    2.  **Video Track:** Analyzes official **Chainlink YouTube** videos to extract technical deltas, performance metrics, and strategic positioning.
*   **AI Logic:** Employs specialized personas (Lead Institutional Strategist and System Architect) to ensure professional, objective, and high-signal reporting.
*   **Output:** Sends two types of reports via **Gmail**:
    *   **Weekly Strategic Dashboard:** A curated list of the top 10 institutional-grade news items.
    *   **Technical Intelligence:** In-depth deconstruction of the latest technical updates.

---

## Setup & Usage

1.  **Install n8n:** Ensure you have an n8n instance running (Cloud or Self-hosted).
2.  **Import Workflows:**
    *   Open your n8n dashboard.
    *   Click **"Add Workflow"** -> **"Import from..."** -> **"Local File"**.
    *   Select the `.json` files from this directory.
3.  **Configure Credentials:**
    You will need to set up the following credentials in n8n for these workflows to function:
    *   **Google Gemini (PaLM) API:** For the AI analysis and summarization.
    *   **Discord Webhook URL:** For the trading bot notifications.
    *   **SerpApi Key:** For the Google News search functionality.
    *   **Gmail OAuth2:** For sending the daily email reports.

## Disclaimer
The "Chrome Extension Backend with AI" workflow generates financial analysis based on AI interpretation of charts. This is for educational and informational purposes only. **Do not use this as financial advice.** Always do your own research (DYOR).
