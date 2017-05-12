---
title: "IDebugDocumentHelper::Init | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Init
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Init"
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Init
Il metodo `Init` inizializza un supporto del documento di debug con un nome e gli attributi iniziali.  
  
## Sintassi  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### Parametri  
 `pda`  
 \[in\] l'applicazione di debug associata al documento.  
  
 `pszShortName`  
 \[in\] stringa con terminazione null che contiene il nome breve del documento.  
  
 `pszLongName`  
 \[in\] stringa con terminazione null che contiene il nome lungo del documento.  
  
 `docAttr`  
 \[in\] specifica gli attributi del documento di testo.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo inizializza un supporto del documento di debug con un nome e gli attributi iniziali.  
  
 In questo documento non viene visualizzato nella struttura ad albero fino a chiamare `IDebugDocumentHelper::Attach`.  
  
## Vedere anche  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Costanti TEXT\_DOC\_ATTR](../../winscript/reference/text-doc-attr-constants.md)