---
name: canto-md
description: Genera il file .md di commento narrativo per un canto della Divina Commedia (Inferno, Purgatorio o Paradiso) a partire dal testo grezzo del canto. Usa SEMPRE questa skill quando l'utente incolla o allega il testo completo e grezzo di un canto — tipicamente uno scrape da un sito di studio con sezioni come "Argomento del Canto", una scomposizione narrativa per terzine (es. "La selva dei suicidi (1-21)"), "Interpretazione complessiva", "Note e passi controversi", "Testo" (i versi originali) e "Parafrasi" — anche se l'utente non lo chiede esplicitamente con queste parole. Attivala anche per richieste come "genera il md per questo canto", "crea il commento del canto X", "trasforma questo testo in un riassunto/commento", o quando allega un file .txt con il contenuto di un canto in una cartella di questo archivio. Non serve per riassumere un canto già esistente in formato .md (quello è un altro compito) né per lavorare su PDF.
---

# Canto → Markdown

Questa skill trasforma il testo grezzo di un canto della *Divina Commedia* (fornito dall'utente come testo incollato o come file `.txt`) in un file `.md` di commento narrativo, con lo stesso identico formato già usato in tutto l'archivio.

Sostituisce una pipeline che l'utente eseguiva manualmente in tre passaggi separati (narrazione cinematografica → titolo → riassunto strutturato): qui vanno fusi in un'unica generazione coerente, senza bisogno di andare avanti e indietro con l'utente.

## Riferimento canonico — leggilo sempre per primo

Prima di scrivere qualsiasi cosa, rileggi questa coppia di file reali già presenti nell'archivio: sono l'esempio vivente di input → output e vanno trattati come lo standard di riferimento, non solo come ispirazione.

- Input grezzo: `Inferno/13° Canto/content.txt`
- Output atteso: `Inferno/13° Canto/Inferno, Canto XIII.md`

Studia come il secondo deriva dal primo: cosa viene narrato, cosa viene spiegato, dove vengono inserite le citazioni in blockquote, come è scritta la sezione finale di analisi, come è costruito il riassunto. Il file che produrrai per un nuovo canto deve poter stare in quell'archivio senza stonare per stile, tono o livello di dettaglio.

## 1. Leggi tutto il testo grezzo prima di scrivere

Il testo che l'utente fornisce di solito contiene più blocchi: un "Argomento del Canto" riassuntivo, una scomposizione in episodi con intervalli di versi (es. "Incontro con Pier della Vigna (55-78)"), una sezione di analisi complessiva, note puntuali su singoli versi, il testo poetico originale in terzine e una parafrasi verso per verso. I nomi esatti delle sezioni possono variare da fonte a fonte — non bloccarti se le etichette non coincidono parola per parola con l'esempio: riconosci il contenuto per quello che è (argomento generale, episodi, analisi, note, versi, parafrasi) anche se è organizzato o intitolato diversamente. Se l'utente fornisce solo i versi senza note o parafrasi, fai comunque del tuo meglio: la narrazione sarà più asciutta ma deve restare fedele a quel testo.

Non iniziare a scrivere il file finché non hai letto e capito l'intero contenuto fornito: ogni fatto, nota e dettaglio presente nel testo deve poter finire da qualche parte nel documento finale.

## 2. Identifica cantica, numero del canto e cartella di destinazione

Il testo grezzo di solito dichiara esplicitamente la cantica e il numero del canto (es. un titolo "Inferno, Canto XIII" o un riferimento a Purgatorio/Paradiso). Se non è esplicito, deducilo dal contesto (personaggi, luoghi, temi — Inferno se si parla di dannati e pene eterne, Purgatorio se di anime in espiazione, Paradiso se di beati e cieli).

Converti il numero in arabo e romano usando `references/numeri-romani.md`. Poi determina la cartella di destinazione: `<Cantica>/<numero arabo>° Canto/` nella root dell'archivio (es. `Purgatorio/3° Canto/`). Se la cartella non esiste, creala — è normale, oggi solo `Inferno/` è popolato ma `Purgatorio/` e `Paradiso/` sono cartelle vuote pronte a essere riempite con la stessa struttura.

**Prima di scrivere qualunque file**, controlla se in quella cartella esiste già un `.md` di commento. Se esiste, fermati e chiedi conferma all'utente prima di sovrascriverlo — potrebbe trattarsi di un lavoro già rifinito a mano.

## 3. Struttura del file — segui questo schema esatto

```markdown
# <Cantica>, Canto <numero romano> — <Titolo evocativo>

## 1. <Titolo della prima scena/episodio>

<narrazione...>

---

## 2. <Titolo della seconda scena/episodio>

<narrazione...>

---

... (una sezione numerata per ogni episodio/blocco narrativo del canto, nello stesso ordine in cui accadono)

## Il senso del canto

<analisi complessiva...>

## Riassunto

---

<paragrafo introduttivo, senza titolo>

1. **<Titolo breve episodio 1>**
<2-5 frasi di riassunto>
2. **<Titolo breve episodio 2>**
<2-5 frasi di riassunto>
...

<eventuale paragrafo di chiusura>
```

### Il titolo (H1)

Formato: `<Cantica>, Canto <numero romano> — <Titolo>`. Il titolo va inventato da te, breve ed evocativo, coerente con lo stile già in uso nell'archivio (guarda gli altri file `.md` nelle cartelle dei canti per calibrarti). Alcuni esempi reali già usati: "Lo smarrimento e la selva oscura", "I dubbi di Dante e la missione di Virgilio", "La porta dell'Inferno", "Farinata e Cavalcante", "Le mura di Dite". A volte il titolo ha un doppio livello separato da due punti, come nel Canto XIII: "La selva dei suicidi: il pianto di Pier della Vigna" — usalo quando il canto ha sia un'ambientazione/tema generale sia un episodio o personaggio dominante che vale la pena nominare esplicitamente.

**Il nome del file non deve includere il sottotitolo.** Anche se l'H1 è lungo, il file va salvato come `<Cantica>, Canto <numero romano>.md` (es. `Inferno, Canto XIII.md`), esattamente come il riferimento canonico — questa è la convenzione stabilita in questo archivio (vedi `CLAUDE.md` nella root).

### Le sezioni narrative numerate

Qui va la parte più corposa e importante: racconta il canto come una scena vissuta, non come un riassunto scolastico. Non dire mai "in questa scena", "il canto si apre con", "l'autore descrive" — descrivi direttamente ciò che accade, come se il lettore lo stesse vedendo. Regole, tutte tratte da come è già stato fatto nell'archivio:

- Segui l'ordine cronologico degli eventi, senza saltarne nessuno.
- Includi ogni fatto presente nel testo grezzo, note e commenti compresi — niente va perso, ma va integrato nel racconto nel punto più naturale, non isolato in una sezione a parte. Se un dettaglio storico, filologico o interpretativo (un riferimento letterario, una variante testuale, il significato di una parola arcaica) chiarisce cosa sta succedendo, tessilo nella narrazione proprio lì, con naturalezza.
- Se il testo specifica quando e dove si svolge l'azione (ora, giorno, stagione, luogo, cerchio/girone), inseriscilo nella narrazione.
- Descrivi l'ambiente in modo visivo — luci, colori, suoni, atmosfera — e racconta cosa pensa e prova Dante personaggio in ogni momento, e perché agisce come agisce.
- Quando compare un nuovo personaggio, presentalo subito: chi è, perché è importante, perché si trova lì.
- Quando qualcosa ha un significato simbolico o allegorico (un animale, un contrappasso, un oggetto), racconta prima il fatto concreto e solo dopo il significato, in modo semplice.
- Se Dante racconta un ricordo o un episodio del passato, segnalalo chiaramente come tale nella narrazione.
- Per i dialoghi importanti, riporta i versi originali chiave in blockquote (`> ...`), scegliendo le battute più significative o rivelatrici — non l'intero canto in versi, solo i passaggi che nel racconto meritano di essere letti nella voce originale di Dante. Introduci e commenta la citazione nel testo che la circonda.
- Dividi il racconto in sezioni numerate (`## 1.`, `## 2.`...), una per ogni episodio o blocco narrativo distinto (l'arrivo in un luogo, l'incontro con un personaggio, un dialogo, una digressione dottrinale), separate da una riga `---`. Il numero di sezioni dipende dal canto: non forzare uno schema fisso, segui la struttura naturale degli eventi.
- Non inventare nulla che non sia nel testo fornito. Se aggiungi un'informazione di dominio comune tra gli studiosi ma non presente nel testo grezzo (es. una data alternativa, un'identificazione storica dubbia), dillo esplicitamente come tradizione interpretativa esterna, non come fatto certo del testo.

### Il senso del canto

Una sezione unica, in prosa, che analizza il canto nel suo complesso: temi dominanti, scelte stilistiche e retoriche (figure retoriche, registro linguistico, rimandi letterari ad altre opere), simbolismo generale, collegamento con il percorso di Dante. Si basa sul materiale di analisi/interpretazione presente nel testo grezzo (se il testo grezzo lo fornisce con dettaglio, riprendi le osservazioni più significative; se il testo grezzo è povero di analisi, resta più sintetico piuttosto che inventare).

### Il riassunto

Sezione finale pensata per chi ha già letto la narrazione estesa sopra e vuole un ripasso rapido. Struttura esatta:

1. Subito dopo il titolo `## Riassunto` e la riga `---`, un paragrafo introduttivo **senza titolo in grassetto** che indica: il momento del viaggio (tempo narrativo, giorno/notte, data se nota), il cerchio/girone (o balzo/cielo, a seconda della cantica) in cui si svolge il canto, chi vi è punito/espia/si trova e perché. Se il canto prosegue un episodio iniziato nel canto precedente o si svolge a cavallo tra due luoghi, dillo qui.
2. Una lista numerata (`1.`, `2.`, `3.`...), una voce per ogni episodio/blocco narrativo, nello stesso ordine del testo. Ogni voce ha un titolo breve in **grassetto** seguito da 2-5 frasi in prosa scorrevole che riassumono chi è coinvolto, cosa accade e il significato/simbolismo se rilevante. Se dentro una voce ci sono più elementi elencabili (più domande, più dannati nominati, più profezie), usa un elenco puntato interno.
3. Se pertinente, chiudi con un breve paragrafo che accenna al collegamento con il canto successivo o al senso complessivo, solo se il testo grezzo lo suggerisce chiaramente — non inventare un gancio che non c'è.

Tono narrativo-esplicativo, non troppo tecnico. Markdown minimo: solo grassetto per i titoli di sezione e per i nomi propri più importanti alla prima menzione nel riassunto — niente tabelle, niente citazioni lunghe.

Non aggiungere una riga "Ecco i principali avvenimenti del Canto..." prima della lista: negli esempi reali dell'archivio il riassunto entra direttamente nel paragrafo introduttivo.

## 4. Salva i file

- Il commento va salvato in `<Cantica>/<numero arabo>° Canto/<Cantica>, Canto <numero romano>.md`.
- Salva anche il testo grezzo originale, così com'è stato fornito, come `content.txt` nella stessa cartella — è la prassi già in uso (vedi il Canto XIII) e permette di rigenerare o correggere il commento in futuro senza dover richiedere di nuovo il testo all'utente.
- Se la skill viene invocata per un canto dell'Inferno che ha già le sue cartelle PDF popolate (`Canto_<N>_..._Parafrasi.pdf`, ecc.), non toccare quei PDF: aggiungi solo il `.md` e il `content.txt`.

## 5. Alla fine

Indica all'utente il percorso del file creato e il titolo scelto, così può aprirlo e controllare che narrazione e riassunto rispettino fedelmente il testo che ha fornito.
