# Delta-Reg Python SDK & API Wrapper 🏛️⚖️

An automated AI-compliance tool for FinTechs, Risk Managers, and LegalTech developers. 

Delta-Reg acts as a digital compliance officer. It bypasses government bot-blockers to scrape dynamic regulatory websites (like the FTC) and uses Google Gemini to cross-reference the live text against your company's internal JSON policies. 

It instantly identifies compliance gaps, mandatory technical upgrades, and provides an urgency score.

---

## 🔑 Getting Started

Delta-Reg is a premium API. To use this SDK, you need a subscription key.
**👉 [Get your API Key and view full documentation here]([https://www.notion.so/Delta-Reg-API-339a551b9183801aaa37f8c78b193a7c])**

*(Note: Delta-Reg uses a Bring-Your-Own-Key (BYOK) architecture. You will need to pass your own Google Gemini API key in the headers alongside your Delta-Reg key).*

---

## 💻 Python Quickstart

You don't need to install any heavy libraries to use Delta-Reg. It is a simple REST API. Here is the exact Python script to test your compliance against a live FTC press release.

```python
import requests
import json

# 1. Define the API endpoint
URL = "[https://delta-reg-api.onrender.com/analyze-delta](https://delta-reg-api.onrender.com/analyze-delta)"

# 2. Add your keys (Get your Delta-Reg key from the Notion link above)
HEADERS = {
    "x-delta-reg-key": "dr_your_delta_reg_key_here",
    "byok-api-key": "your_google_gemini_key_here",
    "Content-Type": "application/json"
}

# 3. Define the target agency and your company's internal policy
PAYLOAD = {
  "target_agency": "[https://www.ftc.gov/news-events/news/press-releases](https://www.ftc.gov/news-events/news/press-releases)",
  "user_policy": {
    "company_name": "FinTech Secure LLC",
    "data_retention": "We store user financial data for 3 years.",
    "encryption": "AES-128 bit encryption on all databases.",
    "compliance_focus": "Consumer financial protection and data breach reporting."
  }
}

# 4. Run the digital compliance officer
response = requests.post(URL, json=PAYLOAD, headers=HEADERS)

print(f"Status Code: {response.status_code}")
print(json.dumps(response.json(), indent=2))
```

## 📊 Sample JSON Output
The API strictly returns parsed JSON that you can instantly save to your internal database or display on a dashboard:

```json
{
  "delta_detected": true,
  "impact_summary": "The FTC recently emphasized stricter data security protocols. While your policy mentions AES-128, current guidelines strongly suggest AES-256 for financial data.",
  "required_technical_changes": "Upgrade database encryption to AES-256 to meet updated regulatory standards.",
  "urgency_score": 8
}
```

## 🛠️ Stack
* FastAPI
* Playwright (Headless Web Scraping)
* Google Gemini (LLM)
* Supabase
