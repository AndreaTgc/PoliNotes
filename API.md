## Appunti di API. AA 2021/2022

# Modelli e linguaggi
## I Modelli
**Progettazione basata su modelli:**

La fase di progettazione di un artefatto complesso di basa sull'uso di *modelli*. Il modello consente di focalizzarsi sugli aspetti principali del problema e permette di effettuare delle verifiche preliminari sul funzionamento.

**Modelli formali e il loro uso:**

effettuare una formalizzazione di un problema significa ottenere una descrizione astratta dell'entità reale del problema.
dopo la formalizzazione del problema chiaramente va trovata una soluzione ad esso e per concludere bisogna interpretare i risultati alla luce del modello, nel contesto dell'entità reale &rarr; (ri)valutazione delle scelte di progetto.
Un modello viene detto *adeguato* se riflette con correttezza e precisione il fenomeno modellato per gli aspetti interessati.

**Modelli dell'informatica:**

l'informatica è una delle discipline dove vi è presente una grande vicinanza tra il modello e la realtà di cui si occupa (In questo caso il calcolo)
Nella sua evoluzione i primi calcolatori sono stati la materializzazione diretta del modello di calcolo.

**Applicazioni dell'informatica:**

L'informatica viene applicata in svariati contesti &rarr; un particolare calcolo è il modello di qualcosa di reale.
Il successo è determinato dalla flessibilità del calcolo astratto come modello di una sequenza di ragionamenti logici; spesso la difficolà sta proprio del *formulare* il modello (definire il problema).

## I linguaggi
Il linguaggio è da sempre uno strumento utilizzato per esprimere modelli.

### Gli elementi che compongono un linguaggio

**L'alfabeto:**

Un linguaggio è, per definizione, sempre definito su un *alfabeto*.
L'alfabeto è un insieme finito di simboli di qualsiasi tipo.
esempi:
* *{a,b,c,d,....,z}*
* *{0,1}*
* *Codice Morse, Baudot, ASCII ecc.*  

**Stringa di un alfabeto arbitrario A:**

Una stringa è una sequenza ordinata e finita di elementi dell'alfabeto.
La lunghezza di una stringa è, come ci si può immaginare, il numero di caratteri che la compongono &rarr; |a| = 1, |stringa| = 7.  
Inoltre, a prescindere dall'alfabeto utilizzato, è presente anche la stringa nulla **ε** &rarr; |ε| = 0.  
A* è invece l'insieme di tutte le stringhe (incluse quella nulla) su A.
 * *Esempio:* A = {0,1}, A* = {ε,0,1,00,01,10,11,100...}

**Operazioni sulle stringhe:**  

Concatenazione &rarr; operazione che concatena due stringhe
  *Esempio:* x = Bana, y = na &rarr; x.y = Banana

**Monoide libero:**

Dato un alfabeto arbitrario A &rarr; **(A* , .)** è il *monoide libero* costruito su A, l'elemento neutro di questo monoide è ε.  

**Il Linguaggio:**

Un linguaggio **L** su un alfabeto **A** è un sottoinsieme di **A*** ovvero un insieme di parole di A.
*esempi:*  
* *l'italiano è un linguaggio su A = {a,b,c,d,e,...}*
* *I files pdf sono un linguaggio su A = {0,1}*
* *Il DNA è un linguaggio codificabile su A = {C,G,A,T}*
* *I numeri pari in base 4 sono un linguaggio su A = {0,1,2,3}*  
**NOTA BENE:** anche se |A| < ∞, non necessariamente si avrà che |L| < ∞ (vedi ultimo esempio).

## Operazioni tra linguaggi

Un dato linguaggio L è a tutti gli effetti un insieme, di conseguenza valgono l'Unione ∪, l'intersezione ∩ e la differenza \ .  
Il complemento ¬L è definito come A*\L  

**Concatenazione tra linguaggi:**  

Dati L<sub>1</sub> su A<sub>1</sub> e L<sub>2</sub> su A<sub>2</sub> &rarr; L<sub>1</sub>.L<sub>2</sub> definito su A<sub>1</sub> ∪ A<sub>2</sub> è:  
L<sub>1</sub>.L<sub>2</sub> = {x.y | x ∈ L<sub>1</sub>, y ∈ L<sub>2</sub>}  

 *esempio:* &rarr; Dati L<sub>1</sub> = {0,1}*, L<sub>2</sub> = {a,b}* abbiamo che:  
 * L<sub>1</sub>.L<sub>2</sub> = {ε,0,1,0a,011b,0aba,...}   
 **NOTA BENE:** la stringa a1 **non fa parte** di  L<sub>1</sub>.L<sub>2</sub>.
                   
**Alcune proprietà:**

* L<sup>n</sup>, n ∈ N, è la concatenazione di L con sè stesso *n* volte.   
**NOTA BENE:** Il lunguaggio vuoto L<sub>1</sub> = ∅ ≠ {ε} = L<sub>2</sub>  

**Operatore +**

L'operatore **+** indica le stringhe fatte concatenando uno o più elementi dell'insieme.
* A = {0,1}, A<sup>+</sup> = {0,1,00,01,...}
* *Per estensione* &rarr; L<sup>*</sup> = U<sup>∞</sup><sub>n=0</sub>  L<sup>n</sup>  ,   L<sup>+</sup> = U<sup>∞</sup><sub>n=1</sub>  L<sup>n</sup>,
                   
 **Il linguaggio come formalismo espressivo:**  
 
Un linguaggio può essere usato per esprimere un problema:
* trovare la miglior mossa successiva in una partita a scacchi  
* trovare tre numeri interi positivi tali per cui x<sup>3</sup> + y<sup>3</sup> = z<sup>3</sup>  

L'insieme delle soluzioni di un problema è un linguaggio  

* risolvere un problema &rarr; calcolare (riconoscere) un x ∈ L
* *esempio:*  "Questo programma C è sintatticamente corretto?" &rarr; Data x dire se x ∈ L<sub>linguaggio c</sub>  

### Passare da un linguaggio all'altro

**traduzioni:**  

Tradurre &rarr; mettere in corrispondenza parole di due linguaggi.  
Formalmente, una traduzione è una mappa τ (·): L<sub>1</sub> &rarr; L<sub>2</sub>  

* L<sub>1</sub> = {a,b}* , L<sub>2</sub> = {c,d}* , τ mappa a &rarr; c , b &rarr; d ,  τ(ba) = dc. 


# Automi a stati finiti 

## un semplice modello di calcolo  

* I modelli operazionali di calcolo vengono definiti come *macchine astratte*.  
* Esse modellano il calcolo come una serie di passaggi discreti tra uno stato precedente e uno successivo. 
* Le macchine più semplici sono gli **automi a stati finiti** (anche dette *finite state automata FSA*), esse hanno una memoria di calcolo formata da un insieme finito di stati
* *esempi:* {marce di un'auto}, {in partenza, in viaggio, arrivo}, {1,2,...,k}.  

## Formalizzazione 

**Costituenti di un FSA**  

* **Q** &rarr; l'insieme finito dei suoi stati.  
* **I** &rarr; l'insieme finito (alfatebo) dei simboli in ingresso.
* **δ: Q × I &rarr; Q** &rarr; la funzione di transizione: mappa una coppia (stato corrente e destinazione).  
* Serve definire un inizio della computazione: chiamiamo q<sub>0</sub> ∈ **Q** lo stato iniziale del nostro automa. Esso viene indicato graficamente con una freccia entrante non generata da alcuno stato.  

## FSA riconoscitore  

**Riconoscere un linguaggio con un FSA**  

Possiamo utilizzare un FSA per riconoscere le parole di un linguaggio, definiamo l'insieme di stati finali **F ⊆ Q**.  
Se l'automa, leggendo una stringa, partendo da q<sub>0</sub> termina in uno stato finale allora la stringa appartiene al linguaggio.  

**Formalizzazione dell'accettazione**

**Sequenza di mosse** &rarr; Formalizziamo una sequenza di mosse definendo **δ<sup>*</sup> : Q × I<sup>*</sup> &rarr; Q** estensione di δ, induttivamente:  
* Base: ∀q ∈ Q, δ<sup>*</sup>(q,ε) = q  
* Passo: δ<sup>*</sup>(q, y.i) = δ(δ<sup>*</sup>(q, y), i)  


**Accettazione di un linguaggio** &rarr; Possiamo formalizzare l'accettazione di un linguaggio L su I da parte di un FSA (Q, I, δ, q<sub>0</sub>, F) in questo modo:  x ∈ L ⇔ δ<sup>*</sup>(q<sub>0</sub>, x) ∈ F


## Formalizzazione di un traduttore  

**Elementi del traduttore**  

* Un FSA traduttore: 7-upla *A*: (Q, I, δ, q<sub>0</sub>, F, O, η)  
* ⟨Q, I, δ, q<sub>0</sub>, F⟩ come nell'FSA riconoscitore. 
* **O**: Alfabeto di uscita. 
* η : Q × I → O<sup>*</sup> Funzione di traduzione. 


**Funzione di traduzione per stringhe η<sup>*</sup>**

* **η<sup>*</sup> : Q × I<sup>*</sup> → O<sup>*</sup>** Definita in maniera analoga  
Base η<sup>*</sup>(q,ε) = ε  
Passo η<sup>*</sup>(q, y.i) = η<sup>*</sup>(q, y).η(δ<sup>*</sup>(q, y), i)  

* L'intero calcolo di una traduzione è quindi formalizzato come:  τ(x) = η<sup>*</sup>(q<sub>0</sub>,x) ⇔ δ<sup>*</sup>(q<sub>0</sub>,x) ∈ **F**  

## Formalizzazione del comportamento ciclico   

**Pumping lemma**  
 
**Premessa** &rarr;  ∃x ∈ L, L riconosciuto da FSA, |x| > |Q|  
* Conseguenza &rarr; esistono q ∈ Q, w ∈ I<sup>+</sup> tali che x = ywz con y, z  ∈ I<sup>*</sup> e δ<sup>*</sup>(q,w) = q  
ovvero esiste una sottostringa di x che viene riconosciuta dall’automa effettuando un’iterazione su un ciclo di stati. 
* Dal pumping lemma segue che yw<sup>n</sup>z ∈ L,  ∀n ≥ 0.

**Proprietà dei linguaggi riconosciuti da FSA**  

* Posso dire se L = ∅  
∃x ∈ L ⇒ ∃y ∈ L, |y| < |Q| &rarr; se una parola ha “cicli in riconoscimento” li elimino &rarr; posso dare in pasto le y all’FSA (sono finite) e verificare se almeno una ∈ L
* Posso dire se L = ∞  
∃x ∈ L, |Q| ≤ |x| < 2|Q| implica che x abbia un ciclo in riconoscimento. 

## Limitazioni degli FSA  

**Riconoscere le strutture a parentesi**

Domanda: L = {a<sup>n</sup>b<sup>n</sup> | n ≥ 0} è riconosciuto da un FSA?  
intuizione: **NO**, dimostriamolo per assurdo. 

sia x ∈ L, x = a<sup>m</sup>b<sup>m</sup>, m/2 > |Q|, applicando il pumping lemma abbiamo che x = ywz, con w che deve avere una di queste forme: 
* w = a<sup>k</sup>, pompando w ottengo ∀r ∈ N, a<sup>m-k</sup>a<sup>r·k</sup>b<sup>m</sup> ∈ L, **non va** 
* w = b<sup>k</sup>, pompando w ottengo ∀r ∈ N, a<sup>m</sup>a<sup>r·k</sup>b<sup>m-k</sup> ∈ L, **non va** 
* w = a<sup>k</sup>b<sup>h</sup>, pompando w ottengo ∀r ∈ N, a<sup>m-k</sup>(a<sup>k</sup>b<sup>h</sup>)<sup>r</sup>b<sup>m-h</sup> ∈ L, **non va** 

**Verso modelli più potenti**  

* Intuitivamente: per “contare” un n arbitrariamente grande, occorre una quantità di memoria altrettanto grande. 
* Riconoscere strutture a parentesi (HTML,XML,linguaggi di programmazione) non è fattibile per un FSA. 
* Anche modellare un calcolatore fisico (che è un FSA) come tale può essere scomodo/intrattabile. 
* è necessario estendere gli FSA per riuscire a renderli più efficaci. 

## Il concetto di chiusura 

### Chiusura algebrica 

Dati un insieme S, ed un’operazione definita sui suoi elementi si dice che S è chiuso rispetto all’operazione, se il risultato di dell’applicarla ad un elemento di S è contenuto in S. 

### Chiusura nei linguaggi 

**chiusura di famiglie di linguaggi**  

* Famiglia di linguaggi: un insieme **L** i cui elementi sono linguaggi, **L** = {L<sub>i</sup>}  
* L è chiusa rispetto a un’operazione (binaria) ⋆ se ∀L1, L2 ∈ **L** vale L1 ⋆ L2 ∈ **L**  

**Linguaggi regolari**  

* La famiglia di linguaggi riconoscibili con un FSA è la famiglia dei linguaggi regolari, **R** o REG.  
* **R** è chiusa rispetto a ∪, ∩, ¬, \, alla concatenazione, a ∗ e +  

# Automi a pila  

## Aumentiamo la potenza di un FSA  

**Descrizione operativa dell'automa a pila**  

Un FSA ha un organo di controllo (OC) con memoria finita e un nastro di input infinito su cui non può scrivere.
Se l'automa a pila considerato è un traduttore, esso ha un nastro di output sul quale può solo scrivere.  
La "memoria" dello stato di calcolo è finita.  

**Una memoria estesa**  

Al concetto descritto prima aggiungiamo una memoria a impilamento:  
* Infinita
* Accesso alla sola cima  
* La lettura cancella  
* Funziona con metodo LIFO  

**Descrizione Operativa**  

L'automa a pila compie una mossa in funzione di:  
* simbolo letto dalla cima della pila. 
* stato corrente nell'FSA che costituisce l'organo di controllo. 
* Opzionalmente, simbolo letto dal nastro in ingresso  

L'automa a pila passa alla configurazione successiva:  
* Cambiando stato nell'OC.
* sostituendo al simbolo in cima allo stack una stringa α di simboli (potenzialmente α = ε)  
* Spostando (opzionalmente) la testina di lettura  
* Se l'automa è un traduttore, scrivendo una stringa (potenzialmente nulla)  

### Riconoscitori e traduttori  

**Automa riconoscitore**  

La stringa x in ingresso è riconosciuta (accettata) se:  
* L'automa scandisce completamente x  
* Una volta scandita tutta, lo stato dell'OC è di accettazione. 

**Automa traduttore**  

* Se la stringa è accettata, il nastro di scrittura contiene la sua traduzione al termine del calcolo τ(x).  
* Se la x non è accettata la traduzione è indefinita τ(x) = ⊥  

### Esempio: riconoscere {a<sup>n</sup>b<sup>n</sup> | n > 0} 

**Automa Riconoscitore**  

![Automa Riconoscitore anbn](ApiImages/riconoscitoreAnBn.png)  

**Convenzioni di notazione**  
* Etichetta archi: ⟨lettura input, cima della pila/riscrittura in pila⟩  
* Consideriamo la pila inizializata con Z<sub>0</sub> per marcare il fondo. 

### Stringhe ben parentetizzate  

**Esempio con le parentesi tonde**  

![Riconoscitore di stringhe con tonde](ApiImages/StringheTonde.png)  

**Note:**  
* è una semplificazione del riconoscitore di L = {a<sup>n</sup>b<sup>b</sup>}
* Verifica solamente che il numero di a coincida con quello di b.  

### Esempio di un traduttore  

**Da L<sub>1</sub> ⊂ {a,b,c}<sup>*</sup> a L<sub>2</sub> ⊂ {a,b,c}<sup>*</sup>**  

![traduttore automa a pila](ApiImages/TraduttoreApila.png)   

Questo automa effettua una traduzione impilando A e B fino alla prima c.  

### Formalizzazione  

**Riconoscitore e traduttore**  

* Automa **[Traduttore]** a Pila: ⟨Q, I, Γ, δ, q0, Z0, F **[, O, η]**⟩  
* Q, I, δ, q<sub>0</sub>, F **[, O]** come nell’FSA **[traduttore]**  
* Γ alfabeto di pila (per comodità, disgiunto da I,**[, O]**)  
* Z0 ∈ Γ simbolo iniziale di pila  
* δ:Q×(I∪{ε})×Γ→Q×Γ<sup>∗</sup> (n.b. δ è parziale)  
* **η:Q×(I∪{ε})×Γ→O<sup>∗</sup>** (η è definita solo dove lo è δ)  

### Generalizzare lo stato  

**Il concetto di configurazione**  

Catturare lo stato di un automa a pila (AP o PDA *Push down automata*) richiede giustamente più informazioni rispetto ad un FSA. 
Chiamiamo lo stato di un AP *configurazione* c = ⟨q, x, γ, **[z]**⟩; q è lo stato dell'organo di controllo, x la stringa ancora da leggere, γ la stringa dei caratteri in pila (la prima cresce da destra verso sinistra) e z è la stringa scritta in output. 

**Transizione tra configurazioni**  

Transizione di un AP: c ⊢ c′ : ⟨q, x, γ, **[z]**⟩ ⊢ ⟨q′, x′, γ′, **[z′]**) 
Per chiarezza abbiamo γ = βA, definiamo, a seconda dei casi:  
* **Lettura effettiva**: con x = i.y e δ(q, i, A) = ⟨q′, α⟩ (definita, non ⊥)  
**[η(q,i,A) = w]** abbiamo x′ = y, γ′ = βα, **[z′ = z.w]**  
* **ε-Lettura**: con x = y e δ(q,ε,A) = ⟨q′,α⟩ (definita, non ⊥) **[η(q,ε,A) = w]**  
abbiamo x′ =y,γ′ =βα, **[z′ =z.w]**  

**Accettazione e traduzione**  

Sequenza di mosse: definiamo ⊢<sup>*</sup> come chiusura riflessiva e transitiva di ⊢  
Accettazione e **traduzione** di x ∈ L

x ∈ L **∧ [z = τ(x)]** ⇔ c<sub>0</sub> = ⟨qo,x,Z0, **[ε]**⟩ ⊢<sup>*</sup> cf = ⟨q,ε,γ, **[z]**⟩,q ∈ F  
**NOTA BENE** &rarr; attenzione alle ε mosse, soprattutto a fine stringa!  

### Proprietà degli AP (riconoscitori) 

**Cosa posso riconoscere?**  

Un AP è in grado di riconoscere {a<sup>n</sup>b<sup>n</sup> con n > 0}, {a<sup>n</sup>b<sup>3</sup>n con n > 0}  
Posso riconoscere {a<sup>n</sup>b<sup>n</sup>c<sup>n</sup> con n > 0}?  

* **NO** intuitivamente: dopo aver impilato per contare le a e spilato per contare le b, come conto le c?  
* Per la dimostrazione formale si usa l'estensione del pumping lemma per i linguaggi riconosciuti dagli AP 
* Pumping lemma esteso: Esiste un p ≥ 1 tale per cui, data:  
x=pvcws ∈ L<sub>AP</sub>,|x| ≥ p con |vcw| ≤ p,|vc| ≥ 1 ⇔ ∀n∈N, pv<sup>n</sup>cw<sup>n</sup>s ∈ L<sub>AP</sub>  
* La pila è, per definizione, una memoria distruttiva: per leggere occorre cancellare degli elementi!  

Un AP è in grado di riconoscere sia {a<sup>n</sup>b<sup>n</sup>|n > 0} che {a<sup>n</sup>b<sup>2n</sup>|n > 0}  
Posso riconoscere l'unione tra di essi?  

* **NO** intuitivamente è molto simile a prima. 
* se svuoto la pila per contare le prime n b perdo memoria per contare le successive  
* Se ne svuoto solo metà, e ce ne sono solo n non so se sono a metà pila. 
* Intuitivamente: mi servirebbe “dare un’occhiata” in avanti sull’input, per un numero arbitrariamente grande di caratteri 
* Formalizzazione diversa dal precedente (non banale, diversa dal dalla precedente, serve il double-service lemma). 

### Conseguenze delle proprietà  

**La famiglia L<sub>AP</sub>**  

* L<sub>AP</sub> è la famiglia di linguaggi riconosciuti dagli AP deterministici.
* L<sub>AP</sub> non è chiusa rispetto all'unione (come visto prima) ma è chiusa rispetto al complemento.  
* L<sub>AP</sub> non è chiusa rispetto all'intersezione!  

### Costruire il complemento  

**Difficoltà nella costruzione**  

* La δ dell’automa va completata come per gli FSA con lo stato di errore. 
Le ε mosse possono introdurre non-determinismo. 
* Un ciclo di ε mosse può evitare che l’automa proceda (stringa non accettata, neppure dall’automa con F′ = Q \ F)  
Si può trasformare ogni AP con cicli di ε mosse in uno equivalente privo di essi. 
* Se esiste una sequenza ⟨q<sub>1</sub>, ε, γ<sub>1</sub>⟩ ⊢ ⟨q<sub>2</sub>, ε, γ<sub>2</sub>⟩ ⊢ ⟨q<sub>3</sub>, ε, γ<sub>3</sub>⟩ dove solo q<sub>1</sub>, q<sub>3</sub> ∈ F, ma q<sub>2</sub> non è elemento di F cosa succede?  
Serve “forzare” l’automa ad accettare solo alla fine di una sequenza (necessariamente finita) di ε mosse. 
* Più della tecnica di dimostrazione è importante: per impiegare la macchina che risolve il “problema positivo” anche per risolvere il “complemento” serve essere sicuri che termini

# Macchine di Turing 

## Un modello di calcolo universale  

Gli AP sono decisamente più potenti degli FSA ma presentano ancora grosse limitazioni.  
Esaminiamo ora un modello di calcolo con maggiori capacità...  
* Saremo in grado di effettuare praticamente qualunque calcolo  
* Esamineremo il costo di tale generalità espressiva 

Il modello è la *Macchina di Touring (MT)*. Essa è uno dei primi modelli di calcolo incredibilmente semplici nella loro efficacia.
Esaminiamo ora il funzionamento come riconoscitore e **traduttore**, in seguito le proprietà universali del calcolo automatico. 
Tra le due varianti presenti esamineremo prima la MT a k nastri per semplicità.  

## Modello a K nastri

![macchina di Turing a K nastri](ApiImages/MTaKNastri.png)  

**Componenti**  

* Insieme di stati dell’OC, alfabeto I e **O** come per gli AP. 
* Ogni nastro di memoria può avere un suo alfabeto dedicato o meno: considereremo un unico alfabeto Γ  
* Per convenzione storica e semplicità di formalizzazione, i nastri sono sequenze infinite di celle  
Solo una quantità finita è inizializzata con un valore sensato
Celle restanti contenenti uno spazio vuoto o *blank*
* Le tutte testine possono scorrere sui nastri o rimanere ferme  
* Configurazione di MT: stato dell’OC e contenuto dei nastri  

### Transizione della MT  

**In funzione di...**  

* Lettura del carattere sotto la testina del nastro di input. 
* Lettura dei caratteri sotto le testine dei nastro di memoria. 
* Stato dell’OC. 

**...Azione conseguente**

* Cambiamento di stato dell’OC. 
* Scrittura di un carattere su ogni nastro di memoria. 
* **Scrittura di un carattere sul nastro di uscita**. 
* Spostamento delle testine  
Testine di memoria e ingresso: 1 posizione a sinistra (L), destra (R) o ferme (S). 
Testina di output: solo S o R, se si sposta scrive sempre una lettera o un blank. 

**Riconoscitore e Traduttore**  

Transizione δ : Q × (I ∪ {blank}) × Γ<sup>k</sup> → Q × Γ<sup>k</sup> × {L, S, R}<sup>k+1</sup>  
**Traduzioneη: Q × (I ∪ {blank})×Γ<sup>k</sup> →(O ∪ {blank})**  

**Convenzione grafica**  

 ![Convenzione Grafica](ApiImages/ConvenzioneMT.png)  

* Mossa m<sub>in</sup> ∈ {L, S, R}: testina di input. 
* Nastri da i = 1 a i = k → memoria, mosse m<sub>i</sub> ∈ {L,S,R}  
* **Nastro k + 1 → output, m<sub>k+1</sub> ∈ {S, R}**  

**Configurazione iniziale**  

* Tutti i nastri di memoria pieni di *blank*, tranne nella posizione iniziale della rispettiva testina dove c'è z<sub>0</sub>  
* Per farvi riferimento, la posizione della testina conta da 0  
* Stato iniziale dell'OC pari a q<sub>0</sub>  
* Stringa in ingresso x scritta a partire dalla cella 0 del nastro in ingresso, seguita e proceduta da *blank*  
* **nastro di output riempito con *blank***  

**Configurazione finale e accettazione**  

* Gli stati di accettazione sono come quelli delle FSA &rarr; F ⊆ Q  
* Per comodità (convenzione) la δ, **η** non è definita a partire dagli stati finali :
∀q ∈ F, δ(q,...) = ⊥, **η(q,...) = ⊥**  
* La MT si ferma in uno stato q se δ(q,...) = ⊥  
* La stringa x in ingresso viene accettata se e solo se, con un numero finito di transizioni, la MT si ferma in uno stato tra quelli finali  

**Mancata accettazione**  

una stringa non viene accettata in 2 casi: 
* La MT si ferma in uno stato non finale. 
* La MT non si ferma affatto.  

### Proprietà di chiusura  

**Chiusure valide**  

* **∩** &rarr; La MT simula l'esecuzione di 2 in serie  
* **∪** &rarr; La MT simula l'esecuzione di 2 in parallelo  
* **Concatenazione** &rarr; ragionamento simile a ∩  
* **operazione asterisco** &rarr; vedi concatenazione  

**Chiusure non valide** 

L'unica chiusura non valida per le MT è quella rispetto al complemento  

### Modelli equivalenti alle MT 

**Turing completezza**  

Possiamo costruire dei modelli di calcolo equivalenti alle MT  
* Una MT con un nastro bidimensionale 
* Una MT con k testine per nastro  
* Un AP con due pile (esse messe l'una di fronte all'altra simulano un nastro infinito nel mezzo)  

Idea generale &rarr; Per mostrare che sono equivalenti vengono messi in una corrispondenza biunivoca le transizioni della MT "classica" e quelle del modello di calcolo che stiamo proponendo. 
Se un modello di calcolo è in grado di simulare una macchina di Turing esso viene detto *Turing completo*. 

**MT a nastro singolo** 

Una particolare variazione delle MT "classiche" è la MT a nastro singolo, in essa input, output e memoria si trovano sullo stesso nastro; questo è il modello iniziale proposto da Alan Turing. 
Questa particolare MT è equivalente alle MT a k nastri  

**Differenza con modelli più realistici**  

* Una MT è in grado di simulare il comportamento di una macchina di von Neumann (opportunamente “astratta”, con memoria infinita)  
* La differenza principale è la modalità di accesso alla memoria; una macchina di Von Neumann accede alla memoria attraverso gli indirizzi mentre una MT scorre il nastro opportuno.  
* non c'è alcuna differenza nella capacità espressiva di questi due modelli. 
* Spesso cambiare il modello influisce sulla complessità del calcolo e, di conseguenza, sul tempo e risorse impiegate. 

# Non determinismo  

## Modelli deterministici e non deterministici a confronto  

Nella maggior parte dei casi un algoritmo è una *sequenza deterministica* di passi perchè, dato uno stato della computazione e un input, il passo successivo è unico.  
Detto ciò, non sempre l'ordine dei passi è fondamentale.  

**La comodità del non determinismo**  

Una descrizione di un algoritmo non deterministico è solitamente più compatta, inoltre per la realizzazione pratica si possono sfruttare più esecutori.  
Simmetricamente, un modello di esecuzione non deterministico può essere utile come semantica del calcolo in parallelo.  

## Versioni non deterministiche dei modelli noti  

### Automi a stati finiti non deterministici  

 ![FSA non deterministico](ApiImages/FSAnonDet.png)  
 
 La δ diventa δ : Q × I &rarr; ℘(Q)  
 
 Questo FSA effettua tutte le computazioni possibili, se almeno una di essa termina in uno stato finale la stringa viene accettata.
 **NOTA BENE** &rarr; un FSA non deterministico può avere più di un solo stato finale (ma sempre un solo stato iniziale).  
 
Posso sempre costruire un automa a stati finiti deterministico partendo dal suo equivalente non deterministico. (processo decisamente ostico se ci va male in quanto gli stati di un automa deterministico possono essere alla peggio 2<sup>stati del non deterministico</sup>.  
 
A differenza di quanto si possa pensare gli FSA non deterministici non hanno un potere espressivo maggiore rispetto alle loro controparti deterministiche.  

**Comodità di specifica**  

Sapendo che gli FSA non deterministici e deterministici hanno lo stesso potere espressivo, perchè mai dovremmo mantenere l'utilizzo di quelli non deterministici?  
Può essere comodo specificare un FSA non deterministico per poi ricavare quello deterministico, senza avere il compito di concepire da 0 quello deterministco.  

### Automi a pila non deterministici  

Gli automi a pila, a differenza di quelli a stati finiti, sono *naturalmente* non deterministici, basta semplicemente eliminare la restrizione imposta fino ad ora.  

 ![AP non deterministici](ApiImages/APnonDet.png)  
 
 Otteniamo la δ<sub>AP-ND</sub> :Q × (I ∪ {ε}) × Γ → ℘<sub>F</sub>(Q × Γ<sup>∗</sup>)  
 L’AP non deterministico accetta x se esiste una sequenza c<sub>0</sub> ⊢<sup>*</sup> {c1, . . . cn} con c<sub>0</sub> = ⟨q<sub>0</sub>, x, Z<sub>0</sub>⟩, c<sub>1</sub> = ⟨q, ε, γ⟩, q ∈ F

**Esempio di riconoscitore**  

 ![AP non deterministico riconoscitore](ApiImages/APriconoscitoreND.png)  
 
 
L’automa precedente è in grado di riconoscere {a<sup>n</sup>b<sup>n</sup>} ∪ {a<sup>n</sup>b<sup>2n</sup>}  
Gli automi a pila non deterministici sono più potenti di quelli deterministici. 
Osservando l'immagine sopra si può notare come gli automi a pila non deterministici siano chiusi rispetto all'unione (a differenza di quelli deterministici)  
Essi però non sono chiusi rispetto all'intersezione e, di conseguenza, nemmeno rispetto al complemento.  

### Macchine di turing non deterministiche  

**Definizione e caratteristiche**  

δ : Q × I × Γ<sup>k</sup> → ℘(Q × Γ<sup>k</sup> × {L, S, R}) (perchè ℘ e non ℘<sub>F</sub> ?)  
Configurazione, transizione, sequenza di transizioni e accettazione definite come negli altri casi. 

![Esempio di computazione di una MT non deterministica](ApiImages/ComputazioneMTND.png) 
 
* Computazione in verde &rarr; accettante.  
* Computazione in rosso &rarr; non accettante.  

**Emulare una MT non deterministica con una deterministica**  

x è accettata da una MT ND solo se esiste un calcolo che termina in uno stato di accettazione.  
*Come posso emulare una MT ND con una MT D?*  
* Percorrere l’albero delle computazioni ND per stabilire se esiste un percorso che termina in uno stato di accettazione.  
* Nel caso di un albero “normale”, esistono algoritmi consolidati per effettuare questa visita.  

*Come gestisco le computazioni che non terminano?*  
* Visita dell’albero “in ampiezza”.  
* Costruisco una MT D che scandisce le configurazioni della ND a partire dalle più vicine a c<sub>0</sub>  
* Intuitivamente: se la MT ND termina, termina anche la mia MT D con lo stesso esito. 

## Considerazioni finali sul non determinismo  

**Un utile formalismo**  

* Utile per rappresentare problemi/algoritmi dove alcune scelte locali non sono fattibili al momento/importanti.  
* Aumenta la potenza dei soli AP (tra i formalismi visti). 
* Può essere applicato praticamente a tutti i modelli di calcolo (estensione facile ai traduttori). 

# Le Grammatiche  

I modelli di calcolo visti fino ad ora sono in grado di riconoscere se una stringa appartiene ad un dato linguaggio.  
Vediamo ora però un modello *generativo* del linguaggio &rarr; la grammatica. 
In generale, una grammatica (sintassi) è un insieme finito di regole che definiscono le frasi di un linguaggio. 

## Riscritture per raffinamenti successivi  

* Le regole di una grammatica descrivono un “oggetto principale” (libro, protocollo, messaggio grafico) come un insieme ordinato di “componenti”. 
* La descrizione è fornita fino ad arrivare al livello di dettaglio desiderato (carattere, bit, forma geometrica elementare). 
* Ogni passo di riscrittura può offrire una o più alternative.  
* Spesso si tende a chiamare lessico la descrizione grammaticale delle singole “parole”, sintassi quella della loro composizione. 

### Definizione formale 

Una grammatica è una quadrupla G = ⟨V<sub>t</sub>, V<sub>n</sub>, P, S⟩  
* V<sub>t</sub> &rarr; Alfabeto o Vocabolario *terminale*. 
* V<sub>n</sub> &rarr; Alfabeto o Vocabolario *nonterminale*.  
* v<sub>t</sub> ∪ v<sub>n</sub> = V &rarr; Vocabolario o Alfabeto.  
* S ∈ V<sub>n</sub> &rarr; Elemento di V<sub>n</sub> detto *assioma* o *simbolo iniziale*.  
* P ⊆ V<sub>n</sub><sup>+</sup> × V<sup>∗</sup> &rarr; Insieme delle produzioni sintattiche o regole di scrittura.  

### La relazione di derivazione 

Definiamo la relazione di derivazione immediata ⇒<sub>G</sub> per una grammatica G = ⟨V<sub>t</sub>, V<sub>n</sub>, P, S⟩ come α ⇒<sub>G</sub> β se e solo se G
α ∈ V<sup>+</sup>, β ∈ V<sup>∗</sup>, α = α<sub>1</sub>α<sub>2</sub>α<sub>3</sub>, β = α<sub>1</sub>β<sub>2</sub>α<sub>3</sub>, α<sub>2</sub> → β<sub>2</sub> ∈ P    
Dove non ambiguo, ometteremo il pedice G dove esso indica la grammatica usata.  
Definiamo ⇒<sup>∗</sup> come la chiusura riflessiva e transitiva di ⇒  
Il linguaggio L(G) generato dalla grammatica G è l’ insieme di tutte e sole le stringhe x di soli caratteri di V<sub>t</sub> tali che S ⇒<sup>∗</sup> x.  

### Usi pratici delle grammatiche  

Le grammatiche sono ampiamente usate come modello descrittivo dei linguaggi di programmazione e di descrizione dati; possono anche essere usate come generatrici di input di test per dei programmi.  

## Espressività delle grammatiche  

### Quali linguaggi è possibile esprimere?  

Come abbiamo visto è possibilie utilizzare delle grammatiche per generare dei linguaggi riconosciuti da un automa a potenza minima.  
Possiamo ora vedere come è possibile classificare le grammatiche in base al loro potere generativo, ovvero in base alla famiglia di appartenenza del linguaggio generato.  
La gerarchia classica proposta da Chomsky prevede 4 classi, a seconda delle limitazioni (crescenti) imposte sulla forma delle produzioni α → β  

![Gerarchia delle grammatiche di Chomsky](ApiImages/GerarchiaGrammatiche.png)  

### A quali automi corrispondono?  

**Linguaggi generati da grammatiche regolari ≡ riconosciuti da FSA**  

Dall’FSA *A* alla grammatica:  

* Poniamo V<sub>n</sub> = Q, V<sub>t</sub> = I, S = ⟨q0⟩  
* Per ogni δ(q, i) = q′ aggiungiamo ⟨q⟩ → i⟨q′⟩ all’insieme P  
* Se q′ ∈ F per una data δ(q, i) = q′, aggiungiamo anche ⟨q⟩ → i all’insieme P  
* Facile mostrare per induzione che δ<sup>∗</sup>(q0, x) = q′ sse ⟨q0⟩ ⇒<sup>∗</sup> x⟨q′⟩  

Dalla grammatica all'FSA (non deterministico):  

* Q = V<sub>n</sub> ∪{q<sub>f</sub>}, I = V<sub>t</sub>, q<sub>0</sub> = S, F = {q<sub>f</sub>}  
* Se A → bC ∈ P, δ(A,b) = C; Se A → b ∈ P, δ(A,b) = q<sub>f</sub>  

**Grammatiche libere dal contesto e AP non deterministici**  

I linguaggi generati da grammatiche libere dal contesto vengono riconosciuti da automi a pila non deterministici.  
*Di seguito è presente un esempio illustrativo* 

Data ⟨{S},{a,b}, {S → aSb,S → ab},S⟩...  

![Da grammatica ad APND](ApiImages/DaGrammaticaAdAP.png)  

**Grammatiche non limitate e Macchine di Turing**  

Le grammatiche di tipo 0 (non limitate) corrispondono alle MT.  
Costruiamo, senza pretesa di formalizzazione qui, una MT non deterministica che accetti L(G):  
* *M* ha un nastro di memoria inizializzato con Z<sub>0</sub>S  
* La stringa da riconoscere è sul nastro in ingresso  
* Il nastro di memoria viene scandito alla ricerca di una parte sinistra di una qualche produzione p ∈ P  
* Quando una viene trovata (scelta nondeterministicamente), viene sostituita con la sua parte destra  
* Se ve n'è più di una, si opera ancora nondeterministicamente  

**Emulare una macchina di Turing con una grammatica non ristretta**  

Senza perdere di generalità emuliamo una MT *M* a nastro singolo con una grammatica G non ristretta.  

Considerato che G può “manipolare” solo elementi di V<sub>n</sub>, faccio in modo che generi stringhe della forma x&X con & ∈ Vn, x ∈ V<sub>t</sub><sup>∗</sup> e X che è costituita da “copie nonterminali” degli elementi di X.  
*Ad esempio, se x = abac, genero la stringa abac&ABAC*.   
**Obiettivo:** avere una derivazione x&X &rarr;<sup>*</sup> x se e solo se x è accettata da *M*  
Simuleremo ogni mossa di *M* con una derivazione diretta di G 

### Corrispondenze mancanti  

**Automi a pila deterministici**  

Esiste un sottoinsieme (proprio) delle grammatiche libere dal contesto che genera i linguaggi riconosciuti dagli automi a pila deterministici.  

**Grammatiche dipendenti dal contesto**  

Le grammatiche di tipo 1 corrispondono ad un sottoinsieme delle Macchine di Turing di cui si è certi sempre della loro terminazione.  
**NOTA BENE** &rarr; non sono le uniche macchine di Turing che terminano sempre!  
Consentono sempre di sapere se una stringa x è generata da G (si può costruire l’insieme delle stringhe generate da G lunghe quanto x e vedere se essa appare). 

# La teoria della computazione  

Una delle domande più importanti che si potremo porre in questo corso è *Siamo in grado di risolvere questo problema?* 
Ma prima di ciò, quali problemi siamo in grado di risolvere? (con un certo formalismo e in assoluto)  
Bhe...chiederlo in termini assoluti appare molto generale  
* Cosa intendiamo per problema?  
* Quante e quali macchine dobbiamo considerare per rispondere "in assoluto"?  
* Come astraiamo dalla specifica abilità del solutore?  
* E dai mezzi impiegati per risolvere il problema?  

## Una prima inquadratura  

**Come formalizzare un "problema informatico"?**  

Abbiamo formalizzato un *problema informatico* usando il concetto di **linguaggio**.  
* Formuliamo un calcolo come il problema di capire se x ∈ L o di calcolare y = τ(x)  
* Queste due formulazioni possono essere unificate riconducendo una all’altra  
So calcolare y = τ(x), voglio risolvere x ∈ L: definisco τ(x) = 1 ⇔ x ∈ L e τ(x) = 0 ⇔ x &notin; L  
M risolve x ∈ L: definisco Lτ = {x‡y|y = τ(x)}, poi per tutte le possibili stringhe y chiedo a M se x‡y ∈ Lτ . Se τ (x) è definita, prima o poi la macchina risponderà positivamente (probabilmente più poi che prima, ma per ora non ci interessa l’efficienza).  

* Esistono moltissimi formalismi di calcolo, moltissimi altri possono essere inventati: quale scegliere?  
A seconda della scelta, ottengo risultati come: “a<sup>n</sup>b<sup>n</sup>|n > 0 è riconosciuto da un AP e una MT ma non da un FSA”. 
* Riflettendo sulla MT si nota come non sia facile costruire un meccanismo con capacità di calcolo maggiori (=che risolva più problemi)  

## La Macchina di Turing è tutto ciò che ci serve  

* Nel 1933 G ̈odel e Herbrandt individuano un insieme di funzioni sugli interi che appaiono definire ci`o che pu`o essere calcolato “a mano, con carta e penna”. 
* Nel 1936, Alonso Church definisce un altro sistema basato su funzioni ricorsive, il λ-calcolo, anch’esso in grado di descrivere tutte le funzioni “calcolabili operativamente”. 
* Nel 1936 Turing definisce quella che è la MT a nastro singolo sempre nell’intento di fornire un formalismo per rappresentare tutto ciò che è “effettivamente calcolabile”.  
* Turing e Church dimostrano che i tre formalismi citati sono equivalenti: definiscono lo stesso insieme di problemi. 
* **Tesi di Church-Turing** &rarr; Tutti i problemi calcolabili operativamente sono descritti da una MT!  

**NOTA BENE** &rarr; Per il resto delle slide su computabilità e decidibilità guardare sito del prof Barenghi.  

# La complessità del calcolo

## Quanto efficientemente risolviamo un problema?

Posto che un problema sia calcolabile ci possiamo domandare "*a che costo?*"  

Effettueremo analisi **quantitative** di:  
* Tempo impegato. 
* Spazio occupato. 

## Dipendenza dal formalismo di calcolo  

Per la tesi di Church-Turing, un problema è calcolabile o meno indipendentemente dallo strumento usato.  
Possiamo dire lo stesso della complessità di calcolo?  

* Una somma in unario ha efficienza diversa da una base B > 1  
* Calcolare una traduzione y = τ(x) decidendo se ∃z ∈ Lτ = {x†y|y = τ(x)} può essere molto meno efficiente del calcolare la traduzione.  

### Costo di calcolo "indipendente" dal formalismo  

Non disponiamo di una tesi di Church-Turing della complessità. 
Ci serve uno strumento per calcolare la complessità spaziale e temporale:  
* Che tralasci "considerazioni superflue"  
* Utilizzabile per la maggioranza dei modelli di calcolo  

Non avendo un formalismo di calcolo “preferito” per costruire il modello, partiamo dalle MT deterministiche. 
* Almeno una MT per conservare le capacità espressive. 
* Una MT deterministica perchè non possiamo costruire fisicamente una non deterministica  

## Complessità temporale  

Data la computazione c<sub>0</sub>⊢<sup>*</sup>c<sub>r</sub> di M la complessità temporale è TM(x) = r se M si ferma in un dato c<sub>r</sub>, ∞ altrimenti. 
M è deterministica ⇒ computazione unica sull’ingresso x. 

## Complessità spaziale  















 

 




























