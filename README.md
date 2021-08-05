# Separation of tracks of different musical instruments

## English language:

Separation of two musical instruments through the use of frequency filters, little Python Notebook project for "Fundamentals of signal and image processing" at University of Genoa (UniGe).

**Author:** Paolo Patrone (https://github.com/patpa99)

**Goals:**

 1. Analysis of the tracks of the didgeridoo and the triangle separately
 2. Overlapping the tracks of the two instruments to form a single track
 3. Analysis of the single track
 4. Separation of the single track in order to obtain the tracks of the two different instruments analyzed previously

**References of .wav files**

 - **didgeridoo.wav:** file downloaded from [SampleSwap](https://sampleswap.org/filebrowser-new.php?q=didgeridoo.wav) site
 - **triangle.wav:** track downloaded from [SampleSwap](https://sampleswap.org/filebrowser-new.php?q=triangle10.wav) site and then modified with a Python program, created by me, in order to obtain the sound in a 4 second loop

**External references**

Material on Aulaweb and some information on sites such as Wikipedia

### Introduction

In sound, which propagates in a fluid medium (typically in air), the vibratory movements, coming from a certain object (called sound source), cause oscillations which are displacements of the particles around the resting position and along the direction of propagation wave. These vibratory movements originate sound waves.

Sound can be analyzed:

 - in the time domain (hearable by humans)
 - in the frequency domain

### Filters in the frequency domain
They are used to select only some useful or interesting frequencies, eliminating the others. They are applicable to both 1D signals (e.g. audio signals) and 2D signals (e.g. images) and other multi-dimensional signals. During this project I will focus on frequency filters applied to audio signals.

To filter a signal in the frequency domain it is necessary:

 1. Calculate the Fourier transform of the signal (F(x))
 2. Multiply the Fourier transform found (F(x)) by a filter function (H(x))
 3. Calculate the inverse of the Fourier transform of the one obtained from the previous point, in order to return to the time domain

![Filtering procedure](https://user-images.githubusercontent.com/33847220/126905360-286a2fa1-2181-410f-8df1-26b8df0c00d1.png)

The types of frequency filters are:

 - **high-pass filters:** filter that allows only the passage of high frequencies, cutting the low frequencies (below a certain cut-off frequency). The ideal high-pass filter cuts all low-frequency components that are less than or equal to the specified distance D0 from the origin of the Fourier transform. The ideal high-pass filter is structured as follows: H(x)=0 if D(x)<=D0, otherwise H(x)=1 if D(x)>D0
 - **low-pass filters**: filter that allows only the passage of low frequencies, cutting the high frequencies (above a certain cut-off frequency). The ideal low-pass filter cuts all high-frequency components that are more than the specified distance D0 from the origin of the Fourier transform. The ideal low-pass filter is structured as follows: H(x)=1 if D(x)<=D0, otherwise H(x)=0 if D(x)>D0
 - **band-pass filters**: filter that allows only the passage of frequencies within a given range, cutting the frequencies not present in this range. It can be formed by composing high-pass and low-pass filters together.

Basically, by multiplying the Fourier transform of the signal by the filter function, the frequencies to be cut will be multiplied by 0 and the frequencies to be left unchanged by 1.

I use band-pass filters in this project.

### Execution

Basically I analyze the tracks of the two musical instruments in order to understand at which frequencies they work, then I combine them into a single musical track and analyze it and finally, using the information I have acquired from the previous analyzes, I separate the combined track into two tracks in order obtain tracks as similar as possible to the starting ones.

**Didgeridoo Audio Signal Analysis:**

We can see that the frequency graph of the didgeridoo turns out to be substantially null with about: 2000Hz < f <42000Hz

![Didgeridoo Audio Signal Analysis](https://user-images.githubusercontent.com/33847220/128391836-5744f283-fa9f-4f7e-bc60-38e7a2acbfbf.png)

**Triangle audio signal analysis:**

We can note that the graph of the frequencies of the triangle turns out to be substantially zero with approximately:

 f < 4500Hz (except a small peak)

 or

 11000Hz < f <34000Hz

 or

 f > 39500Hz (except a small peak)

![Triangle audio signal analysis](https://user-images.githubusercontent.com/33847220/128391938-aab220ca-453e-4d2b-bc4e-8e5db5c70fdd.png)

**Analysis of the only musical track obtained by superimposing the tracks of the previous instruments**

We can note that the graph of the frequencies of the superimposed sound turns out to be substantially null with about: 11000Hz < f <34000Hz

![Analysis of the single musical track obtained by superimposing the tracks of the previous instruments](https://user-images.githubusercontent.com/33847220/128392109-eb782823-e59c-45ee-96fb-1de33bdb0a3b.png)

**I get the triangle sound from the overlapping sound**

I filter the overlaid sound in frequency and zero all frequencies where

 f < 4500Hz

 or

 f > 39500Hz

Respecting what we noticed in the graph of the Fourier transform obtained during the analysis of the audio signal of the triangle.

![I get the triangle sound from the overlapping sound](https://user-images.githubusercontent.com/33847220/128392181-94780a28-0235-4770-afbf-7e414ee65191.png)

**I get the didgeridoo sound from the overlapping sound**

Filter the sound superimposed in frequency and zero all frequencies where 2000Hz < f <42000Hz

Respecting what we noticed in the graph of the Fourier transform obtained during the analysis of the audio signal of the didgeridoo.

![I get the didgeridoo sound from the overlapping sound](https://user-images.githubusercontent.com/33847220/128392259-7628ff9d-7e29-41c4-ad4e-39487715e3ae.png)

To hear the sounds obtained, it is necessary to use the inverse Fourier transform which will bring us back to the time-dependent and therefore listenable signals.

To hear all the sounds and further deepen the conclusions and technical details read the Notebook.


## Lingua italiana:

Separazione di due strumenti musicali mediante l'utilizzo di filtri in frequenza, breve progetto Python Notebook per "Fondamenti dell'Elaborazione di Segnali e Immagini" presso l'Università degli Studi di Genova (UniGe).

**Autore:** Paolo Patrone (https://github.com/patpa99)

**Obiettivi:**

 1. Analisi delle tracce del didgeridoo e del triangolo in modo separato
 2. Sovrapposizione delle tracce dei due strumenti per formare una traccia unica
 3. Analisi della traccia unica
 4. Separazione della traccia unica al fine di ottenere le tracce dei due diversi strumenti analizzati in precedenza

**Riferimenti dei file .wav**

 - **didgeridoo.wav:** file scaricato dal sito [SampleSwap](https://sampleswap.org/filebrowser-new.php?q=didgeridoo.wav)
 - **triangle.wav:** traccia scaricata dal sito [SampleSwap](https://sampleswap.org/filebrowser-new.php?q=triangle10.wav) e poi modificata con un programma in Python, creato da me, in modo da ottenere il suono in un loop di 4 secondi

**Riferimenti esterni**

Materiale presente su Aulaweb e qualche informazione su siti come Wikipedia


### Introduzione

Nel suono, che si propaga in un mezzo fluido (tipicamente in aria), i movimenti vibratori, provenienti da un determinato oggetto (chiamato sorgente del suono), provocano oscillazioni che sono spostamenti delle particelle intorno alla posizione di riposo e lungo la direzione di propagazione dell'onda. Questi movimenti vibratori originano onde sonore.

Il suono può essere analizzato:

 - nel dominio del tempo (ascoltabile dagli esseri umani)
 - nel dominio della frequenza

### Filtri nel dominio della frequenza
Vengono utilizzati per selezionare solo alcune frequenze utili o interessanti, eliminando le altre. Sono applicabili sia a segnali 1D (ad esempio segnali audio) che a segnali 2D (ad esempio immagini) che ad altri segnali multi-dimensionali. Durante questo progetto mi concentrerò sui filtri in frequenza applicati a segnali audio.

Per filtrare un segnale nel dominio della frequenza è necessario:

 1. Calcolare la trasformata di Fourier del segnale (F(x))
 2. Moltiplicare la trasformata di Fourier trovata (F(x)) per una funzione di filtro (H(x))
 3. Calcolare l'inversa della trasformata di Fourier di quello che si è ottenuto dal punto precedente, in modo da tornare nel dominio del tempo

![Procedimento filtraggio](https://user-images.githubusercontent.com/33847220/126905360-286a2fa1-2181-410f-8df1-26b8df0c00d1.png)

Le tipologie di filtri in frequenza sono:

 - **filtri passa-alto:** filtro che permette solo il passaggio delle alte frequenze, tagliando le basse frequenze (sotto una certa frequenza di taglio). Il filtro passa-alto ideale taglia tutte le componenti a bassa frequenza che sono a una distanza inferiore o uguale alla distanza specificata  D0  dall'origine della trasformata di Fourier. Il filtro passa-alto ideale è strutturato nel seguente modo: H(x)=0 se D(x)<=D0, altrimenti H(x)=1 se D(x)>D0
 - **filtri passa-basso**: filtro che permette solo il passaggio delle basse frequenze, tagliando le alte frequenze (sopra una certa frequenza di taglio). Il filtro passa-basso ideale taglia tutte le componenti ad alta frequenza che sono a una distanza superiore alla distanza specificata D0 dall'origine della trasformata di Fourier. Il filtro passa-basso ideale è strutturato nel seguente modo: H(x)=1 se D(x)<=D0, altrimenti H(x)=0 se D(x)>D0
 - **filtri passa-banda**: filtro che permette solo il passaggio delle frequenze all'interno di un dato intervallo, tagliando le frequenze non presenti in questo intervallo. Può essere formato componendo filtri passa-alto e passa-basso tra loro.

Sostanzialmente, moltiplicando la trasformata di Fourier del segnale per la funzione di filtro, verranno moliplicate per 0 le frequenze che si vogliono tagliare e per 1 le frequenze che si vogliono lasciare inalterate.

Io in questo progetto utilizzo filtri passa-banda.


### Esecuzione

Sostanzialmente analizzo le tracce dei due strumenti musicali in modo da capire a quali frequenze lavorano, poi li unisco in un'unica traccia musicale e la analizzo ed infine utilizzando le informazioni che ho acquisito dalle analisi precedenti separo la traccia unita in due tracce in modo da ottenere tracce il più simili possibile a quelle di partenza.

**Analisi del segnale audio del didgeridoo:**

Possiamo notare che il grafico delle frequenze del didgeridoo risulta essere sostanzialmente nullo con circa: 2000Hz < f < 42000Hz

![Analisi del segnale audio del didgeridoo](https://user-images.githubusercontent.com/33847220/128392487-82531701-6b7a-45a1-8b31-8bd19326336b.png)

**Analisi del segnale audio del triangolo:**

Possiamo notare che il grafico delle frequenze del triangolo risulta essere sostanzialmente nullo con circa:

 f < 4500Hz  (eccetto un piccolo picco)

 oppure

 11000Hz < f<34000Hz

 oppure

 f > 39500Hz (eccetto un piccolo picco)

![Analisi del segnale audio del triangolo](https://user-images.githubusercontent.com/33847220/128392535-66c1c844-1318-4ad7-b6c5-c22f66da01c8.png)

**Analisi dell'unica traccia musicale ottenuta dalla sovrapposizione delle tracce degli strumenti precedenti**

Possiamo notare che il grafico delle frequenze del suono sovrapposto risulta essere sostanzialmente nullo con circa: 11000Hz < f < 34000Hz

![Analisi dell'unica traccia musicale ottenuta dalla sovrapposizione delle tracce degli strumenti precedenti](https://user-images.githubusercontent.com/33847220/128392652-60b23ebd-6d3f-4452-bbc7-9df3b4d60ffb.png)

**Ottengo il suono del triangolo dal suono sovrapposto**

Filtro il suono sovrapposto in frequenza e azzero tutte le frequenze dove

 f < 4500Hz

 oppure

 f > 39500Hz

Rispettando quello che abbiamo notato nel grafico della trasformata di Fourier ottenuta durante l'analisi del segnale audio del triangolo.

![Ottengo il suono del triangolo dal suono sovrapposto](https://user-images.githubusercontent.com/33847220/128392742-fd9000cf-b793-463f-a9fa-b4eebc11cab1.png)

**Ottengo il suono del didgeridoo dal suono sovrapposto**

Filtro il suono sovrapposto in frequenza e azzero tutte le frequenze dove 2000Hz < f < 42000Hz

Rispettando quello che abbiamo notato nel grafico della trasformata di Fourier ottenuta durante l'analisi del segnale audio del didgeridoo.

![Ottengo il suono del didgeridoo dal suono sovrapposto](https://user-images.githubusercontent.com/33847220/128392839-083be356-8e02-4438-be63-b235baa7ab5a.png)

Per ascoltare i suoni ottenuti è necessario utilizzare la trasformata inversa di Fourier che ci riporterà ai segnali dipendenti dal tempo e quindi ascoltabili.

Per ascoltare tutti i suoni e approfondire ulteriormente le conclusioni e i dettagli tecnici leggere il Notebook.
