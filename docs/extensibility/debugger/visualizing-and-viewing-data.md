---
title: "Visualizzazione e la visualizzazione dei dati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Debugging SDK], la visualizzazione dei dati"
  - "debug [Debugging SDK], la visualizzazione dei dati"
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Visualizzazione e la visualizzazione dei dati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Digitare i dati correnti dei visualizzatori di personalizzati e dei visualizzatori in modo da rapidamente significativa allo sviluppatore.  L'analizzatore di \(EE\) espressioni può supportare i visualizzatori di terze parti del tipo nonché fornire i propri visualizzatori personalizzati.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina il numero di visualizzatori di tipi e visualizzatori personalizzati sono associati al tipo di oggetto chiamando [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) il metodo.  Se c " è almeno un visualizzatore del tipo o visualizzatore \(disponibile, in Visual Studio [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) viene chiamato il metodo per recuperare un elenco dei visualizzatori e visualizzatori \(in realtà, un elenco di `CLSID`oggetti che implementa i visualizzatori e i visualizzatori\) e li presenta all'utente.  
  
## Visualizzatori di supporto del tipo  
 Sono disponibili diverse interfacce che l'EE deve implementare per supportare i visualizzatori di tipi.  Queste interfacce possono essere suddivise in due categorie principali: quelli che sono elencati i visualizzatori di tipi e quelli che accedono ai dati della proprietà.  
  
### Elenco di visualizzatori di tipi  
 L'EE supporta elenco di visualizzatori di tipi nell'implementazione di `IDebugProperty3::GetCustomViewerCount` e di `IDebugProperty3::GetCustomViewerList`.  questi metodi passano la chiamata ai metodi corrispondenti [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) Viene ottenuto chiamando [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md).  Questo metodo richiede [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) l'interfaccia, che viene ottenuto [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) dall'interfaccia passata [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  `IEEVisualizerServiceProvider::CreateVisualizerService` richiede [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) anche e [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) le interfacce che sono stati passati a `IDebugParsedExpression::EvaluateSync`.  L'interfaccia finale per creare l'interfaccia di `IEEVisualizerService` è [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) l'interfaccia, che l'EE implementa.  Questa interfaccia consente le modifiche da apportare alla proprietà che viene visualizzata.  Tutti i dati della proprietà sono [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) incapsulati in un'interfaccia, che viene inoltre implementata dall'EE.  
  
### Accesso ai dati della proprietà  
 Accesso ai dati della proprietà viene effettuata tramite [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) l'interfaccia.  Per ottenere questa interfaccia, le chiamate di Visual Studio [QueryInterface](/visual-cpp/atl/queryinterface) alla proprietà dell'oggetto per [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) ottenere l'interfaccia \(implementata nello stesso oggetto che implementa [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) l'interfaccia\) e quindi chiama [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) il metodo per ottenere l'interfaccia di `IPropertyProxyEESide` .  
  
 Tutti i dati sono trasformati e da `IPropertyProxyEESide` l'interfaccia è incapsulato [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) nell'interfaccia.  Questa interfaccia rappresenta una matrice di byte e distribuite da Visual Studio che dall'EE.  Quando i dati di una proprietà devono essere modificati, in Visual Studio viene creato un oggetto di `IEEDataStorage` che utilizza i nuovi dati e chiamate [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) a tale oggetto dati per ottenere un nuovo oggetto di `IEEDataStorage` che, a sua volta, viene passato [InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md) per aggiornare i dati della proprietà.  `IPropertyProxyEESide::CreateReplacementObject` consente dell'EE creare un'istanza della propria classe che implementa l'interfaccia di `IEEDataStorage` .  
  
## Visualizzatori personalizzati di supporto  
 Il flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` è impostato nel campo di [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md)`dwAttrib` della struttura \(restituita da [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)una chiamata\) per indicare che l'oggetto ha un visualizzatore personalizzato.  Quando questo flag è impostato, Visual Studio ottiene [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) l'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) dall'interfaccia [QueryInterface](/visual-cpp/atl/queryinterface)utilizzando.  
  
 Se l'utente seleziona un visualizzatore personalizzato, Visual Studio crea un'istanza del visualizzatore personalizzato utilizzando `CLSID` del visualizzatore fornito con il metodo di `IDebugProperty3::GetCustomViewerList` .  Chiamate [Disponibili DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) di Visual Studio visualizzare il valore all'utente.  
  
 In genere, `IDebugCustomViewer::DisplayValue` presenta una visualizzazione di sola lettura dei dati.  Per consentire le modifiche ai dati, l'EE deve implementare un'interfaccia personalizzata che supporta la modifica di dati in un oggetto della proprietà.  Il metodo di `IDebugCustomViewer::DisplayValue` utilizza questa interfaccia per supportare modificare i dati.  Il metodo cerca l'interfaccia personalizzata sull'interfaccia di `IDebugProperty2` passata come argomento di `pDebugProperty` .  
  
## Sia visualizzatori di supporto del tipo che visualizzatori personalizzati  
 L'EE possibile supportare sia i visualizzatori di tipi che i visualizzatori personalizzati [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) nei metodi e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) .  Innanzitutto, l'EE aggiunge il numero di visualizzatori personalizzati che produce il valore restituito dal [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metodo.  In secondo luogo, l'EE associa `CLSID`i propri visualizzatori personalizzati all'oggetto restituito [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) dal metodo.  
  
## Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [Tipo visualizzatore e Visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)