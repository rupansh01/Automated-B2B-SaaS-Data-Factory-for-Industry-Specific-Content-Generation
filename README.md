
# 🚀 Automated B2B SaaS Data Factory for Industry-Specific Content Generation

**Tech Stack:** n8n · JavaScript · GPT-4 · Airtable · Docker

---

## 📌 Overview

Modern B2B companies rely on **industry-specific messaging** to drive conversions, SEO, and sales enablement.
However, manually creating and maintaining tailored content for multiple industries and data sources is slow, error-prone, and not scalable.

This project implements a **fully automated AI-powered Data Factory** that:

* Ingests SaaS metadata
* Handles scraping restrictions safely using fallback intelligence
* Generates **industry-specific software descriptions using GPT-4**
* Stores clean, structured outputs in Airtable
* Runs on a scheduled, production-ready workflow using **n8n**

---

## 🎯 Problem Statement

Most SaaS directories (G2, Capterra, etc.):

* Are protected by anti-bot mechanisms
* Restrict automated scraping
* Return inconsistent or inaccessible data

At the same time, marketing and sales teams need:

* Industry-specific descriptions (Dentists, Lawyers, Real Estate, etc.)
* Consistent structure across platforms
* Reliable automation without violating ToS

**This project solves that gap** by combining controlled fallback data + structured LLM outputs.

---

## 🧠 Solution Architecture

The system follows a **deterministic, auditable pipeline**:

```
Input (SaaS + Industries + Sources)
        ↓
Industry Split (Dentists, Lawyers, etc.)
        ↓
Source Split (G2 / Capterra)
        ↓
Fallback Data Generation (ToS-safe)
        ↓
GPT-4 Industry-Specific Rewrite (Strict JSON)
        ↓
Structured Parsing & Validation
        ↓
Airtable Storage
```

---

## 🏗️ System Components

### 1️⃣ Input Layer

* SaaS name
* Product slug
* Target industries
* Data sources (G2, Capterra)
* Triggered manually or via cron

### 2️⃣ Workflow Orchestration (n8n)

* Industry-wise fan-out
* Source-wise branching
* Deterministic execution (no hidden loops)
* Full visibility into each step

### 3️⃣ Fallback Intelligence Layer

* Avoids direct scraping of protected platforms
* Uses controlled, domain-agnostic fallback content
* Clearly marks data confidence as `fallback`
* Keeps the system **ToS-compliant**

### 4️⃣ GPT-4 Content Generation

* Strict JSON schema enforced
* No hallucinated fields
* Industry-specific professional tone
* Business-benefit focused rewriting

### 5️⃣ Data Storage (Airtable)

* Clean, relational records
* One record per (software × industry × source)
* Ready for CMS, SEO, or analytics usage

---

## ⚙️ Key Features

* ✅ Industry-wise content generation at scale
* ✅ Source-aware processing (G2 / Capterra)
* ✅ ToS-safe fallback strategy
* ✅ Strict JSON schema enforcement
* ✅ Fully automated, scheduled execution
* ✅ Production-ready workflow design
* ✅ Easily extendable to new industries or tools

---

## 🧩 Technologies Used

| Layer         | Technology   |
| ------------- | ------------ |
| Orchestration | n8n          |
| AI Model      | OpenAI GPT-4 |
| Language      | JavaScript   |
| Storage       | Airtable     |
| Deployment    | Docker       |
| APIs          | REST, OpenAI |

---

## 📂 Project Structure (Conceptual)

```
├── n8n-workflows/
│   └── automated-saas-data-factory.json
├── architecture.md
├── docker-compose.yml
├── README.md
├── Airtable-screenshot.png
```

---

## 🚀 How to Run Locally

### 1️⃣ Prerequisites

* Docker & Docker Compose
* OpenAI API key
* Airtable Personal Access Token

### 2️⃣ Start n8n

```bash(for mac m3 users)
docker run -it --rm \ 

  -p 5678:5678 \ 

  -e N8N_BASIC_AUTH_ACTIVE=false \ 

  N8nio/n8n 
```

### 3️⃣ Configure Credentials

* OpenAI API key in n8n credentials
* Airtable base + table mapping
* Optional: Cron scheduling

### 4️⃣ Execute Workflow

* Manual trigger or scheduled trigger
* Outputs stored automatically in Airtable

---

## 📊 Sample Output

Each execution produces structured records like:

* **Software Name:** Notion
* **Industry:** Dentists
* **Source:** G2
* **Rating:** 4.4
* **Rewritten Description:**

  > Industry-specific, professional, business-focused content

---

## 🔐 Compliance & Safety

* ❌ No direct scraping of protected platforms
* ✅ ToS-safe fallback content
* ✅ Transparent data confidence labeling
* ✅ Deterministic and auditable outputs

---

## 🔮 Future Enhancements

* Add more SaaS directories (Product Hunt, AlternativeTo)
* SEO keyword optimization per industry
* CMS integrations (Webflow, WordPress)
* Analytics dashboard for content performance
* Vector database for semantic search

---

## 📌 Why This Project Matters

This project demonstrates:

* Real-world AI system design
* Practical handling of scraping constraints
* Reliable LLM usage with strict outputs
* Scalable automation engineering
* Production-ready orchestration thinking

It is not a demo — **it’s an applied AI automation system.**

---

## 👤 Author

**Rupansh Kumar**
AI Automation & Platform Engineer

* GitHub: [https://github.com/rupansh01](https://github.com/rupansh01)
* LinkedIn: [https://www.linkedin.com/in/rupanshkumar](https://www.linkedin.com/in/rupanshkumar)

---

## ⭐ Final Note

If you're looking to build **reliable, scalable, and compliant AI automation systems**, this project serves as a strong real-world blueprint.

