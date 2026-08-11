# 🎵 AI Product Analytics Agent

An AI-powered music product analytics workflow built with **n8n, PostgreSQL, and Gemini**.

The project analyzes a Spotify music dataset using SQL, extracts useful patterns from the catalog, and converts those findings into **product insights and feature opportunities**.

---

## 🚀 Project Overview

The goal of this project is to demonstrate how raw music data can be transformed into actionable product insights using a combination of:

- PostgreSQL for data analysis
- SQL for analytical queries
- n8n for workflow automation
- Gemini for interpreting analytical results
- JavaScript for transforming and organizing outputs

---

## 🔄 Workflow
## 📸 n8n Workflow

![Complete n8n Workflow](docs/n8n-workflow-full.png)
The overall workflow is:

**Spotify Dataset → PostgreSQL → 17 SQL Analyses → Aggregate Results → Gemini → Product Insights**

### What happens in the workflow?

1. The Spotify dataset is stored in PostgreSQL.
2. The workflow executes multiple SQL queries to analyze different aspects of the music catalog.
3. Each SQL query focuses on a specific product or analytics question.
4. The results from the SQL queries are aggregated.
5. Gemini analyzes the structured SQL results.
6. JavaScript processes the final AI output.
7. The workflow produces product opportunities, recommendations, segments, and roadmap insights.

---

# 🧮 17 SQL Analyses

### 1. Track Similarity
Find similar tracks based on audio features.

### 2. Genre Similarity
Identify relationships between different music genres.

### 3. Hidden Gems Discovery
Find low-popularity tracks with strong audio characteristics.

### 4. Mood-Based Playlists
Identify tracks suitable for different moods and listening experiences.

### 5. Time-of-Day Playlists
Identify tracks suitable for different times of the day.

### 6. Viral Potential Analysis
Identify tracks with characteristics associated with higher viral potential.

### 7. Engagement Analysis
Analyze audio characteristics associated with potential listener engagement.

### 8. Skip-Risk Analysis
Identify tracks and characteristics associated with higher skip probability.

### 9. Artist Analysis
Classify artists based on catalog size, popularity, and genre diversity.

### 10. Cross-Genre Discovery
Find opportunities for recommendations across different genres.

### 11. Niche Genre Analysis
Identify smaller or specialized genre opportunities.

### 12. Explicit vs Clean Content Analysis
Compare explicit and clean music content across the catalog.

### 13. Track Duration Analysis
Analyze track length and identify playlist/content opportunities.

### 14. Listening Segment Analysis
Create music-listener segments based on audio characteristics.

### 15. Audio Feature Opportunities
Identify groups of tracks that can support product features.

### 16. Catalog Health Analysis
Measure the overall health and characteristics of the music catalog.

### 17. Product Feature Opportunity Analysis
Convert catalog analysis into potential product features and roadmap priorities.

---

# 💡 Key Insights

The analysis produced several important product opportunities.

### 🎧 Mood-Based Radio

The dataset contained **114,000 tracks** with the required mood-related audio features.

This supported the idea of creating personalized radio experiences based on mood.

**Priority: 1**

---

### 💎 Hidden Gems

The analysis identified **26,473 tracks** with relatively low popularity but strong combinations of danceability, energy, and valence.

This created an opportunity for a **Hidden Gems** discovery experience.

**Priority: 1**

---

### 👤 Artist Discovery Feed

The analysis identified **31,437 distinct artists** that could support an artist discovery experience.

This creates an opportunity to help users discover artists beyond their existing listening patterns.

**Priority: 2**

---

### 🕐 Time-of-Day Playlists

The dataset contained **114,000 tracks** with usable tempo information for contextual playlist analysis.

This supported the idea of playlists designed around different times of day.

**Priority: 3**

---



# 📌 Final Product Opportunities

| Priority | Feature | Result |
|---|---|---|
| **1** | Mood-Based Radio | Personalized music discovery based on mood |
| **1** | Hidden Gems | Discover high-quality, less-popular tracks |
| **2** | Artist Discovery Feed | Discover new and emerging artists |
| **3** | Time-of-Day Playlists | Contextual playlists based on listening time |

---

# 🎯 Final Outcome

The project demonstrates how a large music catalog can be transformed from **raw data into product decisions**.

The final workflow moves through:

**Data → SQL Analysis → Insights → AI Interpretation → Product Opportunities**

The main outcome was a prioritized set of product ideas:

**Mood-Based Radio → Hidden Gems → Artist Discovery Feed → Time-of-Day Playlists**

The project shows how SQL analytics and AI can work together to support **music discovery, personalization, catalog exploration, and product roadmap decisions**.
