---
title: "Interfaccia IProcessDebugManager | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IProcessDebugManager"
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IProcessDebugManager
Interfaccia primaria all'amministratore del processo di debug.  Tale interfaccia può creare, aggiungere, rimuovere o un'applicazione virtuale da un processo.  Può enumerare gli stack frame e i thread dell'applicazione.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IProcessDebugManager` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Crea un nuovo oggetto applicazione di debug per l'applicazione.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Restituisce un oggetto applicazione predefinito del processo corrente.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Aggiunta un'applicazione all'elenco dei computer di debug delle applicazioni in esecuzione.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Rimuove un'applicazione dall'elenco in esecuzione di un'applicazione.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Crea un nuovo supporto del documento di debug per l'applicazione.|