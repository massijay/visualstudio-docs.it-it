---
title: "IDiaSymbol::get_undecoratedNameEx | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_undecoratedNameEx (metodo)"
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una parte o tutto il nome non decorato per il nome decorato \+\+ c \(collegamento\).  
  
## Sintassi  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### Parametri  
 `undecoratedOptions`  
 \[in\]  Specifica una combinazione di flag che controllano ciò che viene restituito.  Vedere la sezione relativa alle osservazioni per i valori specifici e cosa fare.  
  
 `pRetVal`  
 \[out\]  Restituisce il nome non decorato per il nome decorato di un'applicazione C\/C\+\+.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 `undecorateOptions` può essere una combinazione dei seguenti flag.  
  
> [!NOTE]
>  I nomi del flag non sono definiti nel DIA SDK, pertanto è necessario aggiungere le dichiarazioni al codice oppure utilizzare valori non elaborati.  
  
|Flag|Valore|Descrizione|  
|----------|------------|-----------------|  
|UNDNAME\_COMPLETE|0x0000|abilita il undecoration completo.|  
|UNDNAME\_NO\_LEADING\_UNDERSCORES|0x0001|Rimuove generare caratteri di sottolineatura le parole chiave estese di Microsoft.|  
|UNDNAME\_NO\_MS\_KEYWORDS|0x0002|Disabilita l'espansione delle parole chiave estese di Microsoft.|  
|UNDNAME\_NO\_FUNCTION\_RETURNS|0x0004|disabilita l'espansione di tipo restituito per la dichiarazione primaria.|  
|UNDNAME\_NO\_ALLOCATION\_MODEL|0x0008|Disabilita l'espansione del modello di dichiarazione.|  
|UNDNAME\_NO\_ALLOCATION\_LANGUAGE|0x0010|Disabilita l'espansione dell'identificatore di linguaggio di dichiarazione.|  
|UNDNAME\_RESERVED1|0x0020|RISERVATO.|  
|UNDNAME\_RESERVED2|0x0040|RISERVATO.|  
|UNDNAME\_NO\_THISTYPE|0x0060|Disabilita tutti i modificatori su `this` tipo.|  
|UNDNAME\_NO\_ACCESS\_SPECIFIERS|0x0080|Disabilita l'espansione degli identificatori di accesso per i membri.|  
|UNDNAME\_NO\_THROW\_SIGNATURES|0x0100|Disabilita l'espansione di “tiro\-firme„ per le funzioni e i puntatori a funzioni.|  
|UNDNAME\_NO\_MEMBER\_TYPE|0x0200|disabilita l'espansione di `static` o  `virtual` membri.|  
|UNDNAME\_NO\_RETURN\_UDT\_MODEL|0x0400|Disabilita l'espansione del modello di Microsoft per la restituzione di tipo definito dall'utente.|  
|UNDNAME\_32\_BIT\_DECODE|0x0800|nomi decorati 32 bit di Undecorates.|  
|UNDNAME\_NAME\_ONLY|0x1000|Ottiene il solo nome per la dichiarazione primaria, nome di restituisce semplicemente \[ambito::\].  Espandere params del modello.|  
|UNDNAME\_TYPE\_ONLY|0x2000|L'input è semplicemente una codifica del tipo; crea un dichiaratore astratto.|  
|UNDNAME\_HAVE\_PARAMETERS|0x4000|I parametri di modello reali disponibili.|  
|UNDNAME\_NO\_ECSU|0x8000|Elimina enum\/classe\/struttura\/unione.|  
|UNDNAME\_NO\_IDENT\_CHAR\_CHECK|0x10000|Elimina il controllo per i caratteri validi per un identificatore.|  
|UNDNAME\_NO\_PTR64|0x20000|Non include ptr64 nell'output.|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)