#FRONTEND
# --- STAGE 1: BUILD (serve solo a compilare il codice Angular, poi verrà scartato) ---

# costruiamo l'app
# (partiamo da Node.js perché ci servono npm e Angular CLI per compilare il progetto, e chiamiamo questo stage "build")
FROM node AS build 

# (creiamo e impostiamo /app come cartella di partenza)
WORKDIR /app

# (al posto di COPY . ., scarichiamo l'intero repository direttamente da GitHub dentro /app/SomeBankingApp)
RUN git clone https://github.com/mmenapace/SomeBankingApp

# (entriamo nella sottocartella del frontend della repo clonata, dove si trovano package.json e angular.json)
WORKDIR /app/SomeBankingApp/frontend

# (installa tutte le dipendenze JavaScript elencate in package.json dentro node_modules)
RUN npm i

# (compila l'applicazione Angular trasformando il codice TypeScript/HTML/CSS nei file statici finali dentro la cartella dist/)
RUN ./node_modules/.bin/ng build 


# --- STAGE 2: RUNTIME (l'immagine finale leggera che andrà in esecuzione) ---

# runtime stage
# serviamo l'app 
# (partiamo da un'immagine pulita di Nginx, senza Node.js né git né codice sorgente, per avere un container leggero e sicuro)
FROM nginx

# devo copiare la cartella dist del nostro primo stage
# gli dico di copiare tutta la directory
# (prendiamo SOLO i file compilati dallo stage "build" al percorso completo in cui ng build li ha generati, e li mettiamo nella cartella pubblica di Nginx)
COPY --from=build /app/SomeBankingApp/frontend/dist/SomeBankingFrontend/browser /usr/share/nginx/html