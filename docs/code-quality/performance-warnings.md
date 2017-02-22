---
title: "Avvisi di prestazioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.performancerules"
helpviewer_keywords: 
  - "avvisi, prestazioni"
  - "avvisi di prestazioni"
  - "prestazioni, avvisi"
  - "avvisi dell'analisi codice gestito, prestazioni"
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avvisi di prestazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli avvisi di prestazioni supportano librerie e applicazioni a elevate prestazioni.  
  
## In questa sezione  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[CA1800: Non eseguire il cast inutilmente](../code-quality/ca1800-do-not-cast-unnecessarily.md)|I cast duplicati comportano una riduzione delle prestazioni, in particolare quando i cast vengono eseguiti in istruzioni di iterazione compatte.|  
|[CA1801: Rivedere i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)|Una firma di metodo include un parametro non utilizzato nel corpo del metodo.|  
|[CA1802: Utilizza valori letterali dove appropriato](../code-quality/ca1802-use-literals-where-appropriate.md)|Un campo viene dichiarato static e read\-only \(Shared e ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) e viene inizializzato con un valore calcolabile in fase di compilazione.  Dal momento che il valore assegnato al campo di destinazione è calcolabile in fase di compilazione, modificare la dichiarazione in un campo const \(Const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) in modo che il calcolo del valore venga effettuato in fase di compilazione anziché in fase di esecuzione.|  
|[CA1804: rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)|Le variabili locali inutilizzate e le assegnazioni non necessarie comportano un aumento delle dimensioni dell'assembly e una riduzione delle prestazioni.|  
|[CA1806: Non ignorare i risultati dei metodi](../code-quality/ca1806-do-not-ignore-method-results.md)|Un nuovo oggetto viene creato ma non viene mai utilizzato oppure viene chiamato un metodo che crea e restituisce una nuova stringa e la nuova stringa non viene mai utilizzata oppure un metodo Component Object Mode \(COM\) o P\/Invoke restituisce un HRESULT o un codice di errore che non viene mai utilizzato.|  
|[CA1809: Evitare un numero eccessivo di variabili locali](../code-quality/ca1809-avoid-excessive-locals.md)|Un'ottimizzazione comune delle prestazioni consiste nell'archiviare un valore in un registro del processore anziché in memoria. Tale procedura è definita "registrazione del valore".  Per aumentare la possibilità di registrazione di tutte le variabili locali, limitare il numero di tali variabili a 64.|  
|[CA1810: Inizializzare i campi statici del tipo di riferimento inline](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Quando un tipo dichiara un costruttore statico esplicito, tramite il compilatore JIT \(Just\-In\-Time\) viene aggiunto un controllo a ogni metodo statico del tipo e a ogni costruttore di istanza del tipo per assicurare che il costruttore statico sia stato precedentemente chiamato.  I controlli dei costruttori statici possono ridurre le prestazioni.|  
|[CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)|Un membro privato o interno \(a livello di assembly\) non presenta chiamanti nell'assembly, non viene richiamato da Common Language Runtime e non viene richiamato da un delegato.|  
|[CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Un'istanza di un tipo a livello di assembly non viene creata dal codice nell'assembly.|  
|[CA1813: Evitare attributi non sealed](../code-quality/ca1813-avoid-unsealed-attributes.md)|La libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fornisce metodi per recuperare attributi personalizzati.  Per impostazione predefinita, questi metodi eseguono ricerche nella gerarchia di ereditarietà dell'attributo.  L'utilizzo di attributi sealed elimina la ricerca nella gerarchia di ereditarietà e può migliorare le prestazioni.|  
|[CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Una matrice di matrici è una matrice i cui elementi sono costituiti da matrici.  Poiché le matrici che costituiscono gli elementi possono presentare dimensioni diverse, la quantità di spazio inutilizzato sarà inferiore per alcuni insiemi di dati.|  
|[CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Per i tipi di valore, l'implementazione ereditata di Equals utilizza la libreria Reflection e confronta il contenuto di tutti i campi.  La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo.  Se si prevede che gli utenti confrontino o ordinino le istanze oppure le utilizzino come chiavi di tabelle hash, il tipo di valore deve implementare Equals.|  
|[CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Un metodo che costituisce un'implementazione di Dispose non chiama GC.SuppressFinalize oppure un metodo che non costituisce un'implementazione di Dispose chiama GC.SuppressFinalize oppure un metodo chiama GC.SuppressFinalize e passa un elemento diverso da this \(Me in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).|  
|[CA1819: Le proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md)|Le matrici restituite dalle proprietà non sono protette in scrittura, anche se la proprietà è in sola lettura.  Affinché la matrice sia protetta da eventuali alterazioni, la proprietà deve restituire una copia della matrice.  In genere, gli utenti non comprendono le implicazioni negative sulle prestazioni derivanti dalla chiamata di tale proprietà.|  
|[CA1820: Testare le stringhe vuote utilizzando la lunghezza di stringa](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Il confronto tra stringhe mediante la proprietà String.Length o il metodo String.IsNullOrEmpty è notevolmente più veloce rispetto all'utilizzo di Equals.|  
|[CA1821: Rimuovere i finalizzatori vuoti](../code-quality/ca1821-remove-empty-finalizers.md)|Quando possibile, evitare di utilizzare i finalizzatori per non sovraccaricare ulteriormente le prestazioni durante il rilevamento della durata dell'oggetto.  Un finalizzatore vuoto provoca un sovraccarico aggiuntivo senza alcun vantaggio.|  
|[CA1822: Contrassegna i membri come statici](../code-quality/ca1822-mark-members-as-static.md)|I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static \(Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri.  Si potrà così ottenere un sensibile miglioramento delle prestazioni per codici sensibili alle prestazioni.|  
|[CA1823: Evitare campi privati non utilizzati](../code-quality/ca1823-avoid-unused-private-fields.md)|Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly.|  
|[CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|L'attributo NeutralResourcesLanguage indica a ResourceManager la lingua utilizzata per visualizzare le risorse delle impostazioni cultura non associate ad alcun paese per un assembly.  Tale approccio migliora le prestazioni delle ricerche per la prima risorsa caricata e riduce il working set.|