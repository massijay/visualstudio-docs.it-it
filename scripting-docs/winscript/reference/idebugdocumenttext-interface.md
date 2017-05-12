---
title: "Interfaccia IDebugDocumentText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugDocumentText"
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugDocumentText
Fornisce l'accesso a una versione di testo al documento di debug.  Questa interfaccia vengono utilizzate le seguenti convenzioni:  
  
-   Sia le posizioni dei caratteri che i numeri di riga sono in base zero.  
  
-   Le posizioni dei caratteri rappresentano gli offset di carattere, non rappresentano gli offset di parola o di byte.  Per le API Win32, una posizione di carattere Unicode è stato sottoposto a offset.  
  
 Oltre ai metodi ereditati da `IDebugDocument`, l'interfaccia `IDebugDocumentText` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Restituisce gli attributi del documento.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Restituisce il numero di righe e il numero di caratteri nel documento.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Restituisce la posizione del carattere corrispondente al primo carattere di una riga.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Restituisce il numero di riga e, facoltativamente, l'offset del carattere nella riga che corrisponde alla posizione del carattere specificata.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Recupera i caratteri e\/o gli attributi del carattere associati a un intervallo di posizione del carattere.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Restituisce l'intervallo di posizione del carattere corrispondente a un contesto del documento.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Crea un oggetto di contesto del documento che corrisponde all'intervallo specificato di posizione del carattere.|