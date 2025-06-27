Guide: Real-time Stock Researcher Dify Plugin
This guide provides instructions on how to set up and effectively use the Real-time Stock Researcher Dify Plugin within your Dify applications (Chatflows, Workflows, or Agents).

1. What is the Real-time Stock Researcher Plugin?
The Real-time Stock Researcher Dify Plugin is a tool designed to instantly retrieve current stock prices and basic market data for specified company ticker symbols. It integrates directly with external Financial APIs, allowing your Dify applications to query live market data using natural language commands or structured inputs.

Key Features:

Search for real-time stock prices by ticker symbol (e.g., AAPL, MSFT).

Retrieve the most recent price and last updated timestamp.

Seamless integration into Dify workflows and conversational AI for financial inquiries.

2. Setup and Configuration
Before using the plugin, you need to configure your Financial API credentials within Dify.

2.1. Obtain Financial API Credentials
Financial API Provider Account: You will need an account with a financial data API provider (e.g., Alpha Vantage, Finnhub, Twelve Data). Many offer free tiers for limited usage.

API Key: Obtain your API Key from your chosen financial API provider's developer dashboard.

API Endpoint (if applicable): While some APIs use a single base URL, others might have specific endpoints for different data types. Identify the base URL for the real-time stock price API that you intend to use.

2.2. Configure Credentials in Dify
Navigate to your Dify application's "Plugins" or "Tools" section.

Locate the "Real-time Stock Researcher" plugin.

Go to its "Credentials" or "Settings" area.

Enter your financial_api_key in the designated "Financial API Key" field.

(Optional, but often required for custom setups) Enter your financial_api_endpoint in the "Financial API Base URL" field if your chosen API requires a specific base URL for this service.

Save the configurations.

3. Using the Real-time Stock Researcher Tool
Once configured, you can invoke the stock_researcher tool in your Dify applications.

3.1. Tool Parameters
The stock_researcher tool accepts the following parameter:

symbol (string, required):

Description: The ticker symbol of the stock you wish to research (e.g., AAPL for Apple, MSFT for Microsoft, GOOG for Google).

Example: "TSLA", "AMZN", "NVDA"

3.2. Invoking the Tool
In a Chatflow/Agent:
Your Dify Agent, when prompted by a user, can identify the intent to search for stock prices and call the tool.

User Input Example: "What is the current stock price of Apple?"

Agent Action: The LLM would recognize "Apple" and infer "AAPL" as the symbol, then trigger the stock_researcher tool.

In a Workflow:
You can add a "Tool" node in your workflow, select "Real-time Stock Researcher," and map an input variable (e.g., from a "Text Input" node) to the symbol parameter.

4. Understanding the Output
Upon successful execution, the stock_researcher tool returns a structured JSON object containing the stock's information. This JSON can then be processed by subsequent LLM steps or displayed directly to the user.

Example Output (JSON):

{
  "stock_info": {
    "symbol": "AAPL",
    "current_price": 178.55,
    "last_updated_utc": "2025-06-27 09:30:00 UTC"
  }
}

The Dify interface will typically display this information in a readable format, often as a card or directly in the chat, e.g., "The current price of AAPL is $178.55 as of 2025-06-27 09:30:00 UTC."

5. Use Cases
Financial News & Updates: Provide real-time stock prices in a chatbot for market enthusiasts.

Portfolio Tracking: Integrate into applications that help users monitor their investments.

Market Analysis Tools: Automate data retrieval for financial analysis and reporting.

Educational Content: Help users learn about stock market data in an interactive way.

6. Important Disclaimer: NOT FINANCIAL ADVICE
THIS PLUGIN IS PROVIDED FOR INFORMATIONAL PURPOSES ONLY AND DOES NOT CONSTITUTE FINANCIAL ADVICE OR A RECOMMENDATION TO BUY, SELL, OR HOLD ANY SECURITIES. IT IS NOT INTENDED TO BE A SUBSTITUTE FOR PROFESSIONAL FINANCIAL CONSULTATION. ALWAYS CONSULT WITH A QUALIFIED FINANCIAL ADVISOR OR PROFESSIONAL FOR ADVICE REGARDING YOUR SPECIFIC FINANCIAL SITUATION OR INVESTMENT DECISIONS. NEVER DISREGARD PROFESSIONAL FINANCIAL ADVICE OR DELAY IN SEEKING IT BECAUSE OF INFORMATION OBTAINED THROUGH THIS PLUGIN.

7. Troubleshooting
"Financial API key is not configured" / "Financial API endpoint is not configured":

Solution: Go to the plugin's credentials in Dify and ensure both the API key and the base URL (if required) are correctly entered and saved.

"Error from Financial API: 4xx/5xx":

Solution: This indicates an issue with the API call itself.

Check your Financial API key for correctness and ensure it has the necessary permissions.

Verify the API endpoint URL is exact and accessible.

Consult your financial API's documentation for specific error codes (e.g., invalid symbol, rate limits).

The financial API service might be temporarily unavailable.

"Stock symbol XYZ not found...":

Solution: The provided ticker symbol might be incorrect, misspelled, or not supported by the integrated API. Double-check the symbol.

"Error parsing Financial API response...":

Solution: This suggests the Financial API's response format might have changed, or it returned an unexpected structure. You may need to review the plugin's Python code to adapt to the new response format based on the API's latest documentation.

Network Error:

Solution: Check your internet connection and ensure Dify's environment has outgoing network access to the financial API endpoint.