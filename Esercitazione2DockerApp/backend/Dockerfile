# creiaoo l'immagine con python . farà il download dell'immagine python
FROM python
# per non fare ccasino , specifico la WORKDIR
WORKDIR /app 
# ora copio  , metto . (?)
COPY ./requirements.txt .
#qui 63 :00
COPY ./main.py . 
#devo eseguire l'installaziobne di quei pip installaziobne
RUN pip install -r requirements.txt 
# nel caso ci fosse un errore (?) (57:00) l'esecuzione viene bloccata 
ENTRYPOINT [ "python" , "-m" ,"uvicorn", "main:app" ]

