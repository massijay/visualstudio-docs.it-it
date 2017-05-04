---
title: "Interfaccia IDispError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDispError"
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDispError
Vengono fornite informazioni contestuali.  
  
> [!NOTE]
>  Questa interfaccia non è implementata.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDispError` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Recupera un determinato tipo di informazioni sugli errori.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Recupera l'oggetto successivo `IDispError`.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Recupera il codice di errore dall'oggetto `IDispError`.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Restituisce il ProgID dipendente dal linguaggio per la classe o l'applicazione che ha generato l'errore.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Restituisce il percorso del file della Guida e dell'ID del contesto dell'argomento che viene illustrato l'errore, se possibile.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Restituisce una descrizione testuale dell'errore.|