---
title: "Informazioni su SAL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# Informazioni su SAL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il linguaggio di annotazione del codice sorgente Microsoft \(SAL\) fornisce un set di voci che consente di descrivere il modo in cui una funzione utilizza i suoi parametri, le ipotesi che fa su di essi e le proprietà che garantisce quando termina.  Le annotazioni vengono definite nel file di intestazione `<sal.h>`.  L'analisi del codice di Visual Studio per C\+\+ utilizza le annotazioni SAL per modificare l'analisi di funzioni.  Per ulteriori informazioni su SAL 2,0 per lo sviluppo del driver windows, vedere [Annotazioni SAL 2.0 per driver di Windows](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 A livello nativo, C e C\+\+ forniscono solo poche modalità per far sì che gli sviluppatori possano esprimere in modo consistente finalità e invarianti.  Utilizzando le annotazioni SAL, è possibile descrivere le funzioni in modo più dettagliato così che gli sviluppatori che ne fanno uso possano capire meglio come utilizzarle.  
  
## Cos'è SAL e perché bisognerebbe utilizzarlo?  
 Semplicemente, SAL è un modo conveniente per consentire al compilatore di controllare il codice automaticamente.  
  
### SAL rende il codice più importante  
 SAL consente di rendere la progettazione di codice più comprensibile, sia per gli esseri umani che per gli strumenti di analisi del codice.  Si consideri l'esempio che mostra la funzione C runtime `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 È possibile stabilire cosa fa la funzione?  Quando una funzione viene implementata o chiamata, determinate proprietà devono essere mantenute per garantire la correttezza dei programmi.  Solo guardando una dichiarazione come quella dell'esempio, non si conosce quali sono.  Senza annotazioni SAL, è opportuno basarsi sulla documentazione o sui commenti del codice.  Ecco cosa dice la documentazione di MSDN per `memcpy`:  
  
> "Copia count byte di src verso dest.Se le aree di origine e di destinazione si sovrappongono il comportamento di memcpy non è specificato.Utilizzare memmove per gestire le aree sovrapposte.  
> **Nota sulla sicurezza:** assicurarsi che il buffer di destinazione sia della stessa dimensione o di una dimensione maggiore del buffer di origine.Per ulteriori informazioni, vedere Evitare sovraccarichi del buffer."  
  
 La documentazione contiene una coppia di bit di informazioni che indicano che il codice deve gestire alcune proprietà per garantire la correttezza dei programmi:  
  
-   `memcpy` copia il `count` di byte dal buffer di origine al buffer di destinazione.  
  
-   Il buffer di destinazione deve essere almeno delle dimensioni del buffer di origine.  
  
 Tuttavia, il compilatore non è in grado di leggere documentazione o commenti informali.  Non sa che esiste una relazione tra i due buffer e `count` e non può nemmeno indovinare in modo efficace se esiste una relazione.  SAL potrebbe fornire maggiore chiarezza sulle proprietà e l'implementazione della funzione, come illustrato di seguito:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Si noti che le annotazioni sono simili alle informazioni nella documentazione di MSDN, ma sono più concise e seguono un modello semantico.  Quando si legge il codice, è possibile comprendere rapidamente le proprietà di questa funzione e come evitare problemi di sicurezza di sovraccarico del buffer.  Anche meglio, i modelli semantico che SAL fornisce possono migliorare l'efficienza e l'efficacia degli strumenti automatizzati di analisi del codice nell'individuazione di possibili bug.  Si immagini che qualcuno scriva questa implementazione contenente errori di `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Questa implementazione contiene un comune errore in cui si eccede di uno la dimensione del buffer.  Fortunatamente, l'autore di codice ha incluso l'annotazione SAL sulla dimensione del buffer \- uno strumento di analisi del codice potrebbe intercettare il bug analizzando questa funzione singolarmente.  
  
### Nozioni fondamentali su SAL  
 SAL definisce quattro tipi di base di parametri, suddivisi in categorie in base al modello di utilizzo.  
  
|Categoria|Annotazione di parametri|Descrizione|  
|---------------|------------------------------|-----------------|  
|**Input per la funzione chiamata**|`_In_`|I dati vengono passati alla funzione chiamata e vengono considerati di sola lettura.|  
|**Input alla funzione chiamata e output al chiamante**|`_Inout_`|I dati utilizzabili sono passati alla funzione e vengono potenzialmente modificati.|  
|**Output al chiamante**|`_Out_`|Il chiamante fornisce alla funzione chiamata solo lo spazio per scrivere.  La funzione chiamata scrive i dati in tale spazio.|  
|**Output di tipo puntatore al chiamante**|`_Outptr_`|Come **Output to caller**.  Il valore restituito dalla funzione chiamata è un puntatore.|  
  
 Queste quattro annotazioni di base possono essere rese più esplicite in diversi modi.  Per impostazione predefinita, i parametri del puntatore annotati sono obbligatori \- non devono essere NULL perché la funziona abbia esito positivo.  La variante più utilizzata delle annotazioni di base indica che un parametro puntatore è facoltativo \- se è NULL, la funzione può comunque riuscire a svolgere la propria attività.  
  
 In questa tabella viene mostrato come distinguere tra i parametri obbligatori e quelli facoltativi:  
  
||Parametri obbligatori|Parametri facoltativi|  
|-|---------------------------|---------------------------|  
|**Input per la funzione chiamata**|`_In_`|`_In_opt_`|  
|**Input alla funzione chiamata e output al chiamante**|`_Inout_`|`_Inout_opt_`|  
|**Output al chiamante**|`_Out_`|`_Out_opt_`|  
|**Output di tipo puntatore al chiamante**|`_Outptr_`|`_Outptr_opt_`|  
  
 Le annotazioni consentono di identificare possibili valori non inizializzati e possibili utilizzi non validi del puntatore NULL in modo formale e accurato.  Passare il valore NULL a un parametro obbligatorio potrebbe provocare un arresto anomalo, oppure potrebbe causare la restituzione di codice di errore "failed".  In ogni caso, la funzione potrebbe non riuscire a eseguire il proprio lavoro.  
  
## esempi SAL  
 In questa sezione vengono illustrati esempi di codice per le annotazioni SAL di base.  
  
### Usare lo strumento di analisi del codice di Visual Studio per trovare difetti  
 Negli esempi, lo strumento di analisi del codice di Visual Studio viene utilizzato insieme alle annotazioni SAL per trovare difetti del codice.  Di seguito viene illustrato come eseguire questa operazione.  
  
##### Per utilizzare gli strumenti di analisi codice di Visual Studio e SAL  
  
1.  In Visual Studio, aprire un progetto C\+\+ che contiene annotazioni SAL.  
  
2.  Dalla barra dei menu, scegliere **Compila**, **Esegui Analisi del codice su soluzione**.  
  
     Si consideri l'esempio di \_In\_ che si trova in questa sezione.  Se si esegue l'analisi codice, viene visualizzato questo avviso:  
  
    > **C6387 Valore del parametro non valido**   
    > 'pInt' potrebbe essere '0': questa condizione non soddisfa la specifica della funzione 'InCallee'.  
  
### Esempio: L'annotazione \_In\_  
 L'annotazione `_In_` indica che:  
  
-   Il parametro deve essere valido e non verrà modificato.  
  
-   La funzione leggerà solo dal buffer contenente un solo elemento.  
  
-   Il chiamante deve fornire il buffer e inizializzarlo.  
  
-   `_In_` specifica "readonly".  Un errore comune consiste nell'applicazione di `_In_` a un parametro che invece deve disporre dell'annotazione `_Inout_`.  
  
-   `_In_` è consentito su scalari di non puntatore, ma viene ignorato dall'analizzatore.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Se si utilizza l'analisi codice di Visual Studio in questo esempio, esegue la verifica che i chiamanti passino un puntatore diverso da Null a un buffer inizializzato per `pInt`.  Il valore `pInt` non può essere NULL in questo caso.  
  
### Esempio: L'annotazione \_In\_opt\_  
 `_In_opt_` ha lo stesso comportamento di `_In_`, eccetto che il parametro di input può essere NULL e, pertanto, la funzione deve verificarlo.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 L'analisi codice di Visual Studio verifica che la funzione controlli che ci siano dei valori NULL prima di accedere al buffer.  
  
### Esempio: L'annotazione \_Out\_  
 `_Out_` supporta uno scenario comune in cui un puntatore diverso da NULL che indica un elemento di un buffer viene passato e la funzione inizializza l'elemento.  Il chiamante non deve inizializzare il buffer prima della chiamata, la funzione chiamata dovrà di inizializzarlo prima di restituire.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Lo strumento di analisi del codice di Visual Studio verifica che il chiamante passi un puntatore diverso da Null a un buffer per `pInt` e che il buffer venga inizializzato dalla funzione prima che venga restituito.  
  
### Esempio: L'annotazione \_Out\_opt\_  
 `_Out_opt_` ha lo stesso comportamento di `_Out_`, eccetto che il parametro può essere NULL e, pertanto, la funzione deve verificarlo.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 L'analisi codice di Visual Studio verifica che la funzione controlli la presenza del valore NULL prima che `pInt` sia dereferenziato e se `pInt` non è NULL, che il buffer venga inizializzato dalla funzione prima che venga restituito.  
  
### Esempio: L'annotazione \_Inout\_  
 `_Inout_` viene utilizzato per annotare un parametro puntatore che può essere modificato mediante la funzione.  Il puntatore deve indicare dati inizializzati validi prima della chiamata e anche se viene modificato, deve essere un valore valido da restituire.  L'annotazione specifica che la funzione può liberamente leggere e scrivere nel buffer di un elemento.  Il chiamante deve fornire il buffer e inizializzarlo.  
  
> [!NOTE]
>  Come `_Out_`, `_Inout_` deve essere applicato a un valore modificabile.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 L'analisi del codice di Visual Studio verifica che il chiamante passi un puntatore diverso da Null a un buffer inizializzato per `pInt` e che, prima di restituire, `pInt` sia ancora diverso da Null e che il buffer sia inizializzato.  
  
### Esempio: L'annotazione \_Inout\_opt\_  
 `_Inout_opt_` ha lo stesso comportamento di `_Inout_`, eccetto che il parametro di input può essere NULL e, pertanto, la funzione deve verificarlo.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 L'analisi codice di Visual Studio verifica che la funzione controlli la presenza del valore NULL acceda al buffer e che `pInt` sia dereferenziato e se non è NULL, che il buffer venga inizializzato dalla funzione prima che venga restituito.  
  
### Esempio: L'annotazione \_Outptr\_  
 `_Outptr_` viene utilizzato per annotare un parametro che deve restituire un puntatore.  Il parametro non deve essere NULL e la funzione chiamata restituisce un puntatore diverso da Null che punti a dati inizializzati.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 L'analisi del codice di Visual Studio verifica che il chiamante passi un puntatore diverso da Null per `*pInt`, e che il buffer venga inizializzato dalla funzione prima che venga restituito.  
  
### Esempio: L'annotazione \_Outptr\_opt\_  
 `_Outptr_opt_` si comporta allo stesso modo di `_Outptr_`, con la differenza che il parametro è facoltativo, il chiamante può passare un puntatore NULL per il parametro.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 L'analisi codice di Visual Studio verifica che la funzione controlli la presenza del valore NULL prima che `*pInt` sia dereferenziato e se non è NULL, che il buffer venga inizializzato dalla funzione prima che venga restituito.  
  
### Esempio: L'annotazione di \_Success\_ in combinazione con \_Out\_  
 Le annotazioni possono essere applicate alla maggior parte degli oggetti.  In particolare, è possibile annotare un'intera funzione.  Una delle funzionalità più comuni di una funzione è che avrà esito positivo o negativo.  Ma come l'associazione tra un buffer e la sua dimensione, C\/C\+\+ non può indicare l'esito positivo o negativo di funzione.  Mediante l'annotazione `_Success_`, è possibile specificare l'aspetto di una funzione che ha esito positivo.  Il parametro dell'annotazione `_Success_` è semplicemente un'espressione che quando è true indica che la funzione è riuscita.  L'espressione può essere qualsiasi elemento che il parser di annotazione possa gestire.  Gli effetti delle annotazioni dopo che la funzione ritorna sono applicabili solo quando la funzione ha esito positivo.  In questo esempio viene illustrato come `_Success_` interagisce con `_Out_` per eseguire l'operazione corretta.  È possibile utilizzare la parola chiave `return` per rappresentare il valore di ritorno.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 L'annotazione `_Out_` fa sì che l'analisi codice di Visual Studio verifichi che il chiamante passi un puntatore diverso da Null a un buffer per `pInt`e che il buffer venga inizializzato dalla funzione prima che venga restituito.  
  
## procedura consigliata per SAL  
  
### Aggiungere annotazioni al codice esistente  
 SAL è una tecnologia potente che consente di migliorare la protezione e l'affidabilità del codice.  Dopo aver imparato SAL, è possibile applicare la nuova competenza al lavoro quotidiano.  Nel codice nuovo, è possibile utilizzare le specifiche basate su SAL dalla progettazione in poi; nel codice vecchio, è possibile aggiungere gradualmente le annotazioni incrementando i vantaggi ad ogni aggiornamento.  
  
 Le intestazioni pubbliche di Microsoft sono già annotate.  Pertanto, nei progetti, si consiglia di annotare prima di tutto le funzioni ai nodi foglia e le funzioni che richiamano le API di Win32 per ricevere i maggiori benefici.  
  
### Quando annoto?  
 Di seguito sono riportate alcune linee guida:  
  
-   Annotare tutti i parametri di tipo puntatore.  
  
-   Annotare le annotazioni di un intervallo così che l'analisi del codice assicuri la sicurezza dei puntatori e del buffer.  
  
-   Annotare le regole di blocco e effetti collaterali di blocco.  Per ulteriori informazioni, vedere [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md).  
  
-   Annotare le proprietà del driver e altre proprietà specifiche di dominio.  
  
 Oppure è possibile annotare tutti i parametri per rendere chiaro l'intento in tutto il progetto e rendere semplice controllare che le annotazioni siano state apportate.  
  
## Risorse correlate  
 [Blog del team di analisi codice](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## Vedere anche  
 [Uso delle annotazioni SAL per ridurre gli errori del codice C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento delle funzioni](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)