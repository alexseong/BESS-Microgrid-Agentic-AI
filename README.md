# BESS Microgrid Agentic AI

Hybrid RL (PPO with Ray/RLlib) + Pyomo MILP + Llama3 (vLLM) + FastAPI + React + Postgres + W&B.

## Quick Start

### 1. Start Postgres:

```bash
docker-compose up -d db
Backend:
```

### 2. Backend:

cd backend
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp ../.env.example .env   # edit as needed
./run_backend.sh
vLLM (Llama3):

### 3. vLLM(Llama3):

python -m vllm.entrypoints.openai.api_server \
  --model /path/to/llama3-8b-instruct \
  --chat-template meta-llama-3 \
  --served-model-name llama3-8b-instruct \
  --host 0.0.0.0 --port 8001

### 4. Frontend:

cd frontend
npm install
npm run dev