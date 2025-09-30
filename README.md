# stock-analysis-telegram-bot
📈 Telegram bot that delivers comprehensive US stock analysis combining real-time technical data, AI-powered news sentiment, and fundamental metrics. Get dual-timeframe recommendations for day trading and long-term investing.
# 📈 US Stock Market Analysis Agent

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![n8n](https://img.shields.io/badge/n8n-Automation-orange)](https://n8n.io/)
[![DeepSeek](https://img.shields.io/badge/AI-DeepSeek-blue)](https://deepseek.com/)
[![Telegram Bot](https://img.shields.io/badge/Telegram-Bot-26A5E4)](https://telegram.org/)
> **Intelligent stock analysis agent that delivers comprehensive trading and investment recommendations via Telegram. Get real-time technical analysis, sentiment scoring, and long-term investment metrics for any US stock symbol.**

Simply message your Telegram bot with a stock ticker (e.g., "AAPL") and receive professional-grade analysis combining technical indicators, news sentiment, and fundamental data.

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [How It Works](#-how-it-works)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage Examples](#-usage-examples)
- [Analysis Components](#-analysis-components)
- [Troubleshooting](#-troubleshooting)
- [Best Practices](#-best-practices)
- [License](#-license)

---

## 🎯 Overview

**US Stock Market Analysis Agent** is a sophisticated Telegram bot that provides dual-timeframe stock analysis. It combines real-time technical data, AI-powered news sentiment analysis, and fundamental metrics to deliver actionable insights for both day traders and long-term investors.

### What Makes This Special?

- 📱 **Telegram Interface** - Access analysis anywhere via your phone
- ⚡ **Real-Time Data** - Live price action across multiple timeframes (1m, 15m, 1h)
- 🧠 **AI-Powered Analysis** - DeepSeek AI interprets complex market data
- 📰 **News Sentiment** - Automated sentiment scoring from recent articles
- 💼 **Fundamental Metrics** - Dividend yield, P/E ratios, earnings growth
- 🎯 **Dual Recommendations** - Separate advice for day trading and long-term investing

### Who Is This For?

- 📊 **Day Traders** - Get technical signals with entry/exit points
- 💰 **Long-Term Investors** - Fundamental analysis with expected annual returns
- 📈 **Swing Traders** - Multi-timeframe analysis for timing entries
- 🎓 **Learning Traders** - Understand professional analysis methodology
- 🤖 **Algorithmic Traders** - Integrate structured data into your systems

---

## ✨ Key Features

### 📱 **Telegram Bot Interface**
- Send any US stock ticker symbol
- Receive comprehensive analysis in seconds
- Mobile-first design for on-the-go trading
- Private bot for personal use
- Fast response times

### 📊 **Multi-Timeframe Technical Analysis**
- 1-minute candles for scalping
- 15-minute candles for intraday trends
- 1-hour candles for swing positions
- OHLC data with 100 candles per timeframe
- Normalized and chronologically sorted data

### 📰 **AI News Sentiment Analysis**
- Google News RSS integration
- NewsAPI for comprehensive coverage
- Article content extraction and summarization
- Sentiment scoring (-1 to 1 scale)
- Categorical classification (Positive/Neutral/Negative)
- Detailed rationale for sentiment determination

### 💼 **Fundamental Analysis**
- Company profile (sector, industry, description)
- Dividend history and yield calculation
- Earnings data and EPS growth
- Valuation metrics (P/E, P/B, PEG ratios)
- Financial health (ROE, ROA, debt-to-equity)
- Expected annual return calculation

### 🎯 **Dual-Timeframe Recommendations**

**Short-Term (Day Trading):**
- Technical recommendation (BUY/SELL/HOLD)
- Specific entry price
- Stop-loss level
- Target/exit price
- Trading rationale

**Long-Term (Investment):**
- Investment recommendation (BUY/HOLD/AVOID)
- Current dividend yield
- Expected annual return
- P/E ratio analysis
- Key strengths and risks
- Investment rationale

### 🤖 **AI-Powered Insights**
- DeepSeek model for cost-effective analysis
- Context-aware recommendations
- Professional analyst-style output
- Risk level assessment
- Time horizon preferences

---

## 🔄 How It Works

### User Experience

```
You: AAPL

[Bot processes in seconds]

Bot: 📈 APPLE INC (AAPL) ANALYSIS

    COMPANY INFORMATION
    Sector: Technology
    Industry: Consumer Electronics
    
    SHORT-TERM TRADING (Day Trading)
    Technical Recommendation: BUY
    Entry Price: $185.20
    Stop-Loss: $183.50
    Target Price: $188.00
    
    LONG-TERM INVESTMENT
    Investment Recommendation: BUY
    Current Dividend Yield: 0.52%
    Expected Annual Return: 12.5%
    P/E Ratio: 29.3
    
    [Full detailed analysis...]
```

### Technical Flow

```
User Sends Stock Ticker (Telegram)
     ↓
Telegram Trigger Activates
     ↓
Parallel Data Fetching:
  ├─ 1min Candles (TwelveData API)
  ├─ 15min Candles (TwelveData API)
  ├─ 1hour Candles (TwelveData API)
  ├─ Dividends Data
  ├─ Earnings Data
  ├─ Statistics Data
  ├─ Company Profile
  ├─ Google News RSS
  └─ NewsAPI Articles
     ↓
Data Processing:
  ├─ Merge & Aggregate Timeframes
  ├─ Normalize Candle Data
  ├─ Process Fundamentals
  ├─ Calculate Long-term Metrics
  ├─ Extract & Summarize News
  └─ Sentiment Analysis (GPT-4o-mini)
     ↓
Final Aggregation
     ↓
AI Financial Analyst (DeepSeek)
     ↓
Send Analysis to Telegram
```

---

## 🏗️ System Architecture

### Data Collection Layer

```
┌─────────────────────────────────────────────────────────────┐
│                    TELEGRAM TRIGGER                          │
│            (Receives stock ticker symbol)                    │
└───────────────────────┬─────────────────────────────────────┘
                        │
        ┌───────────────┴───────────────┐
        ↓                               ↓
┌──────────────────┐          ┌──────────────────┐
│  TECHNICAL DATA  │          │   NEWS SOURCES   │
│  (TwelveData)    │          │                  │
├──────────────────┤          ├──────────────────┤
│ • 1min candles   │          │ • Google News    │
│ • 15min candles  │          │ • NewsAPI        │
│ • 1hour candles  │          │                  │
│ • Dividends      │          └──────────────────┘
│ • Earnings       │
│ • Statistics     │
│ • Profile        │
└──────────────────┘
```

### Processing Layer

```
┌─────────────────────────────────────────────────────────────┐
│                    DATA PROCESSING                           │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌──────────────────┐  ┌──────────────────┐               │
│  │ Process Candles  │  │ Process Metrics  │               │
│  │ • Normalize      │  │ • Dividends      │               │
│  │ • Sort by time   │  │ • Earnings       │               │
│  │ • Format OHLC    │  │ • Valuations     │               │
│  └──────────────────┘  │ • Calculate ROI  │               │
│                        └──────────────────┘               │
│                                                              │
│  ┌──────────────────────────────────────┐                  │
│  │     News Sentiment Analysis          │                  │
│  │     (GPT-4o-mini)                    │                  │
│  ├──────────────────────────────────────┤                  │
│  │ • Validate ticker & articles         │                  │
│  │ • Extract article content            │                  │
│  │ • Analyze sentiment                  │                  │
│  │ • Score: -1 to +1                    │                  │
│  │ • Category: Positive/Neutral/Negative│                  │
│  └──────────────────────────────────────┘                  │
└─────────────────────────────────────────────────────────────┘
```

### Analysis & Output Layer

```
┌─────────────────────────────────────────────────────────────┐
│              AI FINANCIAL ANALYST (DeepSeek)                 │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Input: Technical Data + Sentiment + Fundamentals           │
│                                                              │
│  Output:                                                     │
│  ┌──────────────────────────────────────────────┐          │
│  │ SHORT-TERM TRADING RECOMMENDATION            │          │
│  │ • Entry/Stop-Loss/Target                     │          │
│  └──────────────────────────────────────────────┘          │
│  ┌──────────────────────────────────────────────┐          │
│  │ LONG-TERM INVESTMENT RECOMMENDATION          │          │
│  │ • Expected Return, Yield, Valuation          │          │
│  └──────────────────────────────────────────────┘          │
│  ┌──────────────────────────────────────────────┐          │
│  │ OVERALL ASSESSMENT                           │          │
│  │ • Risk Level, Time Horizon, Summary          │          │
│  └──────────────────────────────────────────────┘          │
└───────────────────────┬─────────────────────────────────────┘
                        ↓
              ┌───────────────────┐
              │  TELEGRAM OUTPUT  │
              │  (Send to user)   │
              └───────────────────┘
```

---

## 🛠️ Tech Stack

| Category | Technology | Purpose |
|----------|------------|---------|
| **Automation** | n8n | Workflow orchestration |
| **AI Analysis** | DeepSeek | Financial analysis and recommendations |
| **Sentiment AI** | OpenAI GPT-4o-mini | News sentiment analysis |
| **Stock Data** | TwelveData API | Real-time prices, fundamentals |
| **News Data** | Google News RSS + NewsAPI | Market sentiment sources |
| **Interface** | Telegram Bot | User interaction |
| **Trigger** | n8n Telegram Trigger | Workflow activation |
| **Data Processing** | JavaScript (n8n Code nodes) | Custom data transformations |

---

## 📦 Prerequisites

### Required Accounts & API Keys

| Service | Required? | Purpose | Cost |
|---------|-----------|---------|------|
| **n8n** | ✅ Yes | Run workflows | Free (self-hosted) or $20/mo |
| **TwelveData** | ✅ Yes | Stock market data | Free tier: 800 requests/day |
| **DeepSeek** | ✅ Yes | AI financial analysis | $0.27/million tokens (~$0.01/query) |
| **OpenAI** | ✅ Yes | Sentiment analysis | GPT-4o-mini: ~$0.001/query |
| **NewsAPI** | ✅ Yes | News articles | Free tier: 100 requests/day |
| **Telegram Bot** | ✅ Yes | User interface | Free |

### API Keys Needed

- ✅ TwelveData API Key
- ✅ DeepSeek API Key
- ✅ OpenAI API Key
- ✅ NewsAPI API Key
- ✅ Telegram Bot Token

### Technical Requirements

- n8n instance (v1.0+)
- Telegram account
- Stable internet connection

---

## 🚀 Installation

### Step 1: Create Telegram Bot

1. Open Telegram and message **@BotFather**
2. Send `/newbot` command
3. Choose a name: "My Stock Analyzer"
4. Choose username: "mystockanalyzer_bot"
5. **Save the bot token** provided
6. Get your Telegram user ID from **@userinfobot**

### Step 2: Import Workflow

1. Open your n8n instance
2. **Workflows** → **Import from File**
3. Select `uS-stocks-workflow.json`
4. Click **Import**

### Step 3: Configure API Keys

Update the following nodes with your credentials:

#### TwelveData API (7 nodes)
- HTTP 1 Minutes
- HTTP 15 Minutes
- HTTP 1 Hour
- HTTP Dividends
- HTTP Earnings
- HTTP Statistics
- HTTP Profile

Replace: `YOUR_TWELVEDATA_API_KEY`

#### NewsAPI
- News API node

Replace: `YOUR_NEWSAPI_API_KEY`

#### OpenAI Credentials
- Sentiment Analysis node
- Add OpenAI credential in n8n settings

#### DeepSeek Credentials
- DeepSeek Chat Model node
- Add DeepSeek credential in n8n settings

#### Telegram Configuration
- Telegram Trigger node
- Telegram Tool node
- Add bot token and user ID

### Step 4: Update Telegram User ID

In **Telegram Trigger** node:
- Replace `YOUR_TELEGRAM_USER_ID` with your ID

### Step 5: Activate Workflow

1. Click **Active** toggle in top-right
2. Workflow should turn green
3. Bot is now ready!

---

## ⚙️ Configuration

### 1. TwelveData API Key

**Where to get:**
1. Sign up at https://twelvedata.com/
2. Navigate to dashboard
3. Copy API key
4. Free tier: 800 API calls/day

**Update in all 7 HTTP nodes:**
```javascript
"apikey": "YOUR_TWELVEDATA_API_KEY"
```

**Parameters explained:**
- `symbol`: Stock ticker (from user message)
- `interval`: Timeframe (1min, 15min, 1h)
- `outputsize`: Number of candles (100)

---

### 2. DeepSeek API Configuration

**Where to get:**
1. Sign up at https://platform.deepseek.com/
2. Get API key from dashboard

**In n8n:**
1. **Settings** → **Credentials**
2. Add **"DeepSeek account"**
3. Paste API key
4. Select in "DeepSeek Chat Model" node

**Model:** deepseek-chat (default)

---

### 3. OpenAI API Configuration

**Where to get:**
1. Visit https://platform.openai.com/api-keys
2. Create new API key

**In n8n:**
1. **Settings** → **Credentials**
2. Add **"OpenAi account"**
3. Paste API key
4. Select in "Sentiment Analysis" node

**Model:** gpt-4o-mini (cost-effective for sentiment)

---

### 4. NewsAPI Configuration

**Where to get:**
1. Sign up at https://newsapi.org/
2. Copy API key from dashboard
3. Free tier: 100 requests/day

**Update in News API node:**
```javascript
"apikey": "YOUR_NEWSAPI_API_KEY"
```

---

### 5. Telegram Bot Setup

**In Telegram Trigger node:**
```javascript
"userIds": "YOUR_TELEGRAM_USER_ID"
```

**In Send Telegram Message node:**
The chat ID is automatically pulled from the trigger.

---

## 📖 Usage Examples

### Example 1: Large Cap Tech Stock

**You:** `AAPL`

**Analysis Includes:**
- Current price action across 3 timeframes
- Technical recommendation for day trading
- Dividend yield and expected annual return
- P/E ratio and valuation metrics
- Recent news sentiment analysis
- Risk assessment

---

### Example 2: High-Dividend Stock

**You:** `T`

**Analysis Shows:**
- Strong dividend yield (>5%)
- Long-term investment potential
- Financial health metrics
- Dividend sustainability analysis
- Conservative risk profile

---

### Example 3: Growth Stock

**You:** `TSLA`

**Analysis Provides:**
- High volatility warning
- Short-term trading signals
- Growth metrics without dividends
- News sentiment impact
- Risk level: HIGH

---

### Example 4: Index ETF

**You:** `SPY`

**Analysis Covers:**
- Broad market technical trends
- Lower risk assessment
- Dividend characteristics
- Market sentiment overview
- Time horizon: LONG-TERM

---

## 📊 Analysis Components

### Short-Term Trading Analysis

| Component | Description |
|-----------|-------------|
| **Technical Recommendation** | BUY/SELL/HOLD based on price action |
| **Entry Price** | Suggested entry point |
| **Stop-Loss** | Risk management level |
| **Target Price** | Profit-taking level |
| **Trading Rationale** | Technical reasoning |

### Long-Term Investment Analysis

| Component | Description |
|-----------|-------------|
| **Investment Recommendation** | BUY/HOLD/AVOID based on fundamentals |
| **Dividend Yield** | Annual dividend percentage |
| **Expected Annual Return** | Projected yearly gain |
| **P/E Ratio** | Valuation metric |
| **Key Strengths** | Positive investment factors |
| **Key Risks** | Potential concerns |
| **Investment Rationale** | Fundamental reasoning |

### Sentiment Analysis

| Metric | Range | Meaning |
|--------|-------|---------|
| **Score** | -1 to +1 | Numerical sentiment (-1 very negative, +1 very positive) |
| **Category** | Positive/Neutral/Negative | Qualitative classification |
| **Rationale** | Text | Detailed explanation of sentiment determination |

---

## 🐛 Troubleshooting

### Issue: Bot Not Responding

**Symptoms:** No response when sending ticker

**Solutions:**
1. Verify workflow is **Active**
2. Check Telegram bot token is correct
3. Confirm your user ID is in trigger node
4. Test bot directly: send `/start` command
5. Check n8n executions for errors

---

### Issue: "Invalid API Key" Errors

**Symptoms:** Workflow fails with authentication error

**Solutions:**
1. Verify all API keys are correctly pasted
2. Check no extra spaces in API key fields
3. Confirm API keys are active/not expired
4. Test APIs individually via browser/Postman
5. Check API rate limits aren't exceeded

---

### Issue: No Technical Data Returned

**Symptoms:** Missing price/candle information

**Solutions:**
1. Confirm valid US stock ticker symbol
2. Check TwelveData API quota (800/day)
3. Verify ticker is available on TwelveData
4. Try different ticker (e.g., AAPL, MSFT)
5. Check market hours (data may be delayed)

---

### Issue: Sentiment Analysis Fails

**Symptoms:** Missing sentiment scores

**Solutions:**
1. Verify OpenAI API key is correct
2. Check quota for GPT-4o-mini
3. Confirm news articles are being fetched
4. Review NewsAPI and Google News nodes
5. Check if ticker has recent news coverage

---

### Issue: Incomplete Analysis

**Symptoms:** Some sections missing

**Solutions:**
1. Some stocks lack dividend/earnings data
2. Newly listed companies may have limited data
3. ETFs may not have all fundamental metrics
4. Try well-established large-cap stocks first
5. Review n8n execution logs for specific errors

---

## 💡 Best Practices

### Choosing Stock Tickers

✅ **Good:**
- Use standard US ticker symbols (AAPL, MSFT, GOOGL)
- Large-cap stocks have more complete data
- Established companies provide better analysis
- Major indices work well (SPY, QQQ, DIA)

❌ **Avoid:**
- Non-US stocks (limited data)
- Penny stocks (unreliable data)
- Recently IPO'd companies (insufficient history)
- Crypto tickers (not supported)

---

### Cost Optimization

**TwelveData (Biggest concern):**
- Free tier: 800 calls/day
- Each analysis = 7 API calls
- Daily capacity: ~110 stock analyses
- Upgrade to paid if needed ($49/mo = 8,000 calls/day)

**AI Costs (Very low):**
- DeepSeek: ~$0.01 per analysis
- OpenAI GPT-4o-mini: ~$0.001 per sentiment
- 100 analyses: ~$1.10 total AI cost

**NewsAPI:**
- Free tier: 100 calls/day
- Each analysis = 1 call
- Sufficient for personal use

---

### Interpretation Guidelines

**Technical Recommendations:**
- Consider multiple timeframes
- Validate entry/stop-loss levels
- Use proper position sizing
- Don't trade solely on bot advice

**Long-Term Recommendations:**
- Expected returns are estimates
- Consider your own risk tolerance
- Diversify your portfolio
- Review fundamentals independently

**Risk Levels:**
- **LOW:** Stable, established companies
- **MEDIUM:** Growth stocks with volatility
- **HIGH:** Speculative, high-beta stocks

---

### Timing Your Queries

**Best Times:**
- During market hours (9:30 AM - 4:00 PM ET)
- After major news releases
- Before earnings reports
- Weekly for long-term holdings

**Avoid:**
- Pre-market/after-hours (limited data)
- Weekends (stale data)
- Market holidays (no updates)

---

## 💰 Cost Breakdown

### Per Analysis (Single Stock Query)

| Service | Usage | Cost |
|---------|-------|------|
| **TwelveData** | 7 API calls | $0.00 (free tier) |
| **DeepSeek** | 1 analysis | ~$0.01 |
| **OpenAI** | 1 sentiment | ~$0.001 |
| **NewsAPI** | 1 call | $0.00 (free tier) |
| **Telegram** | Messages | $0.00 |
| **Total** | Per stock | **~$0.011** |

### Monthly Costs (100 analyses)

- **TwelveData:** Free (within 800/day limit)
- **DeepSeek:** ~$1.00
- **OpenAI:** ~$0.10
- **NewsAPI:** Free (within 100/day limit)
- **Total:** **~$1.10/month for 100 analyses**

**Cost per analysis:** $0.011

---

## 📈 Use Cases

### 1. Daily Trading Preparation

**Morning Routine:**
- Query watchlist tickers (5-10 stocks)
- Review technical recommendations
- Set alerts based on entry prices
- Monitor sentiment changes

### 2. Earnings Season Monitoring

**Before Earnings:**
- Check sentiment leading up to report
- Review technical levels
- Assess current valuation metrics

### 3. Long-Term Portfolio Review

**Monthly Check:**
- Query all holdings
- Review expected annual returns
- Assess dividend yields
- Validate investment thesis

### 4. New Investment Research

**Initial Screening:**
- Get comprehensive overview
- Compare to industry peers
- Evaluate risk/return profile
- Determine time horizon fit

### 5. Quick Market Pulse

**Throughout Day:**
- Check major indices (SPY, QQQ)
- Monitor key holdings
- React to news events
- Validate trading decisions

---

## 📄 License

This project is licensed under the **MIT License**.

✅ Commercial use allowed  
✅ Modification allowed  
✅ Distribution allowed  
✅ Private use allowed  
⚠️ No warranty or liability

---

## 🌟 Acknowledgments

Built with powerful tools:

- [n8n](https://n8n.io) - Workflow automation platform
- [DeepSeek](https://deepseek.com) - Cost-effective AI analysis
- [OpenAI GPT-4o-mini](https://openai.com) - Sentiment analysis
- [TwelveData](https://twelvedata.com) - Stock market data API
- [NewsAPI](https://newsapi.org) - News data provider
- [Telegram](https://telegram.org) - Bot platform

---

## 🚀 Future Enhancements

### Planned Features

- [ ] Portfolio tracking and performance analysis
- [ ] Custom alerts for price/volume triggers
- [ ] Multi-stock comparison reports
- [ ] Options trading analysis
- [ ] Sector rotation recommendations
- [ ] Backtesting capabilities
- [ ] Technical indicator customization
- [ ] Export to PDF/CSV
- [ ] Web dashboard integration
- [ ] Webhook support for other platforms

---

## 📞 Support

**Disclaimer:** This tool provides analysis for educational and informational purposes only. Not financial advice. Always do your own research and consult with licensed financial advisors before making investment decisions.

---

**Made with 📈 for traders and investors**

⭐ Use responsibly and trade safely!

🔐 Keep your API keys secure!

📊 Make informed decisions with data-driven insights!

---
