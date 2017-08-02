---
title: "Informazioni dettagliate sull&#39;heap di debug CRT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "C++"
helpviewer_keywords: 
  - "_BLOCK_SUBTYPE (macro)"
  - "_BLOCK_TYPE (macro)"
  - "_CLIENT_BLOCK (macro)"
  - "_CRT_BLOCK (macro)"
  - "_crtBreakAlloc (variabile globale)"
  - "_CrtCheckMemory (funzione)"
  - "_CRTDBG_ALLOC_MEM_DF (macro)"
  - "_CRTDBG_CHECK_ALWAYS_DF (macro)"
  - "_CRTDBG_CHECK_CRT_DF (macro)"
  - "_CRTDBG_DELAY_FREE_MEM_DF (macro)"
  - "_CRTDBG_LEAK_CHECK_DF (macro)"
  - "_crtDbgFlag (funzione)"
  - "_CrtDoForAllClientObjects (funzione)"
  - "_CrtDumpMemoryLeaks (funzione)"
  - "_CrtMemBlockHeader (funzione)"
  - "_CrtMemCheckpoint (funzione)"
  - "_CrtMemDifference (funzione)"
  - "_CrtMemDumpAllObjectsSince (funzione)"
  - "_CrtMemDumpStatistics (funzione)"
  - "_CrtMemState (funzione)"
  - "_CrtReportBlockType (funzione)"
  - "_CrtSetBreakAlloc (funzione)"
  - "_CrtSetDbgFlag (funzione)"
  - "_CrtSetDumpClient (funzione)"
  - "_FREE_BLOCK (blocco)"
  - "_IGNORE_BLOCK (blocco)"
  - "_NORMAL_BLOCK (blocco)"
  - "numeri di richieste di allocazione"
  - "blocchi, tipi sull'heap di debug"
  - "blocchi client, specifica dei sottotipi"
  - "crtBreakAlloc (variabile globale)"
  - "DBGINT.H (file)"
  - "compilazioni di debug, collegamento all'heap di debug"
  - "heap di debug"
  - "heap di debug, accesso"
  - "heap di debug, CRT"
  - "heap di debug, blocchi di memoria"
  - "heap di debug, funzioni di creazione di rapporti"
  - "heap di debug, risoluzione dei problemi di allocazione della memoria"
  - "heap di debug, rilevamento di richieste di allocazione di heap"
  - "heap di debug, utilizzo da C++"
  - "debug [C++], supporto di debug CRT"
  - "debug [C++], heap di debug"
  - "debug [CRT], problemi di heap"
  - "debug [Visual Studio], heap di debug"
  - "debug dei problemi di memoria"
  - "delete (operatore), utilizzo dell'heap di debug da C++"
  - "allocazione di heap, debug"
  - "allocazione di heap, richieste di rilevamento"
  - "funzioni heap"
  - "funzioni di creazione di rapporti sullo stato degli heap"
  - "allocazione di memoria, heap di debug"
  - "blocchi di memoria, allocazione di tipi sull'heap di debug"
  - "blocchi di memoria, disponibili"
  - "perdite di memoria, funzioni della libreria di debug CRT"
  - "perdite di memoria, gestione"
  - "memoria, debug"
  - "nBlockUse (metodo)"
  - "new (operatore), utilizzo dell'heap di debug da C++"
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Informazioni dettagliate sull&#39;heap di debug CRT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento vengono fornite informazioni dettagliate sull'heap di debug CRT.  
  
##  <a name="BKMK_Contents"></a> Contenuto  
 [Individuare i sovraccarichi del buffer con l'heap di debug](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Tipi di blocchi sull'heap di debug](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Verificare l'integrità dell'heap e le perdite di memoria](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Configurare l'heap di debug](#BKMK_Configure_the_debug_heap)  
  
 [new, delete e _CLIENT_BLOCK nell'heap di debug C++](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Funzioni per la creazione di report sullo stato dello heap](#BKMK_Heap_State_Reporting_Functions)  
  
 [Rilevare le richieste di allocazione dell'heap](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Individuare i sovraccarichi del buffer con l'heap di debug  
 Due dei problemi più comuni e difficili da gestire che si presentano ai programmatori sono la sovrascrittura della fine di un buffer allocato e la perdita di memoria, ovvero la mancata liberazione delle allocazioni non più necessarie.  L'heap di debug offre strumenti estremamente efficaci per la risoluzione dei problemi di allocazione di memoria di questo tipo.  
  
 Le versioni di debug delle funzioni degli heap chiamano le versioni standard o di base utilizzate nelle build di rilascio.  Quando si richiede un blocco di memoria, il gestore dello heap di debug alloca dall'heap di base un blocco di memoria un poco più grande di quanto richiesto e restituisce un puntatore alla porzione utilizzata di tale blocco.  Si supponga ad esempio che l'applicazione contenga la chiamata: `malloc( 10 )`.  In una build di rilascio [malloc](/visual-cpp/c-runtime-library/reference/malloc) chiamerebbe la routine di allocazione dell'heap di base richiedendo un'allocazione di 10 byte.  Tuttavia, in una build di debug `malloc` chiamerebbe [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg), che chiamerebbe a sua volta la routine di allocazione dell'heap di base richiedendo un'allocazione di 10 byte più 36 byte circa di memoria aggiuntiva.  Tutti i blocchi di memoria generati nell'heap di debug sono connessi in un unico elenco collegato, ordinato in base al momento dell'allocazione.  
  
 La memoria aggiuntiva allocata dalle routine dello heap di debug viene utilizzata per l'archiviazione delle informazioni sulla gestione, per i puntatori che collegano tra loro i blocchi di memoria di debug e per piccoli buffer prima e dopo i dati che hanno la funzione di rilevare eventuali sovrascritture della regione allocata.  
  
 Attualmente la struttura dell'intestazione del blocco utilizzata per memorizzare le informazioni relative alla gestione dell'heap di debug viene dichiarata come segue nel file di intestazione DBGINT.H:  
  
```  
typedef struct _CrtMemBlockHeader  
{  
// Pointer to the block allocated just before this one:  
    struct _CrtMemBlockHeader *pBlockHeaderNext;  
// Pointer to the block allocated just after this one:  
    struct _CrtMemBlockHeader *pBlockHeaderPrev;  
    char *szFileName;    // File name  
    int nLine;           // Line number  
    size_t nDataSize;    // Size of user block  
    int nBlockUse;       // Type of block  
    long lRequest;       // Allocation number  
// Buffer just before (lower than) the user's memory:  
    unsigned char gap[nNoMansLandSize];  
} _CrtMemBlockHeader;  
  
/* In an actual memory block in the debug heap,  
 * this structure is followed by:  
 *   unsigned char data[nDataSize];  
 *   unsigned char anotherGap[nNoMansLandSize];  
 */  
```  
  
 I buffer `NoMansLand` presenti da entrambi i lati dell'area del blocco destinata ai dati dell'utente hanno attualmente una dimensione di 4 byte e sono riempiti con un valore byte noto utilizzato dalle routine dello heap di debug per verificare che i limiti del blocco di memoria dell'utente non siano stati sovrascritti.  L'heap di debug riempie inoltre i nuovi blocchi di memoria con un valore noto.  Se, come illustrato di seguito, si sceglie di mantenere nell'elenco collegato dello heap i blocchi liberati, anche questi blocchi liberati verranno riempiti con un valore noto.  Attualmente i valori byte utilizzati sono i seguenti:  
  
 NoMansLand \(0xFD\)  
 I buffer "NoMansLand" presenti da entrambi i lati della memoria utilizzata da un'applicazione sono attualmente riempiti con il valore 0xFD.  
  
 Blocchi liberati \(0xDD\)  
 I blocchi liberati mantenuti inutilizzati nell'elenco collegato dell'heap di debug quando è impostato il flag `_CRTDBG_DELAY_FREE_MEM_DF` sono attualmente riempiti con il valore 0xDD.  
  
 Nuovi oggetti \(0xCD\)  
 I nuovi oggetti vengono riempiti con il valore 0xCD al momento dell'allocazione.  
  
 ![Torna all'inizio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenuto](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Tipi di blocchi sull'heap di debug  
 Ciascun blocco di memoria dell'heap di debug viene assegnato a uno di cinque tipi di allocazione.  Questi tipi vengono registrati e visualizzati nei report in modo diverso per il rilevamento di perdite e i report sullo stato.  È possibile specificare il tipo di un blocco allocandolo mediante una chiamata diretta a una delle funzioni di allocazione dello heap di debug quale [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg).  I cinque tipi di blocchi di memoria dell'heap di debug \(impostati nel membro **nBlockUse** della struttura **\_CrtMemBlockHeader**\) sono i seguenti:  
  
 **\_NORMAL\_BLOCK**  
 Una chiamata a [malloc](/visual-cpp/c-runtime-library/reference/malloc) o [calloc](/visual-cpp/c-runtime-library/reference/calloc) crea un blocco normale.  Se si ha intenzione di utilizzare solo blocchi normali e non sono necessari blocchi client, è possibile definire [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc), in modo che tutte le chiamate di allocazione dello heap vengano associate agli equivalenti di debug delle build di debug.  Sarà così possibile archiviare le informazioni di nome file e numero di riga relative a ciascuna chiamata di allocazione nella corrispondente intestazione di blocco.  
  
 `_CRT_BLOCK`  
 I blocchi di memoria allocati internamente da numerose funzioni della libreria di runtime sono contrassegnati come blocchi CRT, in modo da poter essere gestiti separatamente.  Di conseguenza non avranno necessariamente alcun effetto sul rilevamento delle perdite e su altre operazioni.  Le allocazioni non devono mai allocare, riallocare o liberare blocchi di tipo CRT.  
  
 `_CLIENT_BLOCK`  
 Un'applicazione può tenere traccia con modalità speciali di un dato gruppo di allocazioni a scopo di debug effettuando tali allocazioni con questo tipo di blocco di memoria, utilizzando chiamate esplicite alle funzioni dello heap di debug.  In MFC, ad esempio, tutti gli oggetti **CObject** vengono allocati come blocchi client, mentre è possibile che altre applicazioni inseriscano oggetti di memoria differenti in blocchi client.  È inoltre possibile specificare sottotipi dei blocchi client per consentire una registrazione più differenziata.  Per specificare sottotipi di blocchi client, spostare il numero verso sinistra di 16 bit ed effettuare un'operazione `OR` su di esso con `_CLIENT_BLOCK`.  Di seguito è riportato un esempio:  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 È possibile installare una funzione hook fornita dal client per il dump degli oggetti memorizzati in blocchi Client mediante [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient). Tale funzione verrà quindi chiamata ogni volta che una funzione di debug esegue il dump di un blocco Client.  È inoltre possibile utilizzare [\_CrtDoForAllClientObjects](/visual-cpp/c-runtime-library/reference/crtdoforallclientobjects) per chiamare una data funzione fornita dall'applicazione per ciascun blocco Client dell'heap di debug.  
  
 **\_FREE\_BLOCK**  
 Normalmente i blocchi liberati vengono rimossi dall'elenco.  Per controllare che non vengano eseguite operazioni di scrittura nella memoria liberata o per simulare condizioni di memoria ridotta, è possibile scegliere di mantenere i blocchi liberati nell'elenco collegato, contrassegnati come liberi e riempiendoli con un valore byte noto \(attualmente 0xDD\).  
  
 **\_IGNORE\_BLOCK**  
 È possibile disattivare le operazioni dell'heap di debug per un certo periodo di tempo.  Durante questo periodo i blocchi di memoria vengono mantenuti nell'elenco, ma vengono contrassegnati come blocchi da ignorare.  
  
 Per determinare il tipo e il sottotipo di un dato blocco, utilizzare la funzione [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) e le macro **\_BLOCK\_TYPE** e **\_BLOCK\_SUBTYPE**.  Le macro vengono definite \(in Crtdbg.h\) come segue:  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Torna all'inizio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenuto](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Verificare l'integrità dell'heap e le perdite di memoria  
 È necessario accedere a diverse funzionalità dell'heap di debug dall'interno del codice.  Nella seguente sezione vengono descritte alcune funzionalità e le relative modalità di utilizzo.  
  
 `_CrtCheckMemory`  
 È possibile utilizzare una chiamata a [\_CrtCheckMemory](/visual-cpp/c-runtime-library/reference/crtcheckmemory), ad esempio, per controllare l'integrità dell'heap in qualsiasi punto.  Questa funzione esamina ciascun blocco di memoria nell'heap, verifica che le informazioni dell'intestazione del blocco di memoria siano valide e conferma che i buffer non sono stati modificati.  
  
 `_CrtSetDbgFlag`  
 È possibile definire nei dettagli le modalità con cui l'heap di debug tiene traccia delle allocazioni ricorrendo a un flag interno, [\_crtDbgFlag](/visual-cpp/c-runtime-library/crtdbgflag), che può essere letto e impostato mediante la funzione [\_CrtSetDbgFlag](/visual-cpp/c-runtime-library/reference/crtsetdbgflag).  Modificando questo flag, è possibile comunicare all'heap di debug di verificare la presenza di eventuali perdite di memoria al termine del programma e di segnalare le perdite rilevate.  Analogamente, è possibile specificare che i blocchi di memoria liberati non siano rimossi dall'elenco collegato, per simulare situazioni di poca memoria.  Al controllo dell'heap questi blocchi liberati vengono esaminati nella loro interezza per verificare che non siano stati compromessi.  
  
 Il flag **\_crtDbgFlag** contiene i seguenti campi di bit:  
  
|Campo di bit|Valore<br /><br /> predefinito|Descrizione|  
|------------------|----------------------------|-----------------|  
|**\_CRTDBG\_ALLOC\_MEM\_DF**|On|Attiva l'allocazione di debug.  Quando questo bit è off, le allocazioni rimangono concatenate ma vengono assegnate al tipo di blocco **\_IGNORE\_BLOCK**.|  
|**\_CRTDBG\_DELAY\_FREE\_MEM\_DF**|Off|Impedisce l'effettiva liberazione della memoria, ad esempio per simulare condizioni di poca memoria.  Quando questo bit è on, i blocchi liberati vengono mantenuti nell'elenco collegato dell'heap di debug, ma vengono contrassegnati come **\_FREE\_BLOCK** e riempiti con uno speciale valore byte.|  
|**\_CRTDBG\_CHECK\_ALWAYS\_DF**|Off|Causa la chiamata a **\_CrtCheckMemory** a ogni allocazione e disallocazione.  Ciò rallenta l'esecuzione, ma rileva velocemente gli errori.|  
|**\_CRTDBG\_CHECK\_CRT\_DF**|Off|Fa sì che i blocchi contrassegnati come tipo **\_CRT\_BLOCK** vengano inclusi nelle operazioni di rilevamento di perdite e differenze tra stati.  Quando questo bit è off, la memoria utilizzata internamente dalla libreria di runtime viene ignorata durante queste operazioni.|  
|**\_CRTDBG\_LEAK\_CHECK\_DF**|Off|Fa sì che il controllo delle perdite di memoria venga eseguito al termine del programma mediante una chiamata a **\_CrtDumpMemoryLeaks**.  Se l'applicazione non ha liberato tutta la memoria allocata, verrà generato un report di errore.|  
  
 ![Torna all'inizio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenuto](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> Configurare l'heap di debug  
 Tutte le chiamate alle funzioni dell'heap, quali `malloc`, `free`, `calloc`, `realloc`, `new` e `delete` vengono risolte nelle versioni di debug di tali funzioni che operano nell'heap di debug.  Quando si libera un blocco di memoria, l'heap di debug controlla automaticamente l'integrità dei buffer presenti da entrambi i lati dell'area allocata e genera un messaggio di errore se si è verificata una sovrascrittura.  
  
 **Per utilizzare l'heap di debug**  
  
-   Collegare la build di debug dell'applicazione a una versione di debug della libreria di runtime del linguaggio C.  
  
 **Per modificare uno più campi di bit \_crtDbgFlag e creare un nuovo stato per il flag**  
  
1.  Chiamare `_CrtSetDbgFlag` con il parametro `newFlag` impostato su `_CRTDBG_REPORT_FLAG` \(per ottenere lo stato corrente di `_crtDbgFlag`\) e archiviare il valore restituito in una variabile temporanea.  
  
2.  Attivare eventuali bit eseguendo un'operazione `OR` \(simbolo &#124; bit per bit\) tra la variabile temporanea e le corrispondenti maschere di bit \(rappresentate nel codice dell'applicazione da costanti manifesto\).  
  
3.  Disattivare gli altri bit effettuando un'operazione `AND` \(simbolo & bit per bit\) tra la variabile e un operatore `NOT` \(simbolo ~ bit per bit\) delle maschere di bit appropriate.  
  
4.  Chiamare `_CrtSetDbgFlag` con il parametro `newFlag` impostato sul valore archiviato nella variabile temporanea per creare il nuovo stato di `_crtDbgFlag`.  
  
 Le righe di codice riportate di seguito, ad esempio, attivano il rilevamento automatico delle perdite di memoria e disattivano il controllo dei blocchi di tipo `_CRT_BLOCK`:  
  
```  
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![Torna all'inizio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenuto](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> new, delete e \_CLIENT\_BLOCK nell'heap di debug C\+\+  
 Le versioni di debug della libreria di runtime C contengono le versioni di debug degli operatori C\+\+ `new` e `delete`.  Se si utilizza il tipo di allocazione `_CLIENT_BLOCK`, è necessario chiamare la versione di debug dell'operatore `new` in modo diretto oppure creare macro che sostituiscano l'operatore `new` nella modalità di debug, come illustrato nell'esempio che segue:  
  
```  
/* MyDbgNew.h  
 Defines global operator new to allocate from  
 client blocks  
*/  
  
#ifdef _DEBUG  
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)  
#else  
   #define DEBUG_CLIENTBLOCK  
#endif // _DEBUG  
  
/* MyApp.cpp  
        Use a default workspace for a Console Application to  
 *      build a Debug version of this code  
*/  
  
#include "crtdbg.h"  
#include "mydbgnew.h"  
  
#ifdef _DEBUG  
#define new DEBUG_CLIENTBLOCK  
#endif  
  
int main( )   {  
    char *p1;  
    p1 =  new char[40];  
    _CrtMemDumpAllObjectsSince( NULL );  
}  
```  
  
 La versione di debug dell'operatore `delete` può essere utilizzata con tutti i tipi di blocco e non è necessario apportare alcuna modifica al programma quando si compila una versione di rilascio.  
  
 ![Torna all'inizio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenuto](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> Funzioni per la creazione di report sullo stato dello heap  
 **\_CrtMemState**  
  
 Per generare uno snapshot di riepilogo dello stato dell'heap in un dato momento, utilizzare la struttura \_CrtMemState definita in CRTDBG.H:  
  
```  
typedef struct _CrtMemState  
{  
    // Pointer to the most recently allocated block:  
    struct _CrtMemBlockHeader * pBlockHeader;  
    // A counter for each of the 5 types of block:  
    size_t lCounts[_MAX_BLOCKS];  
    // Total bytes allocated in each block type:  
    size_t lSizes[_MAX_BLOCKS];  
    // The most bytes allocated at a time up to now:  
    size_t lHighWaterCount;  
    // The total bytes allocated at present:  
    size_t lTotalCount;  
} _CrtMemState;  
```  
  
 Questa struttura salva un puntatore al primo blocco \(quello allocato più di recente\) dell'elenco collegato dell'heap di debug.  Quindi, registrare in due matrici il numero di blocchi di memoria presenti nell'elenco per ciascun tipo \(\_NORMAL\_BLOCK`_CLIENT_BLOCK`, \_FREE\_BLOCK e così via\), nonché il numero dei byte allocati in ciascun tipo di blocco.  Riporta infine il massimo numero di byte allocato come singola entità nello heap fino a tal punto.  
  
 **Altre funzioni CRT per la creazione di report**  
  
 Le funzioni elencate di seguito indicano lo stato e il contenuto dell'heap e utilizzano tali informazioni per il rilevamento di perdite di memoria e altri problemi.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[\_CrtMemCheckpoint](/visual-cpp/c-runtime-library/reference/crtmemcheckpoint)|Salva uno snapshot dell'heap in una struttura **\_CrtMemState** fornita dall'applicazione.|  
|[\_CrtMemDifference](/visual-cpp/c-runtime-library/reference/crtmemdifference)|Confronta due strutture dello stato della memoria, salva le differenze tra di esse in una terza struttura di stato e restituisce TRUE se i due stati sono differenti.|  
|[\_CrtMemDumpStatistics](/visual-cpp/c-runtime-library/reference/crtmemdumpstatistics)|Esegue il dump di una data struttura **\_CrtMemState**.  La struttura può contenere uno snapshot dello stato dell'heap di debug in un dato momento o le differenze tra i due snapshot.|  
|[\_CrtMemDumpAllObjectsSince](/visual-cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Esegue il dump di informazioni su tutti gli oggetti allocati dopo la generazione di un dato snapshot dell'heap o dall'inizio dell'esecuzione.  Ogni volta che esegue il dump di un blocco **\_CLIENT\_BLOCK**, chiama una funzione hook fornita dall'applicazione, qualora ne sia stata installata una mediante **\_CrtSetDumpClient**.|  
|[\_CrtDumpMemoryLeaks](/visual-cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Determina se si sono verificate perdite di memoria dall'inizio dell'esecuzione del programma e, in caso positivo, esegue il dump di tutti gli oggetti allocati.  Ogni volta che **\_CrtDumpMemoryLeaks** esegue il dump di un blocco **\_CLIENT\_BLOCK**, chiama una funzione hook fornita dall'applicazione, qualora ne sia stata installata una mediante **\_CrtSetDumpClient**.|  
  
 ![Torna all'inizio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenuto](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> Rilevare le richieste di allocazione dell'heap  
 Sebbene conoscere il nome del file sorgente e il numero di riga in cui viene eseguita un'asserzione o una macro per la creazione di report sia spesso molto utile per individuare la causa di un problema, non è sempre così per le funzioni di allocazione heap.  Sebbene le macro possano essere inserite in numerosi punti appropriati nella struttura ad albero logica di un'applicazione, un'allocazione è spesso inclusa in una speciale routine che viene richiamata in momenti diversi da più posizioni differenti.  La difficoltà non risiede in genere nel sapere quale riga di codice ha eseguito un'allocazione errata, ma piuttosto nel capire quale delle migliaia di allocazioni eseguite da tale riga di codice è responsabile del problema e perché.  
  
 **Numeri univoci di richiesta di allocazione e \_crtBreakAlloc**  
  
 Il metodo più semplice per identificare la specifica chiamata di allocazione heap che ha avuto esito negativo consiste nell'utilizzare il numero univoco di richiesta di allocazione associato a ciascun blocco dell'heap di debug.  Quando le informazioni relative a un blocco vengono restituite da una delle funzioni dump, questo numero di richiesta di allocazione è racchiuso tra parentesi, ad esempio "{36}".  
  
 Quando si conosce il numero di richiesta di allocazione di un blocco allocato in modo errato, è possibile passare questo numero a [\_CrtSetBreakAlloc](/visual-cpp/c-runtime-library/reference/crtsetbreakalloc) per creare un punto di interruzione.  L'esecuzione si interromperà appena prima dell'allocazione del blocco e sarà possibile risalire i passi del codice in senso contrario all'esecuzione per determinare la routine responsabile della chiamata errata.  Per evitare di dover ripetere la compilazione, è possibile eseguire la stessa operazione nel debugger impostando **\_crtBreakAlloc** sul numero di richiesta di allocazione in questione.  
  
 **Creazione di versioni di debug delle routine di allocazione**  
  
 Una tecnica un po' più complicata consiste nel creare versioni di debug delle routine di allocazione, paragonabili alle versioni **\_dbg** delle [funzioni di allocazione heap](../debugger/debug-versions-of-heap-allocation-functions.md).  Sarà quindi possibile passare gli argomenti relativi a file sorgente e numero di riga attraverso le routine di allocazione heap sottostanti per sapere immediatamente dove ha avuto origine un'allocazione errata.  
  
 Si supponga ad esempio che l'applicazione contenga una routine di utilizzo comune simile alla seguente:  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 In un file di intestazione sarebbe possibile aggiungere codice del seguente tipo:  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 Si provvederebbe quindi a modificare l'allocazione nella routine di creazione record come segue:  
  
```  
int addNewRecord(struct RecStruct *prevRecord,  
                int recType, int recAccess  
#ifdef _DEBUG  
               , const char *srcFile, int srcLine  
#endif  
    )  
{  
    /* ... code omitted through actual allocation ... */  
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,  
            srcFile, scrLine)) == NULL)  
    /* ... rest of routine omitted too ... */  
}  
```  
  
 Il nome del file di origine e il numero di riga in cui è stata effettuata la chiamata a `addNewRecord` verranno memorizzati in ciascun blocco allocato nell'heap di debug e verranno indicati quando il blocco verrà esaminato.  
  
 ![Torna all'inizio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenuto](#BKMK_Contents)  
  
## Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)