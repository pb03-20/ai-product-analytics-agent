# 🎵 Spotify Product Analytics Agent

> An automated product analytics workflow built with **n8n, PostgreSQL, and Gemini** to transform Spotify catalog data into product insights, feature opportunities, recommendation hypotheses, and roadmap ideas.

---

## 📌 Project Overview

This project demonstrates how a Product Manager can use an automated analytics workflow to move from:

**Raw Spotify Dataset → SQL Analysis → AI-Assisted Interpretation → Product Insights → Feature Opportunities → Roadmap**

Instead of manually analyzing thousands of Spotify tracks, the workflow uses **n8n** as the orchestration layer.

The workflow connects a PostgreSQL database containing Spotify track data to multiple analytical SQL branches. The SQL results are then passed through aggregation and AI analysis steps before being converted into structured product reports.

The goal is not to replace product judgment.

The goal is to **automate repetitive analysis so that more time can be spent on product decisions.**

---

# 🧠 What Problem Does This Solve?

A music product team may have a large catalog containing information such as:

- Track popularity
- Danceability
- Energy
- Valence
- Acousticness
- Tempo
- Instrumentalness
- Speechiness
- Track duration
- Artist
- Genre

The challenge is turning these raw attributes into actionable product questions.

For example:

- Which tracks could support a discovery feature?
- What content could power a mood-based playlist?
- Which tracks look like "hidden gems"?
- Which genres are similar?
- Which artists could be candidates for discovery?
- What tracks have high synthetic skip-risk?
- What content could support a time-based playlist?
- What product experiments could be created from the catalog?

This project automates that analytical process.

---

# 🏗️ Workflow Architecture

The complete workflow is built in **n8n**.

The architecture contains multiple parallel analytical branches. Each branch generally follows this pattern:

```text
PostgreSQL
     ↓
SQL Analysis
     ↓
Aggregate
     ↓
Gemini Analysis
     ↓
JavaScript Processing
     ↓
Product Report
