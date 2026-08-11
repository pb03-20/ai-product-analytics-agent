# 🎵 Spotify Product Analytics Agent

> An automated product analytics system built with **n8n, PostgreSQL, SQL, Gemini, and JavaScript** that transforms a Spotify music dataset into structured analytics, product insights, feature opportunities, and roadmap hypotheses.

---

## 🚀 Project Overview

This project demonstrates how a Product Manager can use **workflow automation + SQL analytics + AI** to move from a large music catalog to actionable product insights.

The pipeline follows:

```text
Spotify Dataset
       ↓
   PostgreSQL
       ↓
  17 SQL Analyses
       ↓
    Aggregate
       ↓
   Gemini / AI
       ↓
JavaScript Processing
       ↓
Structured Reports
       ↓
Product Opportunities
       ↓
Roadmap Hypotheses
```

The purpose of the system is not to allow AI to make unsupported product decisions.

Instead:

> **SQL calculates the analytical metrics → n8n orchestrates the workflow → Gemini interprets the results → JavaScript structures the output → Product thinking turns insights into hypotheses.**

---

# 🏗️ Complete n8n Architecture

The complete workflow is implemented as a single n8n workflow with **17 parallel SQL analysis branches**.

Each branch follows the same general pattern:

```text
Execute SQL Query
        ↓
     Aggregate
        ↓
    Gemini / AI
        ↓
 JavaScript Processing
        ↓
    Final Output
```

## 📸 Full Workflow

![Complete n8n Workflow](docs/n8n-workflow-full.png)

The screenshot above shows the actual workflow architecture used in the project.

The central trigger distributes execution across the analytical branches. Each branch independently performs SQL analysis, aggregates the result, sends the structured result to a Gemini model, and then processes the generated report through JavaScript nodes.

The workflow is intentionally designed as a **fan-out analytical architecture** rather than one large SQL query.

---

# 🔢 Workflow Scale

The successful execution used for this project contained:

| Component | Result |
|---|---:|
| SQL analysis branches | **17** |
| Total workflow nodes executed | **86** |
| Execution status | **Success** |
| Execution mode | Manual |
| Execution ID | `414` |

The execution record shows `status: success` and a total `nodeCount` of 86. :contentReference[oaicite:2]{index=2}

The 17 SQL nodes are explicitly present in the execution data, from `Execute a SQL query` through `Execute a SQL query16`. :contentReference[oaicite:3]{index=3} :contentReference[oaicite:4]{index=4}

---

# 🧩 How the Architecture Works

## 1. Workflow Trigger

The workflow begins with:

```text
When clicking 'Execute workflow'
```

This acts as the manual entry point for the complete analytics pipeline.

The execution record confirms that the trigger completed successfully. :contentReference[oaicite:5]{index=5}

---

## 2. PostgreSQL + SQL Analysis

The core analytical work happens inside PostgreSQL.

The workflow contains **17 independent SQL analysis nodes**.

Rather than asking one query to answer every product question, the workflow separates the analytical problems into independent branches.

This makes the workflow:

- Easier to understand
- Easier to debug
- Easier to modify
- Easier to extend
- Easier to connect to different AI prompts

---

# 🔬 The 17 SQL Analysis Branches

The workflow contains the following 17 SQL execution stages:

| # | n8n SQL Node | Analytical Area |
|---:|---|---|
| 1 | `Execute a SQL query` | Analytical SQL branch |
| 2 | `Execute a SQL query1` | Analytical SQL branch |
| 3 | `Execute a SQL query2` | Analytical SQL branch |
| 4 | `Execute a SQL query3` | Analytical SQL branch |
| 5 | `Execute a SQL query4` | Analytical SQL branch |
| 6 | `Execute a SQL query5` | Analytical SQL branch |
| 7 | `Execute a SQL query6` | Analytical SQL branch |
| 8 | `Execute a SQL query7` | Analytical SQL branch |
| 9 | `Execute a SQL query8` | Analytical SQL branch |
| 10 | `Execute a SQL query9` | Analytical SQL branch |
| 11 | `Execute a SQL query10` | Analytical SQL branch |
| 12 | `Execute a SQL query11` | Analytical SQL branch |
| 13 | `Execute a SQL query12` | Analytical SQL branch |
| 14 | `Execute a SQL query13` | Analytical SQL branch |
| 15 | `Execute a SQL query14` | Analytical SQL branch |
| 16 | `Execute a SQL query15` | Catalog analysis |
| 17 | `Execute a SQL query16` | Product opportunity / roadmap analysis |

The execution log contains 17 successful SQL-query node executions. :contentReference[oaicite:6]{index=6}

> The node names above are the actual n8n node names. The analytical purpose of each query is determined by the SQL logic and its returned fields.

---

# 📊 What the SQL Analysis Produces

The SQL branches generate several different types of analytical outputs.

These include:

### 🎵 Track-level analysis

The workflow evaluates characteristics such as:

- Popularity
- Danceability
- Energy
- Valence
- Tempo
- Acousticness
- Instrumentalness
- Speechiness
- Track duration

---

### 🎧 Discovery Analysis

The workflow creates analytical pools such as:

- Mood Boosters
- Chill Seekers
- Discovery Enthusiasts
- High Energy Listeners

For example, the generated analysis identifies:

| Segment | Tracks | Avg Popularity | Avg Energy | Avg Tempo |
|---|---:|---:|---:|---:|
| Mood Boosters | 26,224 | 30.80 | 0.721 | 124.6 |
| Chill Seekers | 18,010 | 30.32 | 0.221 | 110.6 |
| Discovery Enthusiasts | 30,540 | 16.83 | 0.774 | 124.8 |
| High Energy Listeners | 33,650 | 32.52 | 0.863 | 145.4 |

These are **SQL-defined track segments**, not verified user personas. :contentReference[oaicite:7]{index=7}

---

# 🎚️ Audio Feature Analysis

Another analytical branch groups tracks around individual audio characteristics.

The workflow produced segments such as:

| Segment | Track Count | Feature Average | Proposed Product Experiment |
|---|---:|---:|---|
| Energy Leaders | 37,880 | 0.902 Energy | High Energy Badge |
| Danceability Leaders | 8,768 | 0.849 Danceability | Made for Dancing Badge |
| Acoustic Champions | 15,792 | 0.912 Acousticness | Unplugged Badge |
| Instrumental Focus | 18,850 | 0.824 Instrumentalness | No Lyrics Filter |

These segments are generated from SQL-defined thresholds and are subsequently interpreted as possible product experiments. :contentReference[oaicite:8]{index=8}

---

# 📈 Catalog Health Analysis

One branch focuses on the overall catalog.

The SQL-generated catalog metrics include:

| Metric | Value |
|---|---:|
| Total Active Library | **114,000** |
| Playlist-Ready Tracks | **52,063** |
| Discovery Pool | **65,413** |
| Average Track Quality Score | **0.561** |
| High Quality Content | **13,570** |

The workflow defines these metrics from SQL logic based on popularity, duration, danceability, energy, and valence. :contentReference[oaicite:9]{index=9}

These metrics can then be used as a starting point for product experiments.

---

# 🎯 Skip-Risk Analysis

The workflow also contains a **synthetic skip-risk analysis**.

The analysis evaluates track characteristics such as:

- Duration
- Tempo
- Speechiness
- Danceability
- Energy
- Valence
- Instrumentalness

The generated output analyzed **306 track records**, with approximately **168 unique tracks**, an average popularity of **66.8**, and an average synthetic skip probability of **0.47**. :contentReference[oaicite:10]{index=10}

Example analytical categories include:

- Too Long
- Too Slow
- Too Much Talking
- Too Instrumental
- Low Danceability
- Very Low Mood

### Important

This is **not actual Spotify skip behavior**.

The `skip_probability` and `skip_risk_category` values are generated by SQL logic. The dataset contains no actual listener skip events or retention logs. :contentReference[oaicite:11]{index=11}

Therefore the output should be treated as a **product hypothesis generator**, not a predictive skip model.

---

# 🔀 Cross-Genre Discovery

The workflow also analyzes relationships between genres.

For example, SQL output can produce recommendations such as:

```text
If you like K-Pop
        ↓
Try House
```

or:

```text
If you like EDM
        ↓
Try Electronic
```

These recommendations are based on calculated similarity between genre characteristics rather than actual user behavior. :contentReference[oaicite:12]{index=12}

This creates a potential foundation for:

- Cross-genre recommendations
- Music discovery
- Genre exploration
- Related-genre playlists

---

# 🤖 Gemini / AI Analysis

After PostgreSQL produces structured results, n8n passes the output to Gemini.

The AI does not directly query the database.

Instead, it receives the analytical result and converts it into a product-readable interpretation.

For example:

```text
SQL Result
    ↓
Structured JSON
    ↓
Aggregate
    ↓
Gemini
    ↓
Product Analysis
```

The Gemini output can contain:

- Summary
- Comparison tables
- Key observations
- Product hypotheses
- Experiment ideas
- Feature opportunities
- Roadmap recommendations
- Limitations

The execution record shows Gemini model nodes successfully processing structured analytical results. One example takes the SQL-defined feature opportunities and turns them into a structured feature comparison and roadmap analysis. :contentReference[oaicite:13]{index=13}

---

# 🧠 Why Use AI After SQL?

The important architecture decision is:

### SQL handles **measurement**

SQL answers:

> "What does the data say?"

### Gemini handles **interpretation**

Gemini answers:

> "What could this mean from a product perspective?"

### The Product Manager handles **decision-making**

The PM asks:

> "Should we actually build or test this?"

So the system becomes:

```text
DATA
 ↓
SQL
 ↓
EVIDENCE
 ↓
AI INTERPRETATION
 ↓
PRODUCT HYPOTHESIS
 ↓
PM DECISION
```

---

# 🧱 JavaScript Processing

After Gemini generates the analysis, JavaScript nodes process the response.

The JavaScript stages are used to transform model output into structured formats such as:

- Reports
- HTML
- JSON
- Documentation-ready content

For example, one JavaScript node receives the Gemini-generated `report` and produces the corresponding HTML output. :contentReference[oaicite:14]{index=14}

This allows the workflow to convert AI output into something that can be stored, displayed, or sent to another system.

---

# 💡 Final Product Opportunities

One of the final analytical branches produces four product opportunities.

| Feature | Addressable Content | Feasibility | Demand Hypothesis | Priority | Roadmap |
|---|---:|---|---|---:|---|
| **Mood-Based Radio** | 114,000 tracks | High | High | 1 | Q1 2025 |
| **Hidden Gems Section** | 26,473 tracks | High | High | 1 | Q1 2025 |
| **Artist Discovery Feed** | 31,437 artists | Medium | High | 2 | Q2 2025 |
| **Time-of-Day Playlists** | 114,000 tracks | High | Medium | 3 | Q3 2025 |

These values are directly present in the workflow execution output. :contentReference[oaicite:15]{index=15}

---

# 🥇 Priority 1 — Mood-Based Radio

### Addressable Content

**114,000 tracks**

The SQL logic identifies tracks with non-null valence and energy data.

### Product Idea

Create a personalized radio experience based on mood-related audio characteristics.

### Why it is interesting

The workflow classifies the opportunity as:

- Technical feasibility: **High**
- User demand hypothesis: **High**
- Priority score: **1**

The workflow places it in:

**Q1 2025 — Immediate**

These classifications are generated by SQL logic and should be treated as hypotheses rather than validated product research. :contentReference[oaicite:16]{index=16}

---

# 💎 Priority 1 — Hidden Gems

### Addressable Content

**26,473 tracks**

The SQL logic identifies tracks with:

```text
Popularity < 35
AND
Average Danceability > 0.60
AND
Average Energy > 0.60
AND
Average Valence > 0.60
```

### Product Idea

Create a **Hidden Gems** discovery experience for lesser-known tracks with selected audio characteristics.

### Classification

- Technical feasibility: **High**
- User demand hypothesis: **High**
- Priority score: **1**
- Roadmap: **Q1 2025**

:contentReference[oaicite:17]{index=17}

---

# 🎤 Priority 2 — Artist Discovery Feed

### Addressable Content

**31,437 distinct artists**

Unlike the track-based opportunities, this metric represents distinct artist entities.

### Product Idea

Create an artist discovery feed that introduces users to artists outside their existing listening patterns.

### Classification

- Technical feasibility: **Medium**
- User demand hypothesis: **High**
- Priority score: **2**
- Roadmap: **Q2 2025**

The workflow explicitly notes that this opportunity requires a recommendation engine. :contentReference[oaicite:18]{index=18}

---

# 🕐 Priority 3 — Time-of-Day Playlists

### Addressable Content

**114,000 tracks**

The opportunity uses track characteristics including:

- Tempo
- Energy

### Product Idea

Create contextual playlists based on listening time or context.

Examples:

```text
Morning
   ↓
High-energy / appropriate tempo

Afternoon
   ↓
Focus / balanced energy

Evening
   ↓
Lower-energy listening
```

### Classification

- Technical feasibility: **High**
- User demand hypothesis: **Medium**
- Priority score: **3**
- Roadmap: **Q3 2025**

:contentReference[oaicite:19]{index=19}

---

# 🗺️ Product Roadmap

The resulting roadmap is:

```text
Q1 2025
│
├── Mood-Based Radio
│
└── Hidden Gems
       ↓
Q2 2025
│
└── Artist Discovery Feed
       ↓
Q3 2025
│
└── Time-of-Day Playlists
```

The ordering is based on the SQL-assigned `priority_score`.

It should **not** be interpreted as a validated company roadmap.

---

# 🧪 From Analytics to Product Experiments

The most important PM takeaway from this project is that the workflow does not end with analytics.

The output can become an experimentation backlog.

For example:

### Hypothesis

> Users may engage with lesser-known tracks when those tracks match desirable audio characteristics.

### Feature

**Hidden Gems**

### Experiment

Compare:

```text
Control
Existing discovery experience

vs.

Treatment
Hidden Gems section
```

### Potential KPIs

- Discovery clicks
- Track starts
- Completion rate
- Saves
- Playlist additions
- Repeat plays
- Session continuation

The current dataset does **not** contain these behavioral metrics, so they would need to be measured in a real experiment.

---

# ⚠️ Important Analytical Limitations

This project deliberately separates **analytical hypotheses** from **validated product conclusions**.

## Synthetic metrics

Several metrics are calculated using SQL logic.

For example:

```text
skip_probability
viral_potential_score
engagement_score
priority_score
```

These should not automatically be interpreted as real-world behavioral measurements.

---

## No user-level behavior

The dataset does not establish:

- Actual skips
- Actual retention
- Actual session behavior
- Actual saves
- Actual playlist additions
- Actual user satisfaction

Therefore:

```text
Correlation / Pattern
        ≠
User Behavior
        ≠
Causal Product Impact
```

The skip-risk analysis explicitly notes that the data contains no observed listener logs, skip events, or retention rates. :contentReference[oaicite:20]{index=20}

---

## Dataset duplication

The analysis also identifies duplication caused by multi-genre tagging.

A track can appear under multiple genre records, which can influence aggregate statistics. :contentReference[oaicite:21]{index=21}

---

## Popularity is a proxy

Popularity is used in several analyses as a catalog-level metric.

It should not be treated as:

> "This is how much a user likes the track."

It is a dataset attribute used to construct analytical segments.

---

# 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| **n8n** | Workflow orchestration |
| **PostgreSQL** | Data storage and SQL analytics |
| **SQL** | Analytical calculations and segmentation |
| **Gemini** | AI-assisted interpretation |
| **JavaScript** | Output transformation and formatting |
| **GitHub** | Version control and project documentation |
| **CSV** | Spotify dataset source |
| **JSON** | Workflow and structured data |

---

# 📁 Repository Structure

```text
ai-product-analytics-agent/
│
├── README.md
│
├── docs/
│   └── n8n-workflow-full.png
│
├── workflows/
│   └── ai-product-analytics-agent.json
│
├── spotify.csv
│
└── spotify-sample-input.json
```

### `README.md`

Project documentation.

### `docs/n8n-workflow-full.png`

Full screenshot of the n8n workflow architecture.

### `workflows/`

Exported n8n workflow.

### `spotify.csv`

Spotify dataset used for the analysis.

### `spotify-sample-input.json`

Sample structured input for the workflow.

---

# ▶️ How to Run

## Step 1 — Prepare PostgreSQL

Load the Spotify dataset into PostgreSQL.

---

## Step 2 — Configure n8n

Configure the PostgreSQL connection inside n8n.

---

## Step 3 — Configure Gemini

Add the required Gemini credentials to the AI nodes.

---

## Step 4 — Import the Workflow

Import the workflow JSON from:

```text
workflows/
```

into n8n.

---

## Step 5 — Execute

Use:

```text
Execute workflow
```

The central trigger fans execution out across the analytical SQL branches.

---

## Step 6 — Review Results

The workflow produces:

```text
SQL Results
     ↓
Aggregated Results
     ↓
Gemini Reports
     ↓
JavaScript Output
```

The final outputs can then be used for product analysis and documentation.

---

# ✅ Successful Execution

A complete execution was successfully recorded for this workflow.

```text
Execution ID: 414
Workflow ID: fylalEIuExLBhipB

Status: SUCCESS

Started:
2026-08-02T09:39:54.027Z

Stopped:
2026-08-02T09:44:24.822Z

Total Nodes:
86
```

:contentReference[oaicite:22]{index=22}

The execution data also shows successful execution of the SQL, aggregation, Gemini, and JavaScript stages. For example, the product-opportunity SQL branch, aggregation stage, Gemini interpretation, and JavaScript processing all report `success`. :contentReference[oaicite:23]{index=23} :contentReference[oaicite:24]{index=24} :contentReference[oaicite:25]{index=25} :contentReference[oaicite:26]{index=26}

---

# 🎯 Product Management Takeaway

This project demonstrates a practical workflow for turning a large dataset into a product-analysis pipeline.

The key idea is:

```text
                 RAW DATA
                    ↓
               PostgreSQL
                    ↓
              17 SQL QUESTIONS
                    ↓
              STRUCTURED DATA
                    ↓
                  n8n
                    ↓
              GEMINI ANALYSIS
                    ↓
            PRODUCT INTERPRETATION
                    ↓
          FEATURE OPPORTUNITIES
                    ↓
              PRIORITIZATION
                    ↓
             EXPERIMENT IDEAS
```

The system helps reduce repetitive analytical work while keeping the underlying calculations in SQL.

---

# 💡 What This Project Demonstrates

### Product Management

- Translating data into product questions
- Identifying feature opportunities
- Prioritizing opportunities
- Creating experimentation hypotheses
- Separating evidence from assumptions

### Data Analytics

- SQL-based segmentation
- Catalog-level analysis
- Audio-feature analysis
- Cross-genre analysis
- Synthetic scoring
- Product-oriented metrics

### AI

- Structured interpretation of SQL results
- Automated report generation
- Product insight generation
- Natural-language summaries

### Automation

- Multi-branch n8n workflow
- PostgreSQL integration
- AI integration
- JavaScript transformation
- Automated end-to-end execution

---

# 🔮 Future Improvements

The next version could extend the system with:

- Real user listening data
- Actual skip events
- Session-level analytics
- A/B testing
- Recommendation evaluation
- User-level personalization
- KPI dashboards
- Automated experiment analysis
- Scheduled analytics runs
- Automated GitHub documentation
- Model evaluation
- Production monitoring

The most important improvement would be connecting the catalog analysis to **actual user behavioral data**.

That would allow the project to move from:

```text
Catalog Analytics
```

toward:

```text
Behavioral Product Analytics
```

and eventually:

```text
Analytics
   ↓
Hypothesis
   ↓
Experiment
   ↓
User Behavior
   ↓
Measurement
   ↓
Product Decision
```

---

# 📌 Final Note

The product opportunities, feasibility labels, demand hypotheses, priority scores, and roadmap placements in this project are **SQL-generated analytical outputs**.

They are not claims about actual Spotify users or Spotify's real product roadmap.

The purpose of this project is to demonstrate how a Product Manager can build an automated system that turns structured data into **evidence-backed product hypotheses that can later be validated through research and experimentation**.

---

## 👤 Project Focus

**Product Analytics × SQL × AI × n8n Automation × Product Management**

Built as a portfolio project demonstrating how automation and AI can support **data-driven product discovery and decision-making**.
