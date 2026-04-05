# Nifty & Sensex Short Strangle Algo

This Python script implements an automated short strangle options trading strategy for Nifty and Sensex indices using the Zerodha Kite Connect API.

## Strategy Overview

A **short strangle** involves selling out-of-the-money (OTM) call and put options, while buying further OTM options as hedges to limit risk.

### Key Features
- **Trigger Days**: 
  - Nifty: Monday (1 day before Tuesday expiry)
  - Sensex: Wednesday (1 day before Thursday expiry)
- **Entry Time**: After 9:45 AM
- **Option Selection**:
  - Sells PE and CE in specified premium ranges
  - Buys hedge PE and CE in lower premium ranges
- **Exit Rules**:
  - Stop Loss: 100% (exit if sold premium doubles)
  - Target: 50% (exit if 50% of premium is captured as profit)
- **Alerts**: Console output (can be extended to email/SMS)

### Premium Ranges
- **Nifty**:
  - Sell PE: ₹30–40
  - Buy PE Hedge: ₹10–15
  - Sell CE: ₹20–30
  - Buy CE Hedge: ₹5–10
- **Sensex** (same logic, adjusted for index)

## Requirements
- Python 3.x
- Zerodha Kite account with API access
- Internet connection for API calls

## Dependencies
Install required packages:
```
pip install kiteconnect pandas schedule
```

## Setup
1. **Get API Credentials**:
   - Log in to [kite.trade](https://kite.trade)
   - Go to Developers → Kite Connect → Create App
   - Note your `API_KEY` and `API_SECRET`

2. **Configure the Script**:
   - Edit the user settings in `nifty_sensex_algo.py`:
     - Set `API_KEY` and `API_SECRET`
     - Adjust lot sizes (`NIFTY_LOTS`, `SENSEX_LOTS`)
     - Modify premium ranges if needed
     - Set entry time and exit percentages

3. **Run the Script**:
   - On trigger days, run the script after 9:45 AM
   - Follow the login prompts to authenticate with Zerodha

## Usage
1. Execute the script on the appropriate trigger day.
2. The script will automatically:
   - Log in to Kite
   - Select suitable options based on premium ranges
   - Place orders for short strangle with hedges
   - Monitor positions and exit based on SL/target

## Disclaimer
This is for educational purposes only. Options trading involves significant risk and can result in total loss of capital. Always backtest strategies and use at your own risk. The authors are not responsible for any financial losses.

## License
[MIT License](https://opensource.org/licenses/MIT)</content>
<parameter name="filePath">c:\Users\Mallepogula Ganesh\Downloads\README.md