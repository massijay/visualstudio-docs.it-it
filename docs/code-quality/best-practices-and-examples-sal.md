---
title: "Suggerimenti ed esempi (SAL) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Suggerimenti ed esempi (SAL)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Di seguito sono riportate alcune modalità per ottenere il meglio dal Source Code Annotation Language \(SAL\) ed evitare alcuni problemi comuni.  
  
## \_In\_  
 Se è previsto che la funzione scriva nell'elemento, utilizzare `_Inout_` anziché `_In_`.  Ciò è particolarmente rilevante in casi di conversione automatica da macro più vecchie a SAL.  Prima di SAL, molti programmatori utilizzavano le macro come commenti—macro chiamate `IN`, `OUT`, `IN_OUT`, o varianti di questi nomi.  Sebbene sia consigliabile convertire queste macro in SAL, vi invitiamo a prestare attenzione quando vengono convertite poiché il codice potrebbe venir modificato poiché il prototipo originale è stato scritto e la macro precedente potrebbe non riflettere più quello che il codice fa.  Prestare particolare attenzione alla macro di commento `OPTIONAL` perché viene frequentemente eseguita in modo non corretto—ad esempio sul lato sbagliato di una virgola.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ int *p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
// Correct  
void Func2(_Inout_ PCHAR p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
```  
  
## \_opt\_  
 Se non viene consentito al chiamante di passare un puntatore null, utilizzare `_In_` o `_Out_` anziché `_In_opt_` o `_Out_opt_`.  Questo vale anche per una funzione che controlla i relativi parametri e restituisce un errore se sono NULL quando non dovrebbero esserlo.  Sebbene la presenza di una funzione che controlla i suoi parametri per vedere se ci sono valori NULL inaspettati sia una buona pratica difensiva, non significa che la voce di parametro possa essere di un tipo opzionale\(\_*Xxx*\_opt\_\).  
  
```cpp  
  
// Incorrect  
void Func1(_Out_opt_ int *p1)  
{  
    *p = 1;  
}  
  
// Correct  
void Func2(_Out_ int *p1)  
{  
    *p = 1;  
}  
  
```  
  
## \_Pre\_defensive\_ e \_Post\_defensive\_  
 Se in una funzione è presente un limite di attendibilità, si consiglia di utilizzare l'annotazione `_Pre_defensive_`.  Il modificatore "difensivo" modifica alcune annotazioni per indicare che, al momento della chiamata, l'interfaccia deve essere controllata obbligatoriamente, ma nel corpo dell'implementazione deve assumere che i parametri errati vengano superati.  In tal caso, `_In_ _Pre_defensive_` viene preferito ad un limite di attendibilità per indicare che sebbene un chiamante otterrà un errore se tenta di passare NULL, il corpo della funzione verrà analizzato come se il parametro fosse NULL e verranno contrassegnati tutti i tentativi di de referenziare il puntatore senza prima controllare che non sia NULL.  Un'annotazione `_Post_defensive_` può inoltre essere utilizzata nei callback, dove si assume che la parte attendibile sia il chiamante e il codice non attendibile sia il codice chiamato.  
  
## \_Out\_writes\_  
 Nell'esempio seguente viene illustrato un comune utilizzo improprio di `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 L'annotazione `_Out_writes_` significa che c'è un buffer.  Ha `cb` byte allocati, con il primo byte inizializzato in uscita.  Questa annotazione non è strettamente sbagliata ed è utile indicare la dimensione allocata.  Tuttavia, non indica quanti elementi vengono inizializzati dalla funzione.  
  
 Nell'esempio riportato di seguito vengono mostrate tre modalità corrette per specificare completamente le dimensioni esatte della parte inizializzata del buffer.  
  
```cpp  
  
// Correct  
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,   
    DWORD size,  
    PDWORD pCount  
);  
  
void Func2(_Out_writes_all_(size) CHAR *pb,   
    DWORD size  
);  
  
void Func3(_Out_writes_(size) PSTR pb,   
    DWORD size  
);  
  
```  
  
## \_Out\_ PSTR  
 L'utilizzo di `_Out_ PSTR` è quasi sempre errato.  Ciò viene interpretato come avere un parametro di output che punta a un buffer di caratteri che ha terminazione null.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Un'annotazione come `_In_ PCSTR` è comune e utile.  Punta a una stringa di input con terminazione NULL perché la precondizione `_In_` consente il riconoscimento di una stringa con terminazione null.  
  
## \_In\_ WCHAR\* p  
 `_In_ WCHAR* p` indica che esiste un puntatore di input `p` che indica un carattere.  Tuttavia, in molti casi, questa probabilmente non è la specifica che sia intende.  Invece, quello che probabilmente si intende è la specificazione di un array con terminazione null; a tale scopo, utilizzare `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 La mancanza di una corretta specificazione di una terminazione NULL è comune.  Utilizzare la versione appropriata `STR` per sostituire il tipo, come illustrato nell'esempio seguente.  
  
```cpp  
  
// Incorrect  
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
// Correct  
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
```  
  
## \_Out\_range\_  
 Se il parametro è un puntatore e si desidera specificare l'intervallo del valore dell'elemento puntato, utilizzare `_Deref_out_range_` anziché `_Out_range_`.  Nell'esempio seguente, è espresso l'intervallo di \*pcbFilled, non pcbFilled.  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Out_range_(0, cbSize) DWORD *pcbFilled  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled   
);  
  
```  
  
 `_Deref_out_range_(0, cbSize)` non è strettamente necessaria per alcuni strumenti in quanto può essere dedotto da `_Out_writes_to_(cbSize,*pcbFilled)`, ma qui viene mostrato per completezza.  
  
## Contesto non valido in \_When\_  
 Un altro errore comune è quello di utilizzare la valutazione post\-condivisa per le precondizioni.  Nell'esempio che segue, `_Requires_lock_held_` è una precondizione .  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 L'espressione `result` fa riferimento a un valore post\-condiviso che non è disponibile in pre\-condivisione.  
  
## TRUE in \_Success\_  
 Se la funzione ha esito positivo quando il valore restituito è diverso da zero, utilizzare `return != 0` come condizione di successo anziché `return == TRUE`.  Diverso da zero non significa necessariamente equivalente al valore effettivo che il compilatore fornisce per `TRUE`.  Il parametro `_Success_` è un'espressione e le seguenti espressioni vengono valutate come se fossero: `return != 0`, `return != false`, `return != FALSE` e `return` senza parametri o confronti.  
  
```cpp  
  
// Incorrect  
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
// Correct  
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
```  
  
## Variabile di riferimento  
 Per una variabile di riferimento, la versione precedente di SAL utilizzava il puntatore implicito come destinazione di annotazione e richiedeva l'aggiunta di un `__deref` alle annotazioni che facevano riferimento a una variabile di riferimento.  Questa versione utilizza l'oggetto stesso e non richiede il `_Deref_` aggiuntivo.  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
```  
  
## Annotazioni sui valori restituiti  
 L'esempio seguente mostra un problema comune nelle annotazioni sui valori restituiti.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 In questo esempio, `_Out_opt_` indica che il puntatore potrebbe essere NULL come parte della precondizione.  Tuttavia, le precondizioni non possono essere applicate al valore restituito.  In questo caso, l'annotazione corretta è `_Ret_maybenull_`.  
  
## Vedere anche  
 [Uso delle annotazioni SAL per ridurre gli errori del codice C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento delle funzioni](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funzioni intrinseche](../code-quality/intrinsic-functions.md)