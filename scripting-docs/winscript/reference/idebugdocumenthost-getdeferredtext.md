---
title: "IDebugDocumentHost::GetDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetDeferredText"
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetDeferredText
Restituisce un intervallo di caratteri che sono stati aggiunti tramite il metodo `IDebugDocumentHelper::AddDeferredText`, nel documento originale host.  
  
## Sintassi  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### Parametri  
 `dwTextStartCookie`  
 \[in\] cookie host definite che rappresentano posizione iniziale di testo.  
  
 `pcharText`  
 \[in, out\] buffer di testo del carattere su.  Questo metodo non restituisce i caratteri se questo parametro è `NULL`.  
  
 `pstaTextAttr`  
 \[in, out\] buffer di attributi del carattere su.  Questo metodo non restituisce gli attributi se questo parametro è `NULL`.  
  
 `pcNumChars`  
 \[in, out\] indica effettivo numero di caratteri\/attributi restituiti.  Questo parametro deve essere impostato su zero prima di chiamare questo metodo.  
  
 `cMaxChars`  
 \[in\] numero massimo di caratteri da restituire.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è implementato.|  
  
## Note  
 Questo metodo può restituire `E_NOTIMPL`, se l'host non chiama `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Questo metodo restituisce il testo dal documento originale.  L'host non tiene traccia delle modifiche o altre modifiche al documento.  
  
## Vedere anche  
 [Interfaccia IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Enumerazione SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)