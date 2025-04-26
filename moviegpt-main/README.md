# 🎥 AI Movie Recommender

![version](https://img.shields.io/badge/version-0.0.1-red?style=for-the-badge) ![ChatGPT](https://img.shields.io/badge/chatGPT-74aa9c?style=for-the-badge&logo=openai&logoColor=white) ![python](https://img.shields.io/badge/python-3.10-blue?style=for-the-badge) ![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi) ![ruff](https://img.shields.io/badge/lint-ruff-gold?style=for-the-badge) ![poetry](https://img.shields.io/badge/packaging-poetry-cyan?style=for-the-badge) ![LlamaIndex](https://img.shields.io/badge/LlamaIndex-%F0%9F%A6%99-black?labelColor=purple&style=for-the-badge)

<p align="center"><img src="https://github.com/ralphug24/movie-recommender/blob/main/img/moviegpt.jpeg?raw=true" style="width: 400px; border-radius: 50% 50% 50% 50%"/></p>

<hr />

## AI Powered Movie Recommendations

This project uses **Generative AI** to provide relevant movie recommendations based on user preferences collected via survey. Key technologies include:

📚 **Open Source Data**: We use movie data (e.g., summaries, genres, cast) from [Wikipedia](https://www.wikipedia.org/), transformed into embeddings for storage in a **Vector Database**.

🐕 **Retrieval Augmented Generation (RAG)**: A vector database and semantic search enable relevant contextual retrieval to reduce hallucination risk in LLM responses.

🤖 **ChatGPT**: Generates fluent and engaging recommendations using retrieved movie metadata.

## Architecture

<img src="https://github.com/ralphug24/movie-recommender/blob/main/img/arch.png?raw=true" />

## Getting Started
### With Docker (Recommended)

Set your OpenAI API Token:
```bash
export OPENAI_API_TOKEN=#YOUR_TOKEN
```

Build the Docker image:
```bash
make docker
```

Run the container:
```bash
make run
```

```bash
INFO:root:Starting web server...
INFO:     Started server process [29]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     Uvicorn running on http://0.0.0.0:8000 (Press CTRL+C to quit)
```

Access the API docs: http://localhost:8000/docs

### Without Docker (Pure Python)

Ensure you are using **Python 3.10.12** (we recommend `pyenv`):
```bash
pyenv install 3.10.12
pyenv shell 3.10.12
```

Install `poetry`:
```bash
pip install poetry
```

Activate environment and install dependencies:
```bash
cd src && poetry shell && poetry install
```

Run the recommender:
```bash
poetry run moviegpt
```

### Step-by-step Commands
```bash
poetry run moviegpt data && \
poetry run moviegpt index && \
poetry run moviegpt web
```

Access the API: http://localhost:8000/docs

### CLI Mode

Run the CLI:
```bash
moviegpt
```

You should see:
```bash
Usage: moviegpt [OPTIONS] COMMAND [ARGS]...

Options:
  --help  Show this message and exit.

Commands:
  data   Downloads WikiData for movies.
  index  Creates a VectorDB Index based on Movie Metadata in JSON.
  query  Queries the VectorDB using Semantic Similarity and outputs movie...
  web    Runs our RAG App and exposes it through FastAPI.
```

### Sample API

After setting up the backend, visit the FastAPI UI:

<img src="https://github.com/ralphug24/movie-recommender/blob/main/img/fastapi.png?raw=true" />

## Development

- Run unit tests with `pytest` or `tox`
- Format with `tox -e fix`
- Lint with `tox -e lint`

## Documentation

Further documentation is under development. Please refer to the repo: [https://github.com/ralphug24/movie-recommender](https://github.com/ralphug24/movie-recommender)

