---
title: "Asserzioni C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "_DEBUG (macro)"
  - "ASSERT (macro)"
  - "Asserzione non riuscita (finestra di dialogo)"
  - "asserzioni"
  - "asserzioni, effetti collaterali"
  - "Stack di chiamate (finestra), asserzioni non riuscite"
  - "debug [C++], asserzioni"
  - "debug [MFC], asserzioni"
  - "errori [C++], intercettazione con asserzioni"
  - "errori, ricerca di percorsi"
  - "controllo risultati"
  - "risultati, controllo"
  - "test, condizioni di errore con istruzioni di asserzione"
  - "VERIFY (macro)"
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Asserzioni C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un'istruzione di asserzione specifica una condizione che si prevede di essere vera in un punto del programma.  Se tale condizione non è true, l'asserzione non riesce, viene interrotta l'esecuzione del programma e la  [finestra di dialogo Asserzione non riuscita](../debugger/assertion-failed-dialog-box.md) viene visualizzato.  
  
 Visual C\+\+ supporta le istruzioni di asserzione sono basate sui seguenti costrutti:  
  
-   Asserzioni MFC per programmi MFC.  
  
-   [ATLASSERT](../Topic/ATLASSERT.md) per programmi che utilizzano ATL.  
  
-   Asserzioni CRT per programmi che utilizzano la libreria di runtime C.  
  
-   L'ANSI  [funzione di asserzione](/visual-cpp/c-runtime-library/reference/assert-macro-assert-wassert) per altri programmi C\/C\+\+.  
  
 È possibile utilizzare asserzioni per rilevare errori logici, controllare i risultati di un'operazione e verificare le condizioni di errore che avrebbero dovuto essere gestite.  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 [Funzionano delle asserzioni](#BKMK_How_assertions_work)  
  
 [Asserzioni in compilazioni di Debug e di rilascio](#BKMK_Assertions_in_Debug_and_Release_builds)  
  
 [Effetti collaterali di utilizzo di asserzioni](#BKMK_Side_effects_of_using_assertions)  
  
 [Asserzioni CRT](#BKMK_CRT_assertions)  
  
 [Asserzioni MFC](#BKMK_MFC_assertions)  
  
-   [ASSERT_VALID e CObject:: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  
  
-   [Limitazioni di AssertValid](#BKMK_Limitations_of_AssertValid)  
  
 [Utilizzo di asserzioni](#BKMK_Using_assertions)  
  
-   [Rilevamento di errori logici](#BKMK_Catching_logic_errors)  
  
-   [Controllo dei risultati](#BKMK_Checking_results_)  
  
-   [Non gestito di individuazione degli errori](#BKMK_Testing_error_conditions_)  
  
##  <a name="BKMK_How_assertions_work"></a> Funzionano delle asserzioni  
 Quando il debugger si interrompe a causa di un'asserzione di libreria di runtime C o MFC, quindi se l'origine è disponibile, il debugger passa al punto in cui si è verificata l'asserzione del file di origine.  Viene visualizzato il messaggio di asserzione in entrambe le  [finestra di Output](../ide/reference/output-window.md) e il  **Asserzione non riuscita** nella finestra di dialogo.  È possibile copiare il messaggio di asserzione dalla  **Output** finestra in una finestra di testo se si desidera salvarlo per riferimento futuro.  Il  **Output** finestra può contenere anche altri messaggi di errore.  Esaminare questi messaggi attentamente, poiché forniscono indizi sulla causa dell'errore di asserzione.  
  
 Utilizzare asserzioni per rilevare errori durante lo sviluppo.  Come regola generale, utilizzare un'asserzione per ciascun presupposto.  Ad esempio, se si presuppone che un argomento non è NULL, utilizzare un'asserzione per verificare tale presupposto.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Asserzioni in compilazioni di Debug e di rilascio  
 Le istruzioni di asserzione vengono compilate solo se  `_DEBUG`è definito.  In caso contrario, il compilatore gestisce le asserzioni alla stregua di istruzioni nulle.  Pertanto, le istruzioni di asserzione non impongano alcun sovraccarico o prestazioni di costo nella versione finale del programma e consentono di evitare l'utilizzo di  `#ifdef`direttive.  
  
##  <a name="BKMK_Side_effects_of_using_assertions"></a> Effetti collaterali di utilizzo di asserzioni  
 Quando si aggiungono asserzioni al codice, assicurarsi che le asserzioni non abbiano effetti collaterali.  Ad esempio, si consideri la seguente asserzione che modifica la  `nM`valore:  
  
```  
ASSERT(nM++ > 0); // Don't do this!  
  
```  
  
 Poiché la  `ASSERT`nella versione di rilascio del programma, non viene valutata l'espressione  `nM`presenterà valori differenti nelle versioni di Debug e Release.  Per evitare questo problema in MFC, è possibile utilizzare il  [verifica](../Topic/VERIFY.md) macro invece di  `ASSERT`.   `VERIFY`valuta l'espressione in tutte le versioni, ma non controlla il risultato nella versione di rilascio.  
  
 Prestare particolare attenzione sull'utilizzo di chiamate di funzione nelle istruzioni di asserzione, poiché la valutazione di una funzione può avere effetti collaterali imprevisti.  
  
```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  
  
 `VERIFY`chiamate  `myFnctn`nelle versioni di Debug e di rilascio, pertanto è possibile utilizzare.  Tuttavia, l'utilizzo di  `VERIFY`impone il sovraccarico di una chiamata di funzione non necessari nella versione di rilascio.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_CRT_assertions"></a> Asserzioni CRT  
 Il CRTDBG.H definisce le  [Assert e ASSERTE](/visual-cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) per il controllo delle asserzioni.  
  
|Macro|Risultato|  
|-----------|---------------|  
|`_ASSERT`|Se l'espressione specificata restituisce FALSE, il file nome e numero di riga del  `_ASSERT`.|`_ASSERTE`|  
|`_ASSERTE`|Come  `_ASSERT`, oltre a una rappresentazione di stringa dell'espressione asserita.|  
  
 `_ASSERTE`è più potente perché riporta l'espressione asserita che è risultato per essere FALSE.  Ciò può essere sufficiente per identificare il problema senza fare riferimento al codice sorgente.  La versione di Debug dell'applicazione conterrà tuttavia una costante stringa per ciascuna espressione asserita mediante  `_ASSERTE`.  Se si utilizzano numerose  `_ASSERTE`delle macro, queste espressioni stringa richiederanno una notevole quantità di memoria.  Se questo costituisce un problema, utilizzare  `_ASSERT`per risparmiare memoria.  
  
 Quando  `_DEBUG`è definito, il  `_ASSERTE`macro viene definita come segue:  
  
```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  
  
 Se l'espressione asserita ha valore FALSE,  [CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) viene chiamato per segnalare il fallimento dell'asserzione \(utilizzando una finestra di dialogo di messaggio per impostazione predefinita\).  Se si sceglie  **Riprova** nella finestra di dialogo di messaggio,  `_CrtDbgReport`restituisce 1 e  `_CrtDbgBreak`chiamerà il debugger tramite   `DebugBreak`.  
  
### Verifica il danneggiamento dell'Heap  
 Nell'esempio seguente viene utilizzato  [CrtCheckMemory](/visual-cpp/c-runtime-library/reference/crtcheckmemory) per verificare la presenza di danneggiamento dell'heap:  
  
```  
_ASSERTE(_CrtCheckMemory());  
```  
  
### Verifica la validità del puntatore  
 Nell'esempio seguente viene utilizzato  [CrtIsValidPointer](/visual-cpp/c-runtime-library/reference/crtisvalidpointer) per verificare che un determinato intervallo di memoria sia valido per la lettura o scrittura.  
  
```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  
  
 Nell'esempio seguente viene utilizzato  [CrtIsValidHeapPointer](/visual-cpp/c-runtime-library/reference/crtisvalidheappointer) per verificare un puntatore punti a memoria nell'heap locale \(heap creato e gestito da questa istanza della libreria di runtime C, ovvero una DLL può avere la propria istanza di libreria e di conseguenza, un heap specifico, di fuori dell'heap dell'applicazione\).  Questa asserzione rileva non solo gli indirizzi nulli o, ma anche i puntatori a variabili statiche, variabili di stack e altre locazioni di memoria.  
  
```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  
  
### Verifica di un blocco di memoria  
 Nell'esempio seguente viene utilizzato  [CrtIsMemoryBlock](/visual-cpp/c-runtime-library/reference/crtismemoryblock) per verificare che un blocco di memoria è nell'heap locale e presenta un tipo di blocco valido.  
  
```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_MFC_assertions"></a> Asserzioni MFC  
 MFC definisce la  [ASSERT](../Topic/ASSERT%20\(MFC\).md) macro per il controllo delle asserzioni.  Definisce inoltre il  `MFC ASSERT_VALID`e  `CObject::AssertValid`metodi per il controllo dello stato interno di un   `CObject`\-oggetto derivato.  
  
 Se l'argomento di MFC  `ASSERT`macro restituisce zero o false, la macro interrompe l'esecuzione del programma e avvisa l'utente; in caso contrario, l'esecuzione continua.  
  
 Quando un errore di asserzione, una finestra di dialogo di messaggio viene visualizzato il nome del file di origine e il numero di riga dell'asserzione.  Se si sceglie Riprova nella finestra di dialogo casella, una chiamata a  [AfxDebugBreak](../Topic/AfxDebugBreak%20\(MFC\).md) , l'esecuzione al debugger.  A questo punto, è possibile esaminare lo stack di chiamate e utilizzare altre utilità del debugger per determinare il motivo per cui l'asserzione non riuscita.  Se è stata attivata la  [debug Just\-in\-time](../debugger/just-in-time-debugging-in-visual-studio.md)e il debugger non è già in esecuzione, nella finestra di dialogo potrà avviare il debugger.  
  
 Nell'esempio riportato di seguito viene illustrato come utilizzare  `ASSERT`per controllare il valore restituito di una funzione:  
  
```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  
  
 È possibile utilizzare ASSERT con la  [IsKindOf](../Topic/CObject::IsKindOf.md) funzione di fornire gli argomenti della funzione di controllo dei tipi:  
  
```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  
  
 Il  `ASSERT`macro non produce codice nella versione di rilascio.  Se è necessario valutare l'espressione nella versione di rilascio, utilizzare il  [verifica](../Topic/VERIFY.md) macro anziché ASSERT.  
  
###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> ASSERT\_VALID e CObject:: AssertValid  
 Il  [CObject:: AssertValid](../Topic/CObject::AssertValid.md) metodo fornisce controlli di runtime dello stato interno di un oggetto.  Sebbene non sia necessario eseguire l'override di  `AssertValid`quando si deriva una classe da   `CObject`, è possibile rendere la classe più affidabile in questo modo.  `AssertValid`deve eseguire asserzioni su tutte le variabili di membro dell'oggetto per verificare che contengano valori validi.  Ad esempio, è necessario verificare che le variabili membro del puntatore non sono NULL.  
  
 Nell'esempio riportato di seguito viene illustrato come dichiarare un  `AssertValid`funzione:  
  
```  
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  
  
```  
  
 Quando esegue l'override  `AssertValid`, chiamare la versione della classe base di  `AssertValid`prima di eseguire i controlli.  Utilizzare quindi la macro ASSERT per controllare i membri unicamente alla classe derivata, come illustrato di seguito:  
  
```  
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  
  
    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  
  
```  
  
 Se una delle variabili membro memorizza oggetti, è possibile utilizzare il  `ASSERT_VALID`macro per verificarne la validità interna \(se esegue l'override delle classi   `AssertValid`\).  
  
 Ad esempio, si consideri una classe  `CMyData`, gli archivi che un   [CObList](/visual-cpp/mfc/reference/coblist-class) in una delle proprie variabili membro.  Il  `CObList`variabile,   `m_DataList`, memorizza un insieme di  `CPerson`oggetti.  Una dichiarazione abbreviata di  `CMyData`si presenta come segue:  
  
```  
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  
  
```  
  
 Il  `AssertValid`eseguire l'override di  `CMyData`si presenta come segue:  
  
```  
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  
  
```  
  
 `CMyData`utilizza il  `AssertValid`meccanismo per verificare la validità degli oggetti memorizzati nel proprio membro dati.  Eseguire l'override  `AssertValid`di  `CMyData`richiama il  `ASSERT_VALID`macro per la propria variabile membro m\_pDataList.  
  
 Verifica della validità non termina a questo livello poiché la classe  `CObList`inoltre eseguito l'override   `AssertValid`.  Questo override esegue un'ulteriore verifica sullo stato interno dell'elenco della validità.  In questo modo, una validità di test su un  `CMyData`oggetto conduce a ulteriori verifiche di validità per gli stati interni dell'oggetto memorizzato  `CObList`oggetto list.  
  
 Con poche operazioni aggiuntive, è possibile aggiungere verifiche di validità per la  `CPerson`gli oggetti memorizzati nell'elenco anche.  È possibile derivare una classe  `CPersonList`da  `CObList`ed eseguire l'override   `AssertValid`.  Nell'override chiama  `CObject::AssertValid`e quindi scorrere l'elenco, chiamata  `AssertValid`in ogni  `CPerson`oggetto archiviato nell'elenco.  Il  `CPerson`esegue l'override di classe illustrata all'inizio di questo argomento già   `AssertValid`.  
  
 Si tratta di un meccanismo potente quando si compila per il debug.  Quando si compila successivamente per il rilascio, il meccanismo viene disattivato automaticamente.  
  
###  <a name="BKMK_Limitations_of_AssertValid"></a> Limitazioni di AssertValid  
 Generazione di un'asserzione indica che l'oggetto non è corretto e l'esecuzione verrà interrotta.  Tuttavia, la mancanza di asserzioni indica solo che è stato rilevato alcun problema, ma l'oggetto potrebbe non essere valida.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_assertions"></a> Utilizzo di asserzioni  
  
###  <a name="BKMK_Catching_logic_errors"></a> Rilevamento di errori logici  
 È possibile impostare un'asserzione su una condizione che deve essere soddisfatto in base alla logica del programma.  L'asserzione non ha alcun effetto a meno che non si verifica un errore logico.  
  
 Si supponga, ad esempio, di molecole di gas in un contenitore e la variabile è una simulazione  `numMols`rappresenta il numero totale delle molecole.  Questo numero non può essere minore di zero, pertanto è possibile includere un'istruzione di asserzione MFC simile al seguente:  
  
```  
ASSERT(numMols >= 0);  
  
```  
  
 In alternativa, è possibile includere un'asserzione CRT come questa:  
  
```  
_ASSERT(numMols >= 0);  
```  
  
 Queste istruzioni non eseguire alcuna operazione se il programma funziona correttamente.  Se a causa di un errore di logica  `numMols` è minore di zero, tuttavia, l'asserzione interromperà l'esecuzione del programma e viene visualizzato il   [Finestra di dialogo Asserzione non riuscita](../debugger/assertion-failed-dialog-box.md).  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Checking_results_"></a> Controllo dei risultati  
 Asserzioni risultano utili per il controllo delle operazioni i cui risultati non sono ovvi a rapidamente.  
  
 Ad esempio, si consideri il codice seguente, che aggiorna la variabile  `iMols`in base al contenuto dell'elenco collegato a cui punta   `mols`:  
  
```  
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  
  
 Il numero di molecole conteggiato da  `iMols`deve essere sempre minore o uguale al numero totale delle molecole,   `numMols`.  Esame visivo del ciclo non mostra che ciò sarà necessariamente il caso, in modo da utilizzata un'istruzione di asserzione dopo il ciclo per verificare tale condizione.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Testing_error_conditions_"></a> Non gestito di individuazione degli errori  
 È possibile utilizzare asserzioni per verificare le condizioni di errore in un punto nel codice in cui qualsiasi errore avrebbero dovuto essere gestite.  Nell'esempio seguente, una routine grafica restituisce un codice di errore oppure zero per il successo.  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* Code to handle errors and  
   reset myErr if successful */  
  
ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  
  
 Se il codice di gestione degli errori funziona correttamente, l'errore dovrebbe essere gestito e  `myErr`Reimposta a zero prima di raggiungere l'asserzione.  Se  `myErr`è un altro valore, l'asserzione avrà esito negativo, il programma verrà interrotto e il  [Finestra di dialogo Asserzione non riuscita](../debugger/assertion-failed-dialog-box.md)viene visualizzato.  
  
 Le istruzioni di asserzione non sono tuttavia un sostituto per codice di gestione degli errori.  Nell'esempio riportato di seguito viene illustrata un'istruzione di asserzione può causare problemi nel codice della versione finale:  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* No Code to handle errors */  
  
ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  
  
 Questo codice si basa sull'istruzione di asserzione per gestire la condizione di errore.  Di conseguenza, qualsiasi codice di errore restituito da  `myGraphRoutine`risulterà non gestito nel codice della versione finale.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md)