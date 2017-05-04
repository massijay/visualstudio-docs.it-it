---
title: "IDebugDocumentHelper::SetDefaultTextAttr | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetDefaultTextAttr
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetDefaultTextAttr"
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetDefaultTextAttr
Imposta gli attributi predefiniti da utilizzare per il testo non in un blocco di script.  
  
## Sintassi  
  
```  
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### Parametri  
 `staTextAttr`  
 Attributi di testo di origine predefiniti.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 A meno che gli attributi predefiniti vengono modificate con questo metodo, gli attributi predefiniti di testo all'esterno di un blocco di script è SOURCETEXT\_ATTR\_NONSOURCE.  L'interfaccia utente può utilizzare queste informazioni per contrassegnare il di fuori dei blocchi di script come di sola lettura.  
  
## Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Enumerazione SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)