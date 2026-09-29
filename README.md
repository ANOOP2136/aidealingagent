# 🤖 AI Deal Intelligence Agent

A multi-agent AI system for **deal intelligence, company research, market analysis, financial modeling, risk assessment, and investment reporting**, built with **Google ADK**, Gemini models, web search, and custom analytical tools.

The AI Deal Intelligence Agent transforms scattered company, market, financial, competitive, and risk information into a structured intelligence report that can be used to evaluate potential deals and investment opportunities.

**Works with any company** — from early-stage startups to well-funded companies. Provide a company name, website URL, or both.

---

## 🚀 Features

- 🔍 **Live Deal Research** — Real-time web research for companies, markets, competitors, funding, and traction
- 🌐 **URL Support** — Analyze companies directly from their website URLs
- 🏢 **Company Intelligence** — Research founders, products, funding, customers, partnerships, and recent developments
- 📊 **Market Intelligence** — Analyze TAM/SAM, competitors, positioning, trends, and market drivers
- 💰 **Financial Intelligence** — Build Bear/Base/Bull revenue scenarios and financial projections
- ⚠️ **Risk Intelligence** — Analyze market, execution, financial, regulatory, and exit risks
- 📝 **Deal Intelligence Memo** — Synthesize findings into a structured decision-support report
- 📄 **Professional Reports** — Generate polished HTML intelligence reports
- 🎨 **Visual Intelligence** — Generate an AI-powered infographic for rapid deal review

---

## 🧠 What It Does

Given a company name or URL, the AI Deal Intelligence Agent automatically:

1. **Researches the company** — Founders, funding, products, traction, technology, and recent developments
2. **Analyzes the market** — Market size, competitors, positioning, growth drivers, and trends
3. **Builds financial scenarios** — Revenue projections and Bear/Base/Bull growth cases
4. **Assesses deal risks** — Market, execution, financial, regulatory, and exit risks
5. **Generates deal intelligence** — Combines all research into a structured intelligence memo
6. **Creates an intelligence report** — Produces a professional HTML report
7. **Generates a visual summary** — Creates an infographic containing key deal intelligence

The system is designed to turn raw research into a **structured view of a potential deal** rather than requiring users to manually collect information from multiple sources.

---

# ⚡ Quick Start

## 1. Clone & Navigate

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
```

## 2. Set Environment

```bash
export GOOGLE_API_KEY=your_api_key
```

Or create a `.env` file:

```bash
echo "GOOGLE_API_KEY=your_api_key" > .env
```

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

## 4. Start the Agent

```bash
adk web
```

## 5. Open the Interface

Open:

```text
http://localhost:8000
```

Example queries:

```text
Analyze https://agno.com as a potential Series A deal.
```

```text
Build deal intelligence for Genspark AI and its next funding round.
```

```text
Analyze Lovable's market position, competitors, financial trajectory, and key deal risks.
```

```text
Research emergent.sh and generate a complete deal intelligence report.
```

---

# 🏗️ Pipeline Architecture

```text
                         USER QUERY
                             │
                             ▼
              ┌──────────────────────────────┐
              │     DealIntelligencePipeline │
              │       SequentialAgent        │
              └──────────────┬───────────────┘
                             │
                             ▼
              ┌──────────────────────────────┐
              │        Stage 1               │
              │    Company Intelligence      │
              │          Research            │
              └──────────────┬───────────────┘
                             │
                             ▼
              ┌──────────────────────────────┐
              │        Stage 2               │
              │     Market Intelligence      │
              │        & Analysis            │
              └──────────────┬───────────────┘
                             │
                             ▼
              ┌──────────────────────────────┐
              │        Stage 3               │
              │    Financial Intelligence    │
              │         & Modeling           │
              └──────────────┬───────────────┘
                             │
                             ▼
              ┌──────────────────────────────┐
              │        Stage 4               │
              │      Deal Risk Analysis      │
              └──────────────┬───────────────┘
                             │
                             ▼
              ┌──────────────────────────────┐
              │        Stage 5               │
              │    Deal Intelligence Memo    │
              └──────────────┬───────────────┘
                             │
                             ▼
              ┌──────────────────────────────┐
              │        Stage 6               │
              │   Intelligence Report        │
              │        Generator             │
              └──────────────┬───────────────┘
                             │
                             ▼
              ┌──────────────────────────────┐
              │        Stage 7               │
              │   Visual Intelligence        │
              │       Generator              │
              └──────────────────────────────┘
                             │
                             ▼
                       FINAL OUTPUTS

              revenue_chart.png
              deal_intelligence_report.html
              infographic.png
```

---

# 🤖 Agent Architecture

## Stage 1 — Company Intelligence Agent

**Purpose:** Build a comprehensive intelligence profile of the target company using web research.

| Property | Value |
|---|---|
| Model | `gemini-3-flash-preview` |
| Tools | `google_search` |
| Output Key | `company_info` |

### Intelligence Collected

- **Company Profile**
  - What the company does
  - Founding date
  - Headquarters
  - Team size

- **Founders & Leadership**
  - Key people
  - Backgrounds
  - Professional profiles

- **Product & Technology**
  - Core products
  - Product architecture
  - Target customers
  - Technology positioning

- **Funding**
  - Funding rounds
  - Investors
  - Reported funding amounts

- **Traction**
  - Customers
  - Partnerships
  - Growth signals

- **Recent Developments**
  - News
  - Product launches
  - Announcements

For early-stage companies, the agent checks available public sources and identifies areas where information is limited.

---

# 📈 Stage 2 — Market Intelligence Agent

**Purpose:** Understand the market environment surrounding the target company.

| Property | Value |
|---|---|
| Model | `gemini-3-flash-preview` |
| Tools | `google_search` |
| Input | `{company_info}` |
| Output Key | `market_analysis` |

### Intelligence Collected

#### Market Size

- TAM
- SAM
- Market growth
- Industry expansion

#### Competitive Landscape

- Direct competitors
- Indirect competitors
- Competitor funding
- Competitor traction

#### Company Positioning

- Differentiation
- Competitive advantages
- Market positioning

#### Market Trends

- Market drivers
- Emerging technologies
- Regulatory changes
- Industry shifts

The agent uses the company intelligence from Stage 1 as context for the market analysis.

---

# 💰 Stage 3 — Financial Intelligence Agent

**Purpose:** Build financial scenarios and visualize potential revenue trajectories.

| Property | Value |
|---|---|
| Model | `gemini-3-pro-preview` |
| Tools | `generate_financial_chart` |
| Inputs | `{company_info}`, `{market_analysis}` |
| Output Key | `financial_model` |

### Financial Analysis

#### Current Metrics

- Estimated ARR
- Growth stage
- Available financial indicators

#### Growth Scenarios

The agent creates three potential scenarios:

**Bear Case**

Conservative growth assumptions.

**Base Case**

Expected growth trajectory based on available information.

**Bull Case**

Optimistic growth scenario.

#### Return Analysis

Where sufficient information exists, the model can analyze:

- Exit valuation scenarios
- MOIC estimates
- IRR estimates

### Output

```text
revenue_chart_TIMESTAMP.png
```

---

# ⚠️ Stage 4 — Deal Risk Intelligence Agent

**Purpose:** Identify and analyze the major risks surrounding a potential deal.

| Property | Value |
|---|---|
| Model | `gemini-3-pro-preview` |
| Tools | None |
| Inputs | Company + Market + Financial intelligence |
| Output Key | `risk_assessment` |

### Risk Framework

#### 1. Market Risk

- Competitive pressure
- Market timing
- Customer adoption barriers

#### 2. Execution Risk

- Team gaps
- Technology challenges
- Scaling challenges

#### 3. Financial Risk

- Burn rate
- Fundraising requirements
- Unit economics

#### 4. Regulatory Risk

- Compliance
- Legal considerations
- Geopolitical factors

#### 5. Exit Risk

- Acquirer landscape
- Potential exit paths
- IPO considerations

### Risk Output

For each identified risk:

- Severity
- Evidence
- Description
- Potential mitigation

---

# 🧠 Stage 5 — Deal Intelligence Memo Agent

**Purpose:** Synthesize all available intelligence into a structured deal intelligence memo.

| Property | Value |
|---|---|
| Model | `gemini-3-pro-preview` |
| Tools | None |
| Input | All previous stages |
| Output Key | `investor_memo` |

### Intelligence Memo Structure

1. **Executive Summary**
2. **Company Intelligence**
3. **Funding & Valuation**
4. **Market Opportunity**
5. **Competitive Landscape**
6. **Financial Intelligence**
7. **Risk Intelligence**
8. **Deal Thesis**
9. **Key Questions & Next Steps**

---

# 📄 Stage 6 — Intelligence Report Generator

**Purpose:** Convert the deal intelligence memo into a professional HTML report.

| Property | Value |
|---|---|
| Model | `gemini-3-flash-preview` |
| Tools | `generate_html_report` |
| Input | `{investor_memo}` |
| Output Key | `html_report_result` |

### Report Features

- Professional financial-research style
- Executive summary
- Structured intelligence sections
- Data tables
- Financial metrics
- Market analysis
- Risk analysis
- Print-friendly layout

### Output

```text
deal_intelligence_report_TIMESTAMP.html
```

---

# 🎨 Stage 7 — Visual Intelligence Generator

**Purpose:** Create a visual one-page summary of the deal intelligence.

| Property | Value |
|---|---|
| Model | `gemini-3-flash-preview` |
| Tool | `generate_infographic` |
| Image Model | `gemini-3-pro-image-preview` |
| Input | `{investor_memo}` |
| Output Key | `infographic_result` |

### Infographic Includes

- Company name
- Key metrics
- Market opportunity
- Financial indicators
- Risk indicators
- Key deal intelligence
- Visual summary

### Output

```text
infographic_TIMESTAMP.png
```

---

# 📁 Project Structure

```text
ai_deal_intelligence_agent/
│
├── __init__.py
│   └── Exports root_agent
│
├── agent.py
│   └── Seven-agent intelligence pipeline
│
├── tools.py
│   └── Custom analytical and generation tools
│
├── outputs/
│   └── Generated intelligence artifacts
│
├── requirements.txt
│   └── Python dependencies
│
└── README.md
    └── Project documentation
```

---

# 📦 Generated Artifacts

Generated artifacts are saved through the ADK Artifacts system and in the project's `outputs/` directory.

```text
outputs/
│
├── revenue_chart_20260104_143030.png
│   └── Financial scenario visualization
│
├── deal_intelligence_report_20260104_143052.html
│   └── Full deal intelligence report
│
└── infographic_20260104_143105.png
    └── Visual deal intelligence summary
```

### Artifact Types

| Artifact | Format | Purpose |
|---|---|---|
| Revenue Chart | PNG | Bear/Base/Bull financial scenarios |
| Deal Intelligence Report | HTML | Detailed company, market, financial, and risk analysis |
| Intelligence Infographic | PNG/JPG | Visual one-page summary |

---

# 🔧 Google ADK Features Demonstrated

| Feature | Usage |
|---|---|
| **SequentialAgent** | Orchestrates the seven-stage pipeline |
| **LlmAgent** | Powers specialized intelligence agents |
| **google_search** | Real-time company and market research |
| **Custom Tools** | Financial charts, HTML reports, infographics |
| **Artifacts** | Stores generated outputs |
| **State Management** | Passes intelligence between stages using `output_key` |
| **Multi-modal Output** | Combines text analysis, charts, and image generation |

---

# 🧩 Models Used

| Agent | Model | Primary Purpose |
|---|---|---|
| Company Intelligence | `gemini-3-flash-preview` | Fast web research |
| Market Intelligence | `gemini-3-flash-preview` | Market and competitor research |
| Financial Intelligence | `gemini-3-pro-preview` | Financial reasoning |
| Deal Risk Intelligence | `gemini-3-pro-preview` | Deep risk analysis |
| Deal Intelligence Memo | `gemini-3-pro-preview` | Multi-stage synthesis |
| Report Generator | `gemini-3-flash-preview` | HTML generation |
| Visual Intelligence | `gemini-3-flash-preview` | Infographic orchestration |
| Infographic Tool | `gemini-3-pro-image-preview` | Image generation |

---

# 🔄 End-to-End Workflow

```text
Company Name / URL
        │
        ▼
┌──────────────────────┐
│ Company Intelligence │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ Market Intelligence  │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ Financial Intelligence│
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│   Deal Risk Analysis │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ Deal Intelligence    │
│ Memo                 │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ Intelligence Report  │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ Visual Intelligence  │
└──────────┬───────────┘
           ▼
       Final Outputs

   📊 Financial Chart
   📄 HTML Report
   🎨 Infographic
```

---

# 🎯 Why AI Deal Intelligence?

Modern deals require information from multiple sources:

- Company websites
- Market research
- Funding databases
- Competitor information
- Financial indicators
- News and announcements
- Technology developments
- Regulatory information

Manually collecting and connecting this information is time-consuming.

The **AI Deal Intelligence Agent** brings these research tasks together into a single multi-agent workflow.

Instead of producing only a single answer, the system creates a structured intelligence pipeline where each specialized agent contributes a different layer of analysis.

---

# ⚠️ Important Note

Financial figures, projections, valuations, market estimates, and other derived metrics may depend on publicly available information and model assumptions. They should be treated as **analysis and decision-support outputs**, not as verified financial statements or guaranteed forecasts.

---

# 📚 Learn More

- [Google ADK Documentation](https://google.github.io/adk-docs/)
- [Multi-Agent Patterns in ADK](https://developers.googleblog.com/developers-guide-to-multi-agent-patterns-in-adk/)
- [Gemini API Documentation](https://ai.google.dev/gemini-api/docs)
- [Gemini Image Generation](https://ai.google.dev/gemini-api/docs/image-generation)
