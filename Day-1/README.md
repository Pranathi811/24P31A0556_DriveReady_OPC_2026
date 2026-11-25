This is the day-1 task.
# Day 1 – AI Trading Research Assistant

## 1. Task Description

The objective of this task is to develop an AI-powered Trading Research Assistant using Python, LangChain, and Groq LLM.

The assistant analyzes user-provided financial market scenarios and generates structured trading research insights. It evaluates market trends, technical indicators, entry zones, stop-loss levels, target prices, and risk management.

The system is designed for educational analysis and hypothetical paper trading.

## 2. Technologies Used

- **Python:** Main programming language.
- **Google Colab:** Development and execution environment.
- **LangChain:** Connects the application with the language model.
- **Groq LLM:** Processes user queries and generates trading analysis.
- **Google Colab Secrets:** Securely manages the Groq API key.

## 3. Code Implementation

### Step 1: Install Required Library

```python
!pip install langchain_groq
```

Installs the LangChain Groq integration required to connect Python with the Groq language model.

### Step 2: Import Libraries

```python
from langchain_groq import ChatGroq
import os
from google.colab import userdata
```

Imports the required modules for model integration, environment configuration, and secure API key retrieval.

### Step 3: Configure API Key and Initialize LLM

```python
os.environ["GROQ_API_KEY"] = userdata.get("GROQ_API_KEY")

llm = ChatGroq(
    model="openai/gpt-oss-120b",
    temperature=0
)
```

- Retrieves the Groq API key from Google Colab Secrets.
- Initializes the language model.
- Sets temperature to 0 for more consistent responses.

### Step 4: Define System Prompt

The system prompt defines the role and responsibilities of the AI Trading Research Assistant.

It instructs the model to analyze:

1. Market Trend – Bullish, bearish, or sideways.
2. Technical Analysis – RSI, MACD, moving averages, and support/resistance.
3. Entry Price – Hypothetical entry zone.
4. Stop Loss – Potential risk-limiting level.
5. Target Price – Potential target levels.
6. Risk-Reward Ratio – Comparison of potential risk and reward.
7. Trade Decision – BUY, SELL, or WAIT.
8. Reasoning – Explanation behind the decision.
9. Risk Management – Maximum 1% capital risk per hypothetical trade.

It also prevents the model from inventing live market prices or guaranteeing trading returns.

### Step 5: Create the Ask Function

```python
def ask(question):
    return llm.invoke([
        ("system", SYSTEM),
        ("human", question)
    ]).content
```

This function accepts a user's question and sends it to the language model along with the system instructions.

The model processes the request and returns the generated analysis.

### Step 6: Test the Assistant

A hypothetical NIFTY 50 intraday trading scenario is provided with:

- Capital: ₹1,00,000
- Maximum Risk: 1%
- Trading Timeframe: 5-minute chart

The assistant is asked to provide market trend, entry zone, stop loss, target price, position sizing, risk-reward ratio, and final trading decision.

## 4. Execution Workflow

1. Install the required Python package.
2. Import the necessary libraries.
3. Configure the Groq API key.
4. Initialize the Groq language model.
5. Define the system prompt and trading analysis framework.
6. Create the `ask()` function.
7. Provide a hypothetical market scenario.
8. Generate and display the AI response.

## 5. Expected Output

The assistant generates a structured response containing:

- Market Trend
- Technical Analysis
- Entry Zone
- Stop Loss
- Target Price
- Position Sizing
- Risk-Reward Ratio
- Final Trading Decision
- Reasoning and Risk Management

Actual prices are not generated when supporting market data is unavailable.

## 6. Conclusion

The AI Trading Research Assistant demonstrates the integration of Python, LangChain, and Groq LLM for financial research and educational trading analysis.

The task provides practical experience in API integration, prompt engineering, language model initialization, and processing user queries using an LLM.

**Note:** This project does not connect to a live market data feed. Its output depends on the information supplied in the user query and the language model's response. It is intended for educational purposes, not actual investment decisions.
