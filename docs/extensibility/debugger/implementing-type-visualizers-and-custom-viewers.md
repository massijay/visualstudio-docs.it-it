---
title: "Implementazione di tipo visualizzatori e visualizzatori personalizzati | Microsoft Docs"
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
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Implementazione di tipo visualizzatori e visualizzatori personalizzati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 I visualizzatori di tipo e visualizzatori personalizzati consentono all'utente di visualizzare i dati di un determinato tipo in modo più significativo rispetto a un semplice dump esadecimale dei numeri. Un analizzatore di espressioni \(EE\) è possibile associare visualizzatori personalizzati a specifici tipi di dati o variabili. Questi visualizzatori personalizzati vengono implementati tramite l'analizzatore di Espressioni. L'analizzatore di Espressioni può inoltre supportare i visualizzatori di tipo esterno, che potrebbero provenire da un altro fornitore di terze parti o anche l'utente finale.  
  
## Discussione  
  
### Visualizzatori di tipo  
 Visual Studio richiede un elenco di visualizzatori di tipo e visualizzatori personalizzati per ogni oggetto da visualizzare nella finestra Espressioni di controllo. Un analizzatore di espressioni \(EE\) fornisce tale elenco per ogni tipo per cui intende supportare visualizzatori personalizzati e i visualizzatori di tipo. Le chiamate a [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) avviare l'intero processo di accesso ai visualizzatori personalizzati e i visualizzatori di tipo \(vedere [Visualizzazione e la visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate sulla sequenza di chiamata\).  
  
### Visualizzatori personalizzati  
 Visualizzatori personalizzati vengono implementati in EE per un tipo di dati specifici e sono rappresentati i [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaccia. Un visualizzatore personalizzato non è flessibile come un visualizzatore di tipo, poiché è disponibile solo quando è in esecuzione l'analizzatore di Espressioni che implementa tale particolare visualizzatore personalizzato. Implementazione di un visualizzatore personalizzato è più semplice rispetto all'implementazione di supporto per i visualizzatori di tipo. Tuttavia, i visualizzatori di tipo di supporto offre la massima flessibilità all'utente finale per la visualizzazione dei dati il propria. Nella parte restante di questa discussione riguarda solo i visualizzatori di tipo.  
  
## Interfacce  
 L'analizzatore di Espressioni implementa le interfacce seguenti per supportare i visualizzatori di tipo, deve essere utilizzato da Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 L'analizzatore di Espressioni utilizza le interfacce seguenti per supportare i visualizzatori di tipo:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzazione e la visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)