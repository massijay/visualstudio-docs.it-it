---
title: "IDebugDocumentText::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetText"
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetText
Recupera i caratteri e\/o gli attributi del carattere associati a un intervallo di posizione del carattere.  
  
## Sintassi  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### Parametri  
 `cCharacterPosition`  
 \[in\] posizione dell'intervallo di posizione del carattere.  
  
 `pcharText`  
 \[in, out\] buffer di testo del carattere su.  Il buffer deve essere sufficiente per contenere i caratteri `cMaxChars`.  Se questo parametro è NULL, il metodo non restituisce i caratteri.  
  
 `pstaTextAttr`  
 \[in, out\] buffer di attributi del carattere su.  Il buffer deve essere sufficiente per contenere i caratteri `cMaxChars`.  Se questo parametro è NULL, il metodo non restituisce gli attributi.  
  
 `pcNumChars`  
 \[in, out\] numero di caratteri\/attributi restituiti.  Questo parametro deve essere impostato su zero prima di chiamare questo metodo.  
  
 `cMaxChars`  
 \[in\] numero di caratteri nell'intervallo di posizione del carattere.  Specifica inoltre il numero massimo di caratteri per restituire.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo recupera i caratteri e\/o gli attributi del carattere associati a una posizione di carattere variano.  L'intervallo di posizione di carattere è specificato da una posizione di carattere e da una serie di caratteri.  
  
## Vedere anche  
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Enumerazione SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)