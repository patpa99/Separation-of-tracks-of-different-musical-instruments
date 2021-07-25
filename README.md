# Separation of tracks of different musical instruments

### Lingua italiana:

Separazione di due strumenti musicali mediante l'utilizzo di filtri in frequenza, breve progetto Python Notebook per "Fondamenti dell'Elaborazione di Segnali e Immagini" presso l'Università degli Studi di Genova (UniGe).

**Autore:** Paolo Patrone (https://github.com/patpa99)

**Obiettivi:**

 1. Analisi delle tracce del didgeridoo e del triangolo in modo separato
 2. Sovrapposizione delle tracce dei due strumenti per formare una traccia unica
 3. Analisi della traccia unica
 4. Separazione della traccia unica al fine di ottenere le tracce dei due diversi strumenti analizzati in precedenza

**Riferimenti dei file .wav**
**didgeridoo.wav:** file scaricato dal sito SampleSwap
**triangolo.wav:** traccia scaricata dal sito SampleSwap e poi modificata con un programma in Python, creato da me, in modo da ottenere il suono in un loop di 4 secondi

**Riferimenti esterni**
Materiale presente su Aulaweb e qualche informazione su siti come Wikipedia


#### Introduzione

Nel suono, che si propaga in un mezzo fluido (tipicamente in aria), i movimenti vibratori, provenienti da un determinato oggetto (chiamato sorgente del suono), provocano oscillazioni che sono spostamenti delle particelle intorno alla posizione di riposo e lungo la direzione di propagazione dell'onda. Questi movimenti vibratori originano onde sonore.

Il suono può essere analizzato:

 - nel dominio del tempo (ascoltabile dagli esseri umani)
 - nel dominio della frequenza

#### Filtri nel dominio della frequenza
Vengono utilizzati per selezionare solo alcune frequenze utili o interessanti, eliminando le altre. Sono applicabili sia a segnali 1D (ad esempio segnali audio) che a segnali 2D (ad esempio immagini) che ad altri segnali multi-dimensionali. Durante questo progetto mi concentrerò sui filtri in frequenza applicati a segnali audio.

Per filtrare un segnale nel dominio della frequenza è necessario:

 1. Calcolare la trasformata di Fourier del segnale (F(x))
 2. Moltiplicare la trasformata di Fourier trovata (F(x)) per una funzione di filtro (H(x))
 3. Calcolare l'inversa della trasformata di Fourier di quello che si è ottenuto dal punto precedente, in modo da tornare nel dominio del tempo

![Procedimento filtraggio](https://user-images.githubusercontent.com/33847220/126905360-286a2fa1-2181-410f-8df1-26b8df0c00d1.png)

Le tipologie di filtri in frequenza sono:

 - **filtri passa-alto:** filtro che permette solo il passaggio delle alte frequenze, tagliando le basse frequenze (sotto una certa frequenza di taglio). Il filtro passa-alto ideale taglia tutte le componenti a bassa frequenza che sono a una distanza inferiore o uguale alla distanza specificata  D0  dall'origine della trasformata di Fourier. Il filtro passa-alto ideale è strutturato nel seguente modo:  H(x)=0  se  D(x)<=D0 , altrimenti  H(x)=1  se  D(x)>D0 
 - **filtri passa-basso**: filtro che permette solo il passaggio delle basse frequenze, tagliando le alte frequenze (sopra una certa frequenza di taglio). Il filtro passa-basso ideale taglia tutte le componenti ad alta frequenza che sono a una distanza superiore alla distanza specificata  D0  dall'origine della trasformata di Fourier. Il filtro passa-basso ideale è strutturato nel seguente modo:  H(x)=1  se  D(x)<=D0 , altrimenti  H(x)=0  se  D(x)>D0 
 - **filtri passa-banda**: filtro che permette solo il passaggio delle frequenze all'interno di un dato intervallo, tagliando le frequenze non presenti in questo intervallo. Può essere formato componendo filtri passa-alto e passa-basso tra loro.
Sostanzialmente, moltiplicando la trasformata di Fourier del segnale per la funzione di filtro, verranno moliplicate per 0 le frequenze che si vogliono tagliare e per 1 le frequenze che si vogliono lasciare inalterate.

Io in questo progetto utilizzo filtri passa-banda.


#### Esecuzione

Sostanzialmente analizzo le tracce dei due strumenti musicali in modo da capire a quali frequenze lavorano, poi li unisco in un'unica traccia musicale e la analizzo ed infine utilizzando le informazioni che ho acquisito dalle analisi precedenti separo la traccia unita in due tracce in modo da ottenere tracce il più simili possibile a quelle di partenza.

**Analisi del segnale audio del didgeridoo:**

Possiamo notare che il grafico delle frequenze del didgeridoo risulta essere sostanzialmente nullo con circa: 2000Hz < f < 42000Hz

![Analisi del segnale audio del didgeridoo](https://user-images.githubusercontent.com/33847220/126905605-baaa51c6-d101-4f7c-a761-7b782a348092.png)

**Analisi del segnale audio del triangolo:**

Possiamo notare che il grafico delle frequenze del triangolo risulta essere sostanzialmente nullo con circa:

 f < 4500Hz  (eccetto un piccolo picco)

 oppure

 11000Hz < f<34000Hz

 oppure

 f > 39500Hz (eccetto un piccolo picco)

![Analisi del segnale audio del triangolo](https://user-images.githubusercontent.com/33847220/126905706-31aa66ee-d5bd-48fe-9c3e-5104105ea6eb.png)



### English language:

Separation of two musical instruments through the use of frequency filters, little Python Notebook project for "Fundamentals of signal and image processing" at University of Genoa (UniGe).
