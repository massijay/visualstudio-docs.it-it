---
title: "Funzione SccGetVersion | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetVersion"
helpviewer_keywords: 
  - "Funzione SccGetVersion"
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccGetVersion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione Ottiene il numero di versione dell'API di plug\-in controllo di origine supportato dal plug\-in del controllo del codice sorgente.  
  
## Sintassi  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### Parametri  
 Nessuno.  
  
## Valore restituito  
 Oggetto `LONG` tipo di dati che contiene il numero di versione dell'API di plug\-in controllo di origine supportati:  
  
|WORD|Descrizione|  
|----------|-----------------|  
|HIWORD|Numero di versione principale|  
|LOWORD|Versione secondaria|  
  
## Note  
 Ad esempio, se un plug\-in del controllo del codice sorgente supporta la versione 1.3 dell'API dei plug\-in controllo di origine, questa funzione restituisce 0x0103.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)