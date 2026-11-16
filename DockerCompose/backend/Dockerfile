#BACKEND
# Partiamo dall'immagine ufficiale di Python
FROM python

# Creiamo e ci spostiamo nella cartella principale di lavoro /app dentro il container
WORKDIR /app

# Scarichiamo direttamente da GitHub l'intero repository del progetto
RUN git clone https://github.com/mmenapace/SomeBankingApp

# Entriamo nella sottocartella del backend dove si trovano requirements.txt e main.py
WORKDIR /app/SomeBankingApp/backend

# Installiamo le dipendenze elencate nel file requirements.txt del repository
RUN pip install -r requirements.txt

# Installiamo esplicitamente FastAPI (mancante nel requirements.txt originale, causava il crash)
RUN pip install fastapi

# Avviamo il server web Uvicorn con l'app FastAPI; '--host 0.0.0.0' serve per accettare richieste dagli altri container (es. il reverse proxy)
ENTRYPOINT [ "python", "-m", "uvicorn", "main:app", "--host", "0.0.0.0" ]