# Greenwashing Detector

## Description
This project is a backend service designed to detect greenwashing in text and web content. It utilizes machine learning and keyword analysis to evaluate environmental claims. The system identifies valid environmental claims, flags likely greenwashing based on buzzwords, and separates non-environmental statements. Additionally, it offers fact-checking capabilities by cross-referencing claims with search engine results to verify their accuracy.

## Technologies and Models
The application is built using the following technologies and models:

*   **Python**: The primary programming language used for the backend logic.
*   **Flask**: A lightweight web framework used to create the API endpoints.
*   **Transformers (Hugging Face)**: Used for implementing the text classification pipeline.
*   **ClimateBERT**: The `climatebert/environmental-claims` model is employed to classify text as environmental claims or otherwise.
*   **BeautifulSoup4**: A library used for scraping and parsing HTML to extract text from URLs for analysis.
*   **SerpAPI**: An API used to perform Google searches for fact-checking specific claims.

## How to Run

### Prerequisites
*   Python 3.8 or higher installed on your system.
*   A valid API key for SerpAPI (required for the fact-checking feature).

### Installation
1.  Navigate to the project directory.
2.  Install the required Python dependencies:
    ```bash
    pip install -r requirements.txt
    ```

### Configuration
The application requires a SerpAPI key for the verification features. You should update the `SERPAPI_KEY` variable in `app.py` with your own valid key or configure it as an environment variable for better security.

### Execution
1.  Start the Flask server by running the application file:
    ```bash
    python app.py
    ```
2.  The application will start effectively and listen for requests, typically accessible at `http://127.0.0.1:5000`.

### API Endpoints
The service exposes the following endpoints:

*   **POST /analyze-text**: Accepts a JSON payload with a `text` field (the raw text to analyze). Optionally accepts a `claim` field for fact-checking. Returns the analysis results and a reference to a generated report file.
*   **POST /analyze**: Accepts a JSON payload with a `url` field (the webpage to scrape and analyze). Optionally accepts a `claim` field.
*   **GET /download/<filename>**: Allows downloading of the generated report file referenced in the analysis response.
