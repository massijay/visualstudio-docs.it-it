---
title: "Interfaccia IDebugHelper | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugHelper"
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugHelper
Opera da factory per i visualizzatori oggetti e i punti di connessione semplici.  L'amministratore di processo \(PDM\) di debug implementa questa interfaccia, utilizzata dal motore di gestione di script.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugHelper` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Restituisce un Visualizzatore proprietà che esegue il wrapping di un VARIANT.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Restituisce un Visualizzatore proprietà che esegue il wrapping di un VARIANT e consente la conversione personalizzata dei valori VARIABILI o VARTYPE digitare le stringhe.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Restituisce un'interfaccia eventi che esegue il wrapping di un oggetto specificato `IDispatch`.|