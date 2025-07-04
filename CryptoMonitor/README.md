# CryptoMonitor Bot 🚦📈

**Crypto Monitor**
*Version 3.0 – Professional UI, Desktop Notifications & TP/SL Persistence*

---

## What is CryptoMonitor?
CryptoMonitor is an advanced, open-source crypto trading bot for real-time market analysis and automated trading. It leverages robust moving average analytics, live price feeds, and multiple APIs to help you trade smarter. Version 3.0 introduces a professional UI, desktop notifications, TP/SL persistence, and enhanced user experience.

---

## ✨ What's New in v3.0

### 🎨 **Professional UI & User Experience**
- **Clean, Uniform Design:** Reduced excessive borders and emojis for a professional appearance
- **Organized Information Sections:** Logical grouping with clear headers and consistent formatting
- **Tasteful Emoji Usage:** Strategic emoji placement for visual cues without clutter
- **Easy-to-Read Format:** Clean, organized output suitable for trading environments

### 🔔 **Desktop Notifications System**
- **Signal Notifications:** Instant alerts when BUY/SELL signals are detected
- **Trade Notifications:** Real-time updates for order execution, fills, and completion
- **TP/SL Notifications:** Alerts for take profit hits, stop loss triggers, and MA crossunders
- **Error Notifications:** Desktop alerts for market errors, API issues, and trade problems
- **Status Notifications:** Monitor startup, position updates, and system status changes
- **Cross-Platform Support:** Windows Toast notifications with console fallback

### 💾 **TP/SL Persistence System**
- **Llama-Generated Values:** Automatically saves custom TP/SL values generated by Llama API
- **Position Memory:** Remembers TP/SL values when bot restarts with existing positions
- **Smart Matching:** Validates saved values against current position entry price
- **Automatic Cleanup:** Clears TP/SL data when positions are closed
- **Fallback Protection:** Uses defaults if saved values don't match or are unavailable

### 🛡️ **Enhanced Error Handling & Monitoring**
- **Comprehensive Error Notifications:** Desktop alerts for all critical errors
- **Improved Position Detection:** Better handling of existing positions on startup
- **Enhanced TP/SL Monitoring:** More reliable monitoring with proper cleanup
- **Professional Logging:** Clean, organized error messages and status updates

---

## ✨ Previous Features (v2.0)
- **Candle-Close Signal Logic:** Signals generated only after candle close
- **Race Condition Exit Logic:** Positions closed by TP, SL, or MA crossunder
- **Persistent User Preferences:** Saved settings for reuse
- **Position & P&L Logging:** Real-time position tracking
- **Bracket Orders:** Managed entry, TP, and SL orders
- **Centralized Error Logging:** API errors logged to `api_errors.log`
- **Improved CLI UI:** Clear prompts and startup summaries

---

## 🛠️ How It Works
1. **Startup:** Launch with trading pair (e.g., `BTC/USD`)
2. **Preferences:** Use saved settings or configure new ones
3. **API Checks:** Verify all API connectivity
4. **Market Status:** Confirm market open and asset tradable
5. **Position Check:** Detect existing positions and load saved TP/SL values
6. **Historical Data:** Fetch OHLCV bars for moving average analysis
7. **Live Feed:** Real-time price updates via WebSocket
8. **Signal Engine:** Analyze price vs. adaptive moving averages
9. **Trade Execution:** Execute with dynamic risk controls and notifications
10. **TP/SL Monitoring:** Persistent monitoring with desktop alerts
11. **Professional Logging:** Clean, organized status updates

---

## 🚀 Installation & Setup

### 1. Clone the Repository
```sh
git clone <your-repo-url>
cd Crypto
```

### 2. Install Node.js
[Download Node.js](https://nodejs.org/)

### 3. Install Dependencies
```sh
npm install
```

### 4. Set Up Your `.env` File
Create a `.env` file in the root directory:
```
ALPACA_API_KEY_ID=your_alpaca_key_id
ALPACA_SECRET_KEY=your_alpaca_secret
POLYGON_API_KEY=your_polygon_key
FINNHUB_API_KEY=your_finnhub_key
LLAMA_API_KEY=your_llama_key (optional, for advanced sizing)
NEWS_API_KEY=your_newsapi_key (optional)
```

---

## 🏃 Usage (CLI)
```sh
node cryptoMonitor.js BTC/USD
```
- Replace `BTC/USD` with any supported crypto pair
- Bot prompts for settings or uses saved preferences
- Press Ctrl+C to stop monitoring

---

## 🖥️ Example Output (v3.0)
```
--------------------------------------------------
CRYPTO MONITOR INITIALIZATION
--------------------------------------------------
Symbol: BTC/USD
Timeframe: 1min
--------------------------------------------------

--------------------------------------------------
CURRENT POSITION - BTC/USD
--------------------------------------------------
Quantity: 0.000928 BTC
Entry Price: $107375.20
Market Value: $99.65
📈 P/L: $0.05 (0.05%)
Take Profit: auto
Stop Loss: auto
--------------------------------------------------
Loaded saved TP/SL values: TP 2.5%, SL 1.8%

--------------------------------------------------
TP/SL MONITORING STARTED
--------------------------------------------------
Entry: $107375.20
Take Profit: 2.5%
Stop Loss: 1.8%
--------------------------------------------------

--------------------------------------------------
ALPACA PAPER TRADING ACCOUNT
--------------------------------------------------
Buying Power: $199545.78
Portfolio Value: $99973.08
Cash: $99672.35
--------------------------------------------------

--------------------------------------------------
API CONNECTIVITY STATUS
--------------------------------------------------
Alpaca: ✅ Connected
Polygon: ✅ Connected
Finnhub: ✅ Connected
Llama: ✅ Connected
NewsAPI: ✅ Connected
--------------------------------------------------

--------------------------------------------------
MARKET STATUS
--------------------------------------------------
Crypto market is OPEN (Polygon)
BTC/USD is available for trading (Alpaca)
--------------------------------------------------

--------------------------------------------------
MONITORING ACTIVE - BTC/USD
--------------------------------------------------

🔔 NOTIFICATION: Monitor Started - Successfully started monitoring BTC/USD
```
---

## ⏳ Supported Exchanges, Assets, and Timeframes
- **Exchanges:** Trades via Alpaca (paper trading, US users)
- **Assets:** Any crypto supported by Alpaca (e.g., BTC/USD, ETH/USD, etc.)
- **Timeframes:** 1Min, 5Min, 15Min, 1Hour, 1Day (all use candle-close logic)

---

## ⚡ Trading Logic & Risk Controls
- **Signals:** Generated when price crosses above the best-fit moving average (QuantumMA) on candle close
- **Position Sizing:** Uses Llama API for dynamic sizing if enabled, otherwise fixed size
- **Take-Profit/Stop-Loss:** User-defined, auto-generated, or Llama-optimized with persistence
- **No Overtrading:** Only one position per symbol at a time
- **Race Condition Exit:** Position closed by TP, SL, or MA crossunder (whichever comes first)
- **Desktop Notifications:** Real-time alerts for all important events
- **Error Handling:** Comprehensive error logging and graceful degradation

---

## 🔑 API Rate Limits & Error Handling
- **Alpaca:** 200 requests/minute
- **Polygon:** Market status and data
- **Finnhub:** Live price feed via WebSocket
- **Llama/NewsAPI:** Optional advanced features
- **Error Handling:** Desktop notifications, logging, and graceful degradation

---

## 🧩 Troubleshooting & FAQ
**Q: Desktop notifications not working?**
- Windows: Ensure notifications are enabled in system settings
- Other platforms: Check console for notification messages

**Q: TP/SL values not persisting?**
- Check if `position_tp_sl.json` file exists
- Verify entry price matches saved position

**Q: Bot not detecting existing positions?**
- Ensure API keys are correct and have proper permissions
- Check market status and asset availability

---

## 👩‍💻 Developer Notes & Contribution
- **Core logic:** `core/CryptoMonitor.js`
- **Trading logic:** `core/tradeUtils.js`
- **Moving averages:** `quantamMA.js`
- **API helpers:** `core/apiHelpers.js`
- **CLI entry:** `cryptoMonitor.js`
- **TP/SL persistence:** `position_tp_sl.json`
- **Extending:** Add new analytics, APIs, or trading logic in respective modules

---

## 📄 Legal & Disclaimer
This software is for educational and research purposes only. Cryptocurrency trading involves substantial risk of loss and is not suitable for all investors. Past performance does not guarantee future results. Always conduct your own research and consider consulting with a financial advisor before making investment decisions. The developers are not responsible for any financial losses incurred through the use of this software.
