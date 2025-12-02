# n8n Newsjacking Agent

A fully automated AI-powered **newsjacking pipeline** built with **n8n**.  
This workflow fetches AI-related news from multiple sources, filters and classifies articles, scores and ranks them based on platform-specific criteria, generates LinkedIn and Twitter drafts, merges them, and composes a complete daily digest email.

This repository contains the full automation logic as an n8n workflow export.

---

## 🚀 Features

### **News Ingestion**
- Pulls articles from multiple RSS feeds (AI, tech, finance, insurance)
- Deduplicates at source level
- Extracts titles, summaries, publish dates, and authors
- Normalizes article structure

### **Intelligent Filtering**
- Keyword-based filtering for AI-relevant content
- Time-window filtering (e.g., last 24 hours or since last digest)
- Summary cleaning and HTML sanitation

### **Channel Classification (LLM-powered)**
Each article is evaluated to determine appropriate platforms:
- **Twitter/X** → buzzy, hype-cycle, breaking AI news  
- **LinkedIn** → enterprise, governance, risk, finance/insurance implications  
- **Dual** → news with both hype and enterprise relevance  

Classification rules are explicitly defined in the workflow.

### **Ranking Engines (LLM-powered)**
Three ranking engines evaluate each article independently:

- **Twitter Ranking Engine**  
  Scores by buzz, novelty, virality, ecosystem impact, and headline punchiness.

- **LinkedIn Ranking Engine**  
  Scores by enterprise relevance, operational impact, industry transformation, and practical applicability.

- **Dual-Platform Ranking Engine**  
  Scores for both audiences simultaneously.

Each engine:
- Clusters similar articles  
- Deduplicates based on source priority  
- Assigns rank  
- Outputs structured JSON  

### **Curator Engine**
- Applies score thresholds
- Enforces quotas per channel (Twitter, LinkedIn, Dual)
- Fills gaps with highest-scoring remaining articles  
- Removes duplicates  
- Produces **8–15 final daily highlight articles**

### **Post Generators**
Two LLM-based post generators craft platform-ready content:

- **LinkedIn Post Generator**  
  Creates professional insights, optionally tied to enterprise AI themes.

- **Twitter Post Generator**  
  Creates short, high-engagement posts with platform-specific tone.

### **Unified Article Merger**
- Combines LinkedIn + Twitter drafts for each article  
- Preserves exact post text  
- Outputs a unified article structure

### **Digest Email Builder**
- Generates a clean, readable daily email containing:
  - Overview summary  
  - Source statistics  
  - Article list  
  - Both posts for each article  
- Ready for sending through any email integration


