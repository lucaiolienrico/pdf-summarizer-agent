# 🚀 Setup e Configurazione

## Prerequisiti
- Python 3.11+
- pip (gestore pacchetti Python)
- account OpenAI o Anthropic per API
- account GitHub con token personale

## Installazione Locale

### 1. Clonare il repository
```bash
git clone https://github.com/lucaiolienrico/pdf-summarizer-agent.git
cd pdf-summarizer-agent
```

### 2. Creare un ambiente virtuale
```bash
python -m venv venv
source venv/bin/activate  # su Windows: venv\Scripts\activate
```

### 3. Installare le dipendenze
```bash
pip install -r requirements.txt
```

### 4. Configurare le variabili di ambiente
```bash
cp .env.example .env
```
Edita `.env` con i tuoi dati:
- `OPENAI_API_KEY`: Dalla dashboard OpenAI
- `GITHUB_TOKEN`: Dai settings di GitHub

## Setup GitHub Actions

### 1. Aggiungere Secrets
Vai a: Repository → Settings → Secrets and variables → Actions

Aggiungi:
- `OPENAI_API_KEY`
- `ANTHROPIC_API_KEY` (opzionale)
- `GITHUB_TOKEN` (auto-generato)

### 2. Attivare il Workflow
I workflow vengono attivati automaticamente quando viene pushato un PDF.

## Come Usarlo

### Upload PDF
1. Crea una cartella `uploads/` nel repository
2. Carica un PDF
3. Fai commit e push
4. GitHub Actions elaborerà automaticamente il PDF
5. Il riassunto sarà salvato in `summaries/`

### Trigger Manuale
Vai a: Repository → Actions → PDF Summary Agent → Run workflow

## Troubleshooting

**Errore API Key non trovata:**
- Verifica che le secrets siano correttamente configurate
- Verifica che il file .env esista (localmente)

**PDF non processato:**
- Controlla i log in GitHub Actions
- Verifica le dimensioni (max 50MB default)

**Riassunto troppo breve/lungo:**
- Modifica `summary_max_length` in config.json
