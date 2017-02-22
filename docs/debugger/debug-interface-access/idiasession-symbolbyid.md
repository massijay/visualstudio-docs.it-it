---
title: "IDiaSession::symbolById | Microsoft Docs"
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
  - "IDiaSession::symbolById (metodo)"
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un simbolo dal relativo identificatore univoco.  
  
## Sintassi  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### Parametri  
 `id`  
 \[in\]  identificatore univoco.  
  
 `ppSymbol`  
 \[out\]  restituisce [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il simbolo recuperato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 L'identificatore specificato sia un valore univoco utilizzato internamente dal DIA SDK per rendere tutti i simboli univoci.  
  
 Questo metodo può essere utilizzato, ad esempio, per recuperare il simbolo che rappresenta il tipo di altro simbolo \(vedere l'esempio\).  
  
## Esempio  
 In questo esempio vengono recuperati [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) rappresenta il tipo di altro simbolo.  In questo esempio viene illustrato come utilizzare `symbolById` metodo nella sessione.  Un approccio più semplice consiste nel chiamare [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) metodo per recuperare direttamente il simbolo del tipo.  
  
```cpp#  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)