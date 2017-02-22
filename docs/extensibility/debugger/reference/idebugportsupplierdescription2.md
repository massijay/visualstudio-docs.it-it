---
title: "IDebugPortSupplierDescription2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugPortSupplierDescription2"
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Consente all'interfaccia utente di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] per visualizzare il testo nella sezione di **informazioni di trasporto** della finestra di dialogo di **Connettersi da elaborare** .  
  
## Sintassi  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata da fornitori di porte.  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi di `IDebugPortSupplierDescription2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera la descrizione e i metadati di descrizione per il fornitore di porte.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll