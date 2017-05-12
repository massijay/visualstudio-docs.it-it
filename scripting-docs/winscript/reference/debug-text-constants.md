---
title: "Costanti DEBUG_TEXT | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Costanti DEBUG_TEXT
Utilizzato durante [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## Sintassi  
  
```  
typedef DWORD DEBUG_TEXT;  
  
```  
  
## Costanti  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|DWORD DEBUG\_TEXT\_ISEXPRESSION|0x00000001|Indica che il testo è un'espressione con un'istruzione.  Questo flag può influire sulla modalità in cui il testo è trattato in alcuni linguaggi.|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|Se il valore restituito è disponibile, verrà utilizzato il chiamante.|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|Non consentire gli effetti collaterali.  Se questo flag è impostato, la valutazione di un'espressione non deve modificare lo stato di runtime.|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|Abilitare i punti di interruzione durante la valutazione del testo.  Se questo flag non è impostato, i punti di interruzione saranno ignorati durante la valutazione del testo.|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|Abilitare i report di errore durante la valutazione del testo.  Se questo flag non è impostato, gli errori non verranno segnalati all'host durante la valutazione.|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|Indica che deve essere valutata l'espressione in un contesto di codice invece di eseguire l'espressione stessa.|  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)