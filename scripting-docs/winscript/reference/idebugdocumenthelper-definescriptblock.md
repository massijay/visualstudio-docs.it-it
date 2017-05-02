---
title: "IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::DefineScriptBlock"
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::DefineScriptBlock
Indica di supporto che un determinato intervallo di caratteri è un blocco di script che viene gestito nel motore di script specificato.  
  
## Sintassi  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### Parametri  
 `ulCharOffset`  
 \[in\] posizione dell'inizio del blocco di script.  
  
 `cChars`  
 \[in\] numero di caratteri nel blocco di script.  
  
 `pas`  
 \[in\] il modulo di gestione di script per questo blocco di script.  
  
 `fScriptlet`  
 \[in\] diminuisca che indica se il blocco di script è uno scriptlet.  
  
 `pdwSourceContext`  
 \[out\] il contesto di origine del blocco di script.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Uno SmartHost possibile utilizzare questo metodo quando i documenti contengono i blocchi di script incorporati.  Un motore di linguaggio possono utilizzare questo metodo se il codice contiene script incorporati per altri linguaggi.  
  
 Il modulo di gestione di script è responsabile di tutte le ricerche di contesto del codice e di colorazione della sintassi nel blocco di script.  
  
 Il metodo `DefineScriptBlock` deve essere chiamato dopo che il testo è stato aggiunto ad esempio, utilizzando il metodo `IDebugDocumentHelper::AddDBCSText` \) ma prima che il blocco di script è stato analizzato \(ad esempio, utilizzando il metodo `IActiveScriptParse ::ParseScriptText` \).  
  
## Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)