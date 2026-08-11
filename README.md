# Spotify Product Analytics Automation

An automated **n8n + PostgreSQL + Gemini** workflow that analyzes Spotify track data and converts SQL results into product insights and recommendations.

## Workflow

![n8n Workflow](docs/n8n-workflow-full.png)

The workflow starts from a manual trigger and fans out into multiple independent SQL analyses.

```text
Manual Trigger
      ↓
PostgreSQL SQL Queries
      ↓
Aggregate Results
      ↓
Gemini Analysis
      ↓
JavaScript Formatting
      ↓
Product Reports
