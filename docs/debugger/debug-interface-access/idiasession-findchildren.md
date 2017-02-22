---
title: "IDiaSession::findChildren | Microsoft Docs"
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
  - "IDiaSession::findChildren (metodo)"
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera tutti gli elementi figlio di un identificatore padre specificato che corrispondono al nome e il tipo del simbolo.  
  
## Sintassi  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parametri  
 `parent`  
 \[in\]   [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il padre.  Se questo simbolo padre è una funzione, modulo, o blocco, i relativi figli lessicali vengono restituiti in `ppResult`.  Se il simbolo padre è di tipo, i relativi figli di classe vengono restituiti.  se questo parametro è `NULL`, quindi  `symtag` deve essere impostata su  `SymTagExe` o  `SymTagNull`, che restituisce l'ambito globale \(file EXE\).  
  
 `symtag`  
 \[in\]  Specifica il tag dei simboli degli elementi figlio da recuperare.  I valori vengono ricavati da [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumerazione.  Impostare su `SymTagNull` per recuperare tutti gli elementi figlio.  
  
 `name`  
 \[in\]  Specifica il nome degli elementi figlio da recuperare.  Impostare su `NULL` per tutti gli elementi figlio vengano recuperati.  
  
 `compareFlags`  
 \[in\]  specifica le opzioni di confronto applicate per denominare la corrispondenza.  Valori da [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) l'enumerazione può essere utilizzata da solo o nell'associazione.  
  
 `ppResult`  
 \[out\]  restituisce [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) oggetto che contiene l'elenco dei simboli figlio recuperati.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come trovare le variabili locali della funzione `pFunc` il nome della corrispondenza  `szVarName`.  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## Vedere anche  
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)