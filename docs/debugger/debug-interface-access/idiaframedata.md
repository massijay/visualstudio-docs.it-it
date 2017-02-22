---
title: "IDiaFrameData | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "IDiaFrameData (interfaccia)"
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

espone i dettagli di uno stack frame.  
  
## Sintassi  
  
```  
IDiaFrameData : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaFrameData`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaFrameData::get\_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Recupera la parte della sezione del codice dell'indicizzazione del frame.|  
|[IDiaFrameData::get\_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Recupera la parte dell'offset del codice dell'indicizzazione del frame.|  
|[IDiaFrameData::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Recupera indirizzo \(RVA\) virtuale di immagine del codice per il frame.|  
|[IDiaFrameData::get\_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Recupera indirizzo \(VA\) virtuale del codice per il frame.|  
|[IDiaFrameData::get\_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Recupera la lunghezza, in byte, del blocco di codice descritto dal frame.|  
|[IDiaFrameData::get\_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Recupera il numero di byte delle variabili locali inserite nello stack.|  
|[IDiaFrameData::get\_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Recupera il numero di byte dei parametri spinti nello stack.|  
|[IDiaFrameData::get\_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Recupera il numero massimo di byte spinti nello stack nel frame.|  
|[IDiaFrameData::get\_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Recupera il numero di byte del codice di prologo nel blocco.|  
|[IDiaFrameData::get\_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Recupera il numero di byte dei registri salvati spinti nello stack.|  
|[IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Recuperare la stringa del programma utilizzata per calcolare il set di log prima della chiamata alla funzione corrente.|  
|[IDiaFrameData::get\_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Recupera un flag che indica che la gestione delle eccezioni del sistema è attiva.|  
|[IDiaFrameData::get\_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Recupera un flag che indica che la gestione delle eccezioni C\+\+ è attiva.|  
|[IDiaFrameData::get\_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|recupera un flag che indica che il blocco contiene il punto di ingresso di una funzione.|  
|[IDiaFrameData::get\_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|recupera un flag che indica che il puntatore di base è allocato per il codice in questo intervallo di indirizzi.  Il metodo è deprecato.|  
|[IDiaFrameData::get\_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|recupera il tipo di frame compilatore\-specifico.|  
|[IDiaFrameData::get\_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Recupera l'interfaccia di dati del frame per viene racchiuso della funzione.|  
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Esegue la rimozione dello stack e restituisce lo stato corrente di log in un'interfaccia del frame dello stack.|  
  
## Note  
 Informazioni dettagliate disponibili per un frame sono per i punti di esecuzione nell'intervallo di indirizzi indicato da e dalla durata di blocco.  
  
## Note per i chiamanti  
 Leggi questa interfaccia chiamando [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) o  [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md) metodi.  vedere [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) interfaccia per i dettagli.  
  
## Esempio  
 L'esempio visualizza le proprietà di `IDiaFrameData` oggetto.  vedere [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) interfaccia per un esempio di come  `IDiaFrameData` l'interfaccia viene ottenuta.  
  
```cpp#  
void PrintFrameData(IDiaFrameData* pFrameData){  
    DWORD dwSect;  
    DWORD dwOffset;  
    DWORD cbBlock;  
    DWORD cbLocals; // Number of bytes reserved for the function locals  
    DWORD cbParams; // Number of bytes reserved for the function arguments  
    DWORD cbMaxStack;  
    DWORD cbProlog;  
    DWORD cbSavedRegs;  
    BOOL  bSEH;  
    BOOL  bEH;  
    BOOL  bStart;  
    BSTR  wszProgram;  
  
    if(pFrameData->get_addressSection(&dwSect) == S_OK &&   
       pFrameData->get_addressOffset(&dwOffset) == S_OK &&  
       pFrameData->get_lengthBlock(&cbBlock) == S_OK &&  
       pFrameData->get_lengthLocals(&cbLocals) == S_OK &&  
       pFrameData->get_lengthParams(&cbParams) == S_OK &&  
       pFrameData->get_maxStack(&cbMaxStack) == S_OK &&  
       pFrameData->get_lengthProlog(&cbProlog) == S_OK &&  
       pFrameData->get_lengthSavedRegisters(&cbSavedRegs) == S_OK &&  
       pFrameData->get_systemExceptionHandling(&bSEH) == S_OK &&  
       pFrameData->get_cplusplusExceptionHandling(&bEH) == S_OK &&  
       pFrameData->get_functionStart(&bStart) == S_OK )  
    {  
        wprintf(L"Frame address  : %04X:%08X\n", dwSect, dwOffset);  
        wprintf(L"Block size     : 0x%8X\n", cbBlock);  
        wprintf(L"Locals size    : 0x%8X\n", cbLocals);  
        wprintf(L"Parms size     : 0x%8X\n", cbParams);  
        wprintf(L"Max stack used : 0x%8X\n", cbMaxStack);  
        wprintf(L"Prolog size    : 0x%8X\n", cbProlog);  
        wprintf(L"Saved regs size: 0x%8X\n", cbSavedRegs);  
        wprintf(L"System Exception Handling: %c\n", bSEH ? L'Y' : L'N');  
        wprintf(L"C++ Exception Handling   : %c\n", bEH ? L'Y' : L'N');  
        wprintf(L"Function starts in block : %c\n", bStart ? L'Y' : L'N');  
  
        if (pFrameData->get_program(&wszProgram) == S_OK)  
        {  
            wprintf(L"Program used for register set: %s\n", wszProgram);  
            SysFreeString(wszProgram);  
        }  
        else  
        {  
            wprintf(L"\n");  
        }  
    }  
}  
```  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)   
 [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)