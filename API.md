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
* {a,b,c,d,....,z}
* {0,1}
* Codice Morse, Baudot, ASCII ecc.

**Stringa di un alfabeto arbitrario A**

Una stringa è una sequenza ordinata e finita di elementi dell'alfabeto.
La lunghezza di una stringa è, come ci si può immaginare, il numero di caratteri che la compongono &rarr; |a| = 1, |stringa| = 7.  
Inoltre, a prescindere dall'alfabeto utilizzato, è presente anche la stringa nulla **ε** &rarr; |ε| = 0.  
A* è invece l'insieme di tutte le stringhe (incluse quella nulla) su A.
 * *Esempio:* A = {0,1}, A* = {ε,0,1,00,01,10,11,100...}

**Operazioni sulle stringhe**


