---
title: "IDebugDocumentHelper::AddDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDeferredText"
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDeferredText
Notifica al supporto che il testo specificato è disponibile, ma non fornisce i caratteri.  
  
## Sintassi  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### Parametri  
 `cChars`  
 \[in\] numero di caratteri \(Unicode\) da aggiungere.  
  
 `dwTextStartCookie`  
 \[in\] cookie host definite che rappresentano posizione iniziale di testo.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il metodo non superato.|  
  
## Note  
 Questo metodo consente all'host rinviare fornendo i caratteri per aggiungere finché non sono necessari necessario che, pur consentendo al supporto generare accurate le notifiche e le informazioni di dimensione.  Il parametro `dwTextStartCookie` è un cookie, definite dall'host, che rappresenta la posizione iniziale del testo.  Le chiamate successive a `IDebugDocumentText::GetText` devono fornire questi cookie.  Ad esempio, in un host che rappresenta il testo in byte, i cookie siano un offset di byte.  
  
 Si presuppone che una singola chiamata a `IDebugDocumentText::GetText` può ottenere i caratteri da più chiamate a `AddDeferredText`.  Le classi di supporto è possibile chiamare più volte lo stesso intervallo di caratteri posticipati.  
  
> [!NOTE]
>  Le chiamate a `AddDeferredText` non devono essere combinati con chiamate a `AddUnicodeText` o a `AddDBCSText`.  In questo caso, `E_FAIL` viene restituito.  
  
## Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)