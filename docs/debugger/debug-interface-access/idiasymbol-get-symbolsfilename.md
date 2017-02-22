---
title: "IDiaSymbol::get_symbolsFileName | Microsoft Docs"
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
  - "IDiaSymbol::get_symbolsFileName (metodo)"
ms.assetid: c1aa39ee-d645-431e-bf5f-0640c0998934
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_symbolsFileName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il nome del file da cui i simboli sono stati caricati.  
  
## Sintassi  
  
```cpp#  
HRESULT get_symbolsFileName (   
   BSTR* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce il nome del file da cui i simboli sono stati caricati.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 Questa proprietà è valida solo per i simboli con un oggetto [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valore di  `SymTagExe` che dispone anche di ambito globale.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)