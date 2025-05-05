# 📚 TrendStory - AI-Powered Story Generation

**TrendStory** is an AI-based story generation app that fetches real-time trends (from Google News and YouTube), and generates stories based on selected topics using the `Phi-2` language model. It supports both REST and gRPC APIs, a Gradio UI, and is fully containerized using Docker.

---

## 🔧 Features

- 📈 Fetch trends from GNews and YouTube APIs
- ✍️ Generate stories in 3 tones: `tragic`, `hopeful`, `poetic`
- 🔊 Optional text-to-speech playback
- ⚡ REST API with FastAPI + gRPC endpoint
- 🐳 Docker support
- 📬 Postman collection for API testing
- 🧪 Python test script for validating and benchmarking

---

## 🚀 Getting Started

### ✅ Requirements

- Python 3.10+
- `pip install -r requirements.txt`
- Docker (optional but recommended)

---

## 🛠️ Setup Instructions

### 🔹 Run REST API Server

```bash
uvicorn main:app --reload
```

### 🔹 Run Gradio Interface (Jupyter or script)

```bash
python gradio_ui.py
```

### 🔹 Run in Docker

```bash
docker build -t trendstory .
docker run -p 8000:8000 trendstory
```

---

## 🔌 REST API Endpoints

### ✅ `GET /trends`

Returns a list of combined trending topics.

**Response:**
```json
{
  "trends": ["Floods in Lahore", "Elections 2025", ...]
}
```

---

### ✅ `POST /generate_story`

**Payload:**
```json
{
  "topic": "Floods in Lahore",
  "tone": "tragic"
}
```

**Response:**
```json
{
  "story": "Once upon a time, in the flood-stricken streets of Lahore..."
}
```

---

## 🔗 gRPC API

### 1. Compile `.proto`
```bash
python -m grpc_tools.protoc -I. --python_out=. --grpc_python_out=. trendstory.proto
```

### 2. Run Server
```bash
python server.py
```

### 3. Run Client
```bash
python client.py
```

---

## 📮 Postman Collection

Use `trendstory_postman_collection.json` or `generate_story_only_postman_collection.json` to test endpoints.

- Import into Postman
- Set `base_url = http://127.0.0.1:8000`
- Includes tests for:
  - Valid request
  - Missing topic
  - Invalid tone

---

## 🧪 Python Test Script

Use `test_api.py` to test all API cases and measure performance:

```bash
python test_api.py
```

---

## 🤖 Model Info

- Uses [microsoft/phi-2](https://huggingface.co/microsoft/phi-2)
- Loaded using Hugging Face Transformers
- Fallback: TinyLlama (for low-memory machines)

---

## ⚠️ Known Limitations

- Phi-2 is large (~7GB); may fail on systems with low RAM or no GPU
- No fine-tuning yet for Roman Urdu prompts
- gRPC client/server must be manually run separately
- Requires Internet to fetch trends via APIs

---

## 📁 Project Structure

```bash
📦 phi2_fastapi_server/
│   ├── main.py               # FastAPI backend
│   ├── gradio_ui.py          # Optional UI
│   ├── Dockerfile
│   ├── test_api.py
│   ├── trendstory.proto
│   ├── server.py             # gRPC server
│   ├── client.py             # gRPC client
│   ├── trendstory_postman_collection.json
│   └── README.md
```

---

## 🙌 Author

Hamza — 2025 NLP Project @ University
