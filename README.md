# Binance MCP Server with OpenAI Integration

![alt text](https://www.daulathussain.com/wp-content/uploads/2025/10/Build-a-Binance-MCP-Server-with-OpenAI-Integration-Node.js-JavaScript-Binance-API-OpenAI-Project.jpg)

- [Final Source Code]()

#### Setup Video

- [Final Code Setup video]()

A Model Context Protocol (MCP) server that connects OpenAI with Binance's cryptocurrency exchange API. Ask questions about crypto prices, trading volumes, order books, and market data directly through your terminal using natural language powered by OpenAI.

## Features

- **Real-time Crypto Data**: Get live cryptocurrency prices and market data from Binance
- **Natural Language Interface**: Ask questions in plain English via terminal
- **OpenAI Integration**: Powered by GPT-4 for intelligent responses
- **Comprehensive Tools**: 8 different tools for various market data queries
- **Easy to Use**: Simple terminal-based chat interface

## Available Tools

1. **get_crypto_price** - Get current price for any trading pair
2. **get_top_cryptocurrencies** - View top cryptocurrencies by trading volume
3. **get_price_change** - Get 24-hour price change statistics
4. **get_orderbook** - View current order book (bids/asks)
5. **get_recent_trades** - See latest executed trades
6. **get_klines** - Get candlestick/OHLCV data for technical analysis
7. **search_symbols** - Search for available trading symbols
8. **get_exchange_info** - Get detailed exchange information

## Prerequisites

- Node.js 18 or higher
- OpenAI API key ([Get one here](https://platform.openai.com/api-keys))
- Internet connection for Binance API access

## Installation

### Step 1: Install Dependencies

```bash
npm install
```

### Step 2: Configure OpenAI API Key

Create a `.env` file in the root directory:

```bash
cp .env.example .env
```

Edit the `.env` file and add your OpenAI API key:

```
OPENAI_API_KEY=sk-your-actual-openai-api-key-here
```

## Usage

### Start the Interactive Client

```bash
npm run client
```

This will:

1. Start the MCP server in the background
2. Connect to OpenAI
3. Launch an interactive terminal chat interface

### Example Questions

Once the client is running, you can ask questions like:

```
What is the current price of Bitcoin?
Show me the top 5 cryptocurrencies by volume
What is the 24h price change for Ethereum?
Get recent trades for BNBUSDT
Show me the order book for BTCUSDT
What are the klines for ETHUSDT on 1 hour interval?
Search for all BTC trading pairs
```

### Exiting

Type `exit` or `quit` to close the client, or press `Ctrl+C`.

## Architecture

```
┌─────────────┐      ┌─────────────┐      ┌──────────────┐
│   Terminal  │ ───> │   OpenAI    │ ───> │  MCP Server  │
│    (You)    │      │   (GPT-4)   │      │  (Binance)   │
└─────────────┘      └─────────────┘      └──────────────┘
                            │                      │
                            │                      │
                            └──── Tool Calls ──────┘
```

1. **You** ask a question in natural language
2. **OpenAI (GPT-4)** understands your intent and decides which tool to use
3. **MCP Server** fetches live data from Binance API
4. **OpenAI** formats and explains the data in a user-friendly way
5. **Terminal** displays the response

## Project Structure

```
binance-mcp-server/
├── src/
│   ├── index.js          # MCP Server implementation
│   └── client.js         # OpenAI client with terminal interface
├── package.json          # Project dependencies
├── .env.example          # Example environment variables
├── .env                  # Your API keys (create this)
├── .gitignore           # Git ignore rules
└── README.md            # This file
```

## Development

### Run Server Only

```bash
npm start
```

### Run with Auto-Reload

```bash
npm run dev
```

### Test Server with MCP Inspector

You can test the MCP server using the official MCP Inspector:

```bash
npx @modelcontextprotocol/inspector node src/index.js
```

## Binance API Symbols Format

When asking about specific cryptocurrencies, use these formats:

- Bitcoin in USDT: `BTCUSDT`
- Ethereum in USDT: `ETHUSDT`
- Binance Coin: `BNBUSDT`
- Cardano: `ADAUSDT`
- Solana: `SOLUSDT`

The OpenAI assistant will automatically format symbols correctly in most cases.

## Available Kline Intervals

For candlestick/OHLCV data, you can use these intervals:

- Minutes: `1m`, `5m`, `15m`, `30m`
- Hours: `1h`, `4h`, `12h`
- Days: `1d`, `3d`
- Weeks: `1w`
- Months: `1M`

## API Rate Limits

Binance has rate limits on their public API:

- 1200 requests per minute
- 6100 requests per 5 minutes

The server handles these automatically, but avoid making too many requests in quick succession.

## Troubleshooting

### Error: "OPENAI_API_KEY not found"

Make sure you've created a `.env` file with your OpenAI API key:

```bash
cp .env.example .env
# Then edit .env and add your key
```

### Error: "Invalid symbol"

Binance symbols must be in the correct format (e.g., `BTCUSDT`). Try:

- Using the `search_symbols` tool to find the correct symbol
- Making sure there are no spaces in the symbol
- Using uppercase letters

### Connection Issues

If you can't connect to Binance:

- Check your internet connection
- Verify Binance API is accessible in your region
- Try accessing https://api.binance.com/api/v3/ping in your browser

### OpenAI API Issues

If OpenAI requests are failing:

- Verify your API key is valid
- Check you have credits available in your OpenAI account
- Ensure you're not hitting rate limits

## Cost Considerations

This application uses:

- **Binance API**: Free, no API key required
- **OpenAI API**: Paid service (typically ~$0.01-0.03 per conversation)

Monitor your OpenAI usage at: https://platform.openai.com/usage

## Security Notes

- Never commit your `.env` file to version control
- Keep your OpenAI API key secure
- The `.gitignore` file prevents accidental commits of sensitive data
- No Binance API key needed (using public endpoints only)

## Contributing

Contributions are welcome! Feel free to:

- Report bugs
- Suggest new features
- Submit pull requests
- Improve documentation

## License

MIT License - feel free to use this project for personal or commercial purposes.

## Support

For issues or questions:

- Check the troubleshooting section above
- Review Binance API documentation: https://binance-docs.github.io/apidocs/
- Review MCP documentation: https://modelcontextprotocol.io/
- Check OpenAI API status: https://status.openai.com/

## Disclaimer

This project is for educational and informational purposes only. It is not financial advice. Always do your own research before making investment decisions.

The project is not affiliated with, endorsed by, or sponsored by Binance or OpenAI.
