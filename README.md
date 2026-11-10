# PlacidWay Social Media Content Automation Workflow

An end-to-end automated pipeline built using **n8n** that extracts publicly available content from PlacidWay, prevents duplicate posting, applies strict AI guardrails against medical hallucination, and publishes engaging posts to a test Facebook Page.

---

## 🛠️ Tech Stack & Automation Architecture
- **Automation Platform:** n8n (Self-hosted or Cloud)
- **Extraction Method:** Sitemap XML parsing via HTTP Request (rate-limited to <1 request/second)
- **State Management & Deduplication:** Google Sheets / Airtable ledger storing posted URLs
- **AI Generation & Guardrails:** OpenAI `gpt-4o-mini` with strict system prompt constraints
- **Publishing & Review:** Facebook Graph API with an optional human approval flag (`APPROVAL_MODE`)

---

## 🚀 Setup & Execution Instructions

1. **Import Workflow:**
   - Open your n8n instance and import the `workflow.json` file.
2. **Configure Credentials:**
   - Set up your **OpenAI API Key** credential in n8n.
   - Configure your **Google Sheets** credential for state tracking.
   - Configure your **Facebook Graph API** credential connected to your test Facebook Page.
3. **Environment Variables:**
   - Set `APPROVAL_MODE=false` for automatic publishing or `true` for human review draft mode.
4. **Run & Test:**
   - Click **Execute Workflow** to perform a manual test run or enable the Schedule Trigger.

---

## 🛡️ Guardrails & Anti-Hallucination Measures
- **Rule-Based & Prompt Guardrails:** The LLM prompt strictly forbids medical outcome promises, absolute guarantees, or price fabrication.
- **State Check:** The ledger ensures no URL is ever posted twice.
