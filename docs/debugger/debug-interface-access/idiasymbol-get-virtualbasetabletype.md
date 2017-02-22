---
title: "IDiaSymbol::get_virtualBaseTableType | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "IDiaSymbol::get_virtualBaseTableType (metodo)"
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_virtualBaseTableType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il tipo di puntatore base virtuale della tabella.  
  
## Sintassi  
  
```cpp#  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`pRetVal`|\[out\]  restituisce [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) l'oggetto che specifica il tipo di tabella di base.|  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 Un puntatore di base virtuale della tabella \(`vbtptr`\) è un puntatore nascosto in un oggetto  [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable che gestisce ereditarietà da classi di base virtuali.  In `vbtptr` può presentare dimensioni diverse in base alle classi derivate.  
  
 questo metodo restituisce [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che può essere utilizzato per determinare la dimensione del vbtptr.  
  
## Requisiti  
  
|Requisiti|Descrizione|  
|---------------|-----------------|  
|intestazione:|dia2.h|  
|versione:|DIA SDK v8.0|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)