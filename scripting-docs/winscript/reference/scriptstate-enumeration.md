---
title: "Enumerazione SCRIPTSTATE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Enumerazione SCRIPTSTATE"
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Enumerazione SCRIPTSTATE
Specifica lo stato di un motore di scripting.  Questa enumerazione è utilizzata con i metodi [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md), [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) e [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md).  
  
## Sintassi  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTSTATE\_UNINITIALIZED|Lo script è stato appena creato, ma non è stato ancora inizializzato tramite un'interfaccia e [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) `IPersist*`.|  
|SCRIPTSTATE\_INITIALIZED|Lo script è stato inizializzato, ma non esegue \(connessione agli altri oggetti o eventi di affondamento\) o non esegue alcun codice.  Il codice è possibile eseguire query per l'esecuzione chiamando il metodo [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md).|  
|SCRIPTSTATE\_STARTED|Lo script può eseguire il codice, ma non è l'elaborazione di eventi di oggetti aggiunti al metodo [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md).|  
|SCRIPTSTATE\_CONNECTED|Lo script viene caricato e connessi per gli eventi di affondamento.|  
|SCRIPTSTATE\_DISCONNECTED|Lo script viene caricato e presenta uno stato in fase di esecuzione, ma temporaneamente è disconnesso dagli eventi di affondamento.|  
|SCRIPTSTATE\_CLOSED|Lo script è stato chiuso.  Il motore di scripting più funzioni e non restituisce gli errori per la maggior parte dei metodi.|  
  
## Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)