# IDFC FIRST Bank — AI Underwriting Copilot v2.0

## Start in 3 steps

```bash
pip install -r requirements.txt
cp .env.example .env   # then edit .env with your API keys
uvicorn app.main:app --reload --port 8000
```

## Seed Weaviate (once)
```bash
curl -X POST http://localhost:8000/policy/seed
```

## Open frontend
Open `frontend/index.html` with VS Code Live Server, or:
```bash
python -m http.server 3000 --directory frontend
```
Visit http://localhost:3000

## API Docs
http://localhost:8000/api/docs

## Health Check
http://localhost:8000/health


## Commands to run

```
 python -c "from app.core import settings; print('O_O', settings.APP_NAME)"
```

```
 python -c "from app.services.embedding_service import embed_texts; print('✅ Vector length:', len(embed_texts('test')))"
```

```
 python -c "from app.services.embedding_service import embed_text; print('✅ Vector length:', len(embed_text('test')))"
```

```
 python -c "from app.services.embedding_service import embed_texts; print('✅ Vector length:', len(embed_texts(['test','the','dog','mumbai'])))"
```

```
 python -c "from app.services.embedding_service import embed_texts; print('✅ Vector length:', embed_texts(['test','the','dog','mumbai']))"
```

```
python -c "from app.services.policy_rag_service import seed; print('✅ Seeded:', seed())"
```
```
python -c "from app.services.policy_rag_service import retrieve; r = retrieve('home loan'); print('✅ retrieve:', len(r), 'results'); print(r[0]['policy_id'] if r else 'No results')"
```

```
python -c "from app.services.policy_rag_service import retrieve; r = retrieve('home loan', loan_type='home_loan', cibil_score=720); print('✅ filtered retrieve:', len(r), 'results'); print(r[0] if r else 'No results')"
```

```
python -c "from app.services.policy_rag_service import check_faithfulness; f = check_faithfulness('Per policy RBI-HL-001, CIBIL 700+ required', 'Home loan applicants with CIBIL 700+ eligible'); print('✅ faithfulness:', f['faithfulness_score'], f['verdict'])"
```