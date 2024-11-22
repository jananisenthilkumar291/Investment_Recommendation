## Investment_Recommendation
### pipeline
- Sentiment Analysis
- Time Series Forecasting
- Recommendation system

### Sentiment Analysis Pipeline
- Data Preprocessing
- Dual Text Summarization
- Dual Sentiment Analysis

#### Text_Processing

- Data Collection
  - Articles related to Apple products and services were fetched from the New York Times Archive API.
- Data Loading, cleaning
- Text Preprocessing
- Sentiment analysis and Summarization
  - Text summarization was performed using a Transformer-based model (facebook/bart-large-cnn) via the Hugging Face transformers library.
  - Sentiment analysis was performed using the VADER (Valence Aware Dictionary and sEntiment Reasoner) tool from NLTK.
- Data Augmentation
  - Sentiment scores (e.g., negative, neutral, positive, compound) were extracted from the sentiment analysis.

#### LLM

- API Integration:
  - The notebook interacts with the local LLaMA model API hosted at http://127.0.0.1:11434/api/generate.
  - Functions are defined to send text to the API for summarization and sentiment analysis.
- Summarization Functionality
  - The summarize_text function formats the input text with a prompt asking the model to summarize it.
  - A stream response is processed to retrieve the summarized text.
- Sentiment Analysis Functionality:
  - The analyze_sentiment function sends a prompt requesting sentiment scores (negative, neutral, positive, compound) for the input text.
  - Regular expressions are used to extract the sentiment scores from the API response.
- Data Preprocessing:
  - A dataset of articles is loaded (Apple_News_Articles_2013_1_2024_10.csv).
  - Selected columns (abstract, snippet, etc.) are normalized and concatenated to form a unified text_in_article field.
- Pipeline Execution:
  - Summarization is applied to each article's text using the summarize_text function and a parallel execution approach (ThreadPoolExecutor).
  - Sentiment analysis is applied to the summaries, and the results are saved in the dataset.
- Data Output:
  - The final dataset, including original text, summaries, and sentiment scores, is saved to a CSV file (articles_sentiment_llm.csv).


#### Stock Forecast
- Data is pulled from yfinance
- Data Preprocessing
- Seasonal, trend Decomposition
- Time Series forcasting is done using Prophet, Naive, snaive, STLM
- Forecast for next month (daily/monthly) using prophet

#### EDA
- Current month News articles pulled from New york times
- Till date Stock Data pulled from yfinance
- Data processed - fetched sentiment of the current month
- Time temporal comparison between nltk/transformers vs LLM
- Forecasted for the current month(Daily/monthly)
- Recommendation,
  - Based on a past 10 day average - 15%
  - Based on momentum - 5%
  - Based on Market downward/upward trend - 20%
  - Based on Sentiment of the Month - 50%
  - Based on targetted profit - 10%
 

  

  
