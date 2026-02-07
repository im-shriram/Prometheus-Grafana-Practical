# 🚀 Prometheus Test Target

[![Python Version](https://img.shields.io/badge/python-3.13+-blue.svg)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.54.0-ff4b4b.svg)](https://streamlit.io/)
[![Prometheus](https://img.shields.io/badge/Prometheus-0.24.1-e6522c.svg)](https://prometheus.io/)

A demonstration of an MLOps monitoring workflow. This project features a **Sentiment Analysis App** built with **Streamlit** that exposes real-time performance and usage metrics to **Prometheus**.

---

## 🌟 Key Features

- **Real-time Monitoring**: Exposes custom metrics (request counts, latency, token usage) via `prometheus-client`.
- **Interactive UI**: A sleek Streamlit interface for sentiment analysis simulation.
- **Metric Tracking**:
  - `prediction_requests_total`: Tracks the volume of incoming requests.
  - `prediction_request_duration_seconds`: Measures inference latency using Prometheus Summaries.
  - `prediction_tokens_total`: Monitors the scale of processed text data.
- **Auto-Metrics Exposure**: Metrics server runs concurrently on port `8000`.

---

## 🛠️ Tech Stack

- **Frontend**: [Streamlit](https://streamlit.io/)
- **Monitoring**: [Prometheus Client](https://github.com/prometheus/client_python)
- **Environment**: Python 3.13+
- **Package Manager**: `uv` or `pip`

---

## 📊 Metrics Overview

The application exposes the following metrics at `http://localhost:8000/metrics`:

| Metric Name | Type | Description |
| :--- | :--- | :--- |
| `prediction_requests_total` | Counter | Total number of sentiment analysis requests. |
| `prediction_request_duration_seconds` | Summary | Latency distribution of the prediction process. |
| `prediction_tokens_total` | Counter | Total count of words/tokens processed. |

---

## ⚙️ Installation

### 1. Clone the Repository
```bash
git clone <repository-url>
cd Prometheus
```

### 2. Set Up Environment
Using `uv` (recommended):
```bash
uv sync
```
Or using `pip`:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

---

## 🚀 Usage

### Run the Application
Start the Streamlit app:
```bash
streamlit run app.py
```

1. Open your browser and navigate to the URL provided by Streamlit (usually `http://localhost:8501`).
2. Enter some text and click **Analyze Sentiment**.
3. View the exposed metrics at `http://localhost:8000/metrics`.

---

## 📉 Monitoring with Prometheus

To scrape metrics from this application, add the following target to your `prometheus.yml`:

```yaml
scrape_configs:
  - job_name: 'prometheus-test-target'
    static_configs:
      - targets: ['localhost:8000']
```

---

## 📁 Project Structure

```text
Prometheus/
├── app.py              # Main Streamlit application
├── test_metrics.py     # Metrics definition & mock prediction logic
├── requirements.txt    # Project dependencies
├── pyproject.toml      # Project configuration
└── README.md           # Documentation (You are here!)
```

---

## 🤝 Contributing

Contributions are welcome! If you have suggestions for new metrics or UI improvements, feel free to open an issue or pull request.

---

*Built with ❤️ for the MLOps Community.*
