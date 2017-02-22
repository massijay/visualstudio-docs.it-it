---
title: "IDiaSymbol::get_lexicalParent | Microsoft Docs"
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
  - "IDiaSymbol::get_lexicalParent (metodo)"
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_lexicalParent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un riferimento al componente padre lessicale del simbolo.  
  
## Sintassi  
  
```cpp#  
HRESULT get_lexicalParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  restituisce [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il padre lessicale del simbolo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 Il padre lessicale di un simbolo è la funzione o il modulo contenitore.  Ad esempio, l'elemento padre lessicale di un parametro di funzione o una variabile locale è la funzione stessa mentre il padre lessicale della funzione è il modulo definita in.  
  
 I simboli possibili che possono essere visualizzati come elementi padre lessicali vengono documentati in [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md).  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)