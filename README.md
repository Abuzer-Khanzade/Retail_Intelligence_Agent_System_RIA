# 📘 Retail Intelligence Agent System (RIA)
### Multi-Agent Retail Analytics Using Google ADK & Gemini

**Track: Enterprise Agents**

---

## 🚀 Overview

The Retail Intelligence Agent System (RIA) is a multi-agent AI solution that automates enterprise retail analytics. Built using Google’s Agent Development Kit (ADK) and Gemini LLMs, RIA replaces manual retail reporting with automated insights, forecasting, and strategic recommendations.

RIA acts as a virtual retail analyst, capable of:

- 🔍 Automated retail insights
- 📈 Time-series forecasting
- 🧩 Strategy recommendations
- 🧭 Intelligent agent routing
- 🛰 Full observability & debugging
- 🧠 Multi-turn conversational analytics

This project demonstrates how intelligent agents can reduce analyst workload and deliver instant, business-ready intelligence.

---

## 🗂 Table of Contents

- Introduction
- Project Features
- Architecture Overview
- Dataset
- Technical Components
- Agents & Tools
- Coordinator Routing
- End-to-End Flow
- Installation
- How to Run
- Example Queries
- Results
- Limitations
- Future Work
- Conclusion

---

## 📖 Introduction

Retail analytics teams spend countless hours on:

- KPI calculations
- Region/category analysis
- Demand forecasting
- Strategy recommendations
- Report preparation

**RIA automates all of this.**

Using intelligent multi-agent orchestration, custom analytical tools, and Gemini reasoning, the system converts raw retail data into actionable insights with:

- Multi-agent execution
- Rule-based routing
- Session memory
- Full observability using `run_debug()`
- Natural language query handling

---

## ⭐ Project Features

| Feature | Description |
|--------|-------------|
| Multi-Agent System | Insights, Forecast, Recommendation, Router |
| Custom Tools | Sales analytics, Holt–Winters forecasting |
| Gemini LLM | Natural language intelligence |
| Google ADK | Production-grade agent orchestration |
| Session Memory | Multi-turn, context-aware interactions |
| Observability | Logs, traces, debugging via `run_debug()` |
| Automatic Routing | Keyword-based query dispatch |

---

## 🧱 Architecture Overview

```
 ┌──────────────────────────────────────────┐
 │           Coordinator Agent              │
 │     (Routes the user query)              │
 └───────────────┬───────────────┬─────────┘
                 │               │
       ┌─────────▼────────┐   ┌──▼───────────┐
       │   InsightsAgent   │   │ ForecastAgent │
       │  (Historical KPIs)│   │ (Time-Series) │
       └─────────┬─────────┘   └─────┬────────┘
                 │                   │
                 └──────────┬────────┘
                            ▼
               ┌────────────────────────┐
               │  RecommendationAgent   │
               │ (Insights + Forecast → │
               │   Strategy Output)     │
               └────────────────────────┘
```

---

## 📦 Dataset

Dataset used: **Superstore Retail Dataset**

Contains:

- Sales, Profit, Discounts
- Quantity
- Categories, Sub-Categories
- Regions & Segments
- Order/Ship Dates

Preprocessing includes:

- Date parsing
- Cleaning invalid sales
- Dropping missing values
- Feature engineering: Year, Month, Quarter

---

## 🧠 Technical Components

This project highlights:

### ✔ Google ADK
- LlmAgent
- Runner, InMemoryRunner
- FunctionTool
- InMemorySessionService

### ✔ Gemini Models
- Gemini 2.5 Flash Lite
- Natural language interpretation and reasoning

### ✔ Observability
Full execution traces using:

```python
await runner.run_debug()
```

---

## 🤖 Agents & Tools

### 🔍 InsightsAgent

Provides grouped KPIs:

- Total Sales
- Total Profit
- Avg Discount
- Avg Profit
- Total Quantity

Uses:
- ✔ insights_tool
- ✔ Gemini model

---

### 📈 ForecastAgent

Predicts the next 3 months of regional sales using:

- Holt–Winters Exponential Smoothing
- Monthly aggregated time series

Uses:
- ✔ forecast_sales tool

---

### 🧩 RecommendationAgent

Combines:

- Insights
- Forecast
- LLM reasoning

Produces:

- Profit improvement strategies
- Inventory & discount suggestions
- Category/region recommendations

---

## 🧭 Coordinator Routing

Simple rule-based router:

```python
def route_query(query):
    if "forecast" in query:
        return "forecast"
    if "recommend" in query:
        return "recommend"
    return "insights"
```

Inspired by A2A (Agent-to-Agent) routing from Google ADK Day-5.

---

## 🚀 End-to-End Flow

- User asks a question
- Coordinator routes it to the correct agent
- Agent invokes the correct tool
- LLM processes tool outputs
- Final answer returned with full trace

---

## 🛠 Installation

Create a `requirements.txt`:

```
pandas
matplotlib
numpy
statsmodels
google-adk
google-genai
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## ▶ How to Run

In your notebook:

```python
import os
os.environ["GOOGLE_API_KEY"] = "YOUR_API_KEY"
```

Then run:

```python
await run_ria("Compare sales by Region")
```

---

## 💬 Example Queries

- “Show me sales and profit grouped by Category.”
- “Forecast the next 3 months for the West region.”
- “Recommend strategies to increase profit in Furniture.”
- “Which region has the highest profitability?”
- “Give me insights on Office Supplies performance.”

---

## 📊 Results

The notebook outputs:

- 📉 Monthly sales trend chart
- 🔮 3-month forecast
- 🏷 Category profitability metrics
- 🧠 Strategic business recommendations
- 🔎 Full execution trace and debug logs

---

## ⚠ Limitations

- Holt–Winters cannot model sudden market shocks
- Keyword-based routing may misclassify queries
- Forecasting limited to region-level
- No BigQuery or live data ingestion
- No UI (CLI/Notebook only)

---

## 🔮 Future Work

- Replace Holt–Winters with Prophet / ARIMA / LSTM
- Add specialized agents:
  - PricingAgent
  - InventoryAgent
  - SupplyChainAgent
- Deploy on Vertex Agent Engine
- Add long-term memory storage
- Build Streamlit/Gradio interface
- Integrate BigQuery for enterprise scale

---

## 🧠 Conclusion

The Retail Intelligence Agent System (RIA) showcases the power of multi-agent AI for enterprise analytics.

Using:

- Google ADK
- Gemini 2.5 Flash Lite
- Custom tools
- Observability
- Intelligent routing

RIA transforms raw retail data into:

- Actionable insights
- Demand forecasts
- Strategic recommendations

This project demonstrates how AI agents will shape the future of automated retail decision-making.
