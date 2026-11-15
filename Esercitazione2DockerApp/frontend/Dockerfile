# costruiamo l'app
FROM node AS build 
WORKDIR /app
COPY . . 
RUN npm i
RUN ./node_modules/.bin/ng build 

# runtime stage
# serviamo l'app 
FROM nginx
# devo copiare la cartella dist del nostro primo stage
# gli dico di copiare tutta la directory
COPY --from=build /app/dist/SomeBankingFrontend/browser /usr/share/nginx/html