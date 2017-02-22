---
title: "IDiaDataSource::get_lastError | Microsoft Docs"
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
  - "IDiaDataSource::get_lastError (metodo)"
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il nome file per ultimo errore di caricamento.  
  
## Sintassi  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### Parametri  
 pRetVal  
 \[out\]  Restituisce una stringa contenente il nome del file pdb associato all'ultimo errore di caricamento.  
  
## Valore restituito  
 Restituisce l'ultimo codice di errore causato da un'operazione di caricamento.  Restituisce `E_INVALIDARG` se  `pRetVal` il parametro è  `NULL`.  
  
## Esempio  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)