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
* **NOTA BENE:** anche se |A| < ∞, non necessariamente si avrà che |L| < ∞ (vedi ultimo esempio).

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
* Per estensione &rarr; L<sup>*</sup> = U<sup>∞</sup><sub>n=0</sub>  L<sup>n</sup>, L<sup>+</sup> = U<sup>∞</sup><sub>n=1</sub>  L<sup>n</sup>,
                   
 
                   
 





