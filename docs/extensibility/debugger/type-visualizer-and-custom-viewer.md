---
title: "Tipo visualizzatore e Visualizzatore personalizzato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], visualizzatore personalizzato"
  - "debug del Visualizzatore di tipo [debug SDK]"
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Tipo visualizzatore e Visualizzatore personalizzato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un visualizzatore del tipo è un componente che visualizza un blocco di dati in un formato specifico.  Questo formato il metodo è attivo completamente fino all'implementatore del visualizzatore, sia l'utente finale o un fornitore di terze parti di visualizzatori.  
  
 Un visualizzatore personalizzato fa parte di un analizzatore di espressioni personalizzato che visualizza un blocco di dati in un formato specifico.  Questo formato il metodo è attivo completamente fino all'implementatore del visualizzatore personalizzato, ovvero il formato spetta al responsabile dell'implementazione dell'analizzatore di \(EE\) espressioni.  
  
## Supporto per i visualizzatori di tipi in un analizzatore di espressioni  
 L'EE possibile supportare i visualizzatori del tipo supporta un set di interfacce accessibili ai visualizzatori: interfacce come [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md).  Si noti, tuttavia, che l'EE non è responsabile dell'implementazione del visualizzatore del tipo: l'EE solo consente l'accesso esterno dei visualizzatori alle informazioni sul tipo.  Tali controlli possono essere forniti con l'EE e siano installati nella posizione appropriata in Visual Studio, fornito da un altro fornitore di terze parti o anche dall'utente finale.  
  
## Supporto per i visualizzatori personalizzati in un analizzatore di espressioni  
 L'EE inoltre possibile supportare i visualizzatori personalizzati in cui l'EE stessa viene fornito il codice per visualizzare il tipo di dati.  Un visualizzatore personalizzato implementa [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) l'interfaccia, dove gestisce tutte le funzioni di visualizzare i dati formato è previsto, il visualizzatore dispone di controllo completo sulla visualizzazione e anche possibile consentire i dati da modificare.  Tutti i visualizzatori personalizzati forniti dall'EE forniti con l'EE quando il prodotto viene fornito.  
  
## Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)   
 [Il motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)