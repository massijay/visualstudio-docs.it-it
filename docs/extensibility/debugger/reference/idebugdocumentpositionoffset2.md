---
title: "IDebugDocumentPositionOffset2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugDocumentPositionOffset2"
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Rappresenta una posizione in un file di origine come offset del carattere.  
  
## Sintassi  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## Note per gli implementatori  
 Implementato dall'IDE e utilizzato dai motori di debug.  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi di `IDebugDocumentPositionOffset2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetRange](../Topic/IDebugDocumentPositionOffset2::GetRange.md)|Recupera l'intervallo per il percorso del documento corrente.|  
  
## Note  
 Ciò restituisce le stesse informazioni di [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ma negli offset di `char` dall'inizio del documento.  Questo approccio il documento come potrà esistere in un disco, ovvero, una matrice unidimensionale di caratteri, anziché la riga e delle informazioni sulle colonne che normalmente vengono restituite.  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)