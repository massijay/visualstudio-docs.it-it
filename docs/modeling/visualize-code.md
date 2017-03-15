---
title: Visualizzare il codice | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 47
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: aa7e0e7e9bbd4d4a3f8a1b2fa82f1ce7a6ba3e53
ms.lasthandoff: 02/22/2017

---
# <a name="visualize-code"></a>Visualizzare il codice
È possibile usare gli strumenti di visualizzazione e modellazione di Visual Studio per comprendere più facilmente il codice esistente e descrivere l'applicazione. In questo modo è possibile avere un'indicazione visiva dell'impatto che le modifiche potrebbero avere sul codice e valutare il lavoro e i rischi risultanti da tali modifiche. Ad esempio:  
  
-   Per comprendere le relazioni nel codice, eseguire visivamente il mapping di tali relazioni.  
  
-   Per descrivere l'architettura del sistema e mantenere il codice coerente con la progettazione, creare diagrammi di dipendenza e convalidare codice rispetto a questi diagrammi.  
  
-   Per descrivere le strutture delle classi, creare diagrammi classi.  
  
 Questi strumenti facilitano anche la comunicazione con le persone coinvolte nel progetto. 
  
 Per informazioni sulle versioni di Visual Studio supportano ogni funzionalità, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="what-do-you-want-to-do"></a>Selezionare l'operazione da eseguire.  
  
|||  
|-|-|  
|**Analizzare il codice e relative relazioni:**<br /><br /> Eseguire il mapping delle relazioni tra parti di codice specifiche.<br /><br /> Ottenere una panoramica delle relazioni nel codice per l'intera soluzione.<br /><br /> **Nota**: in questa versione di Visual Studio, il termine *mappa codice* è usato al posto di *grafico dipendenze*.|-   [Mappare le dipendenze delle soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Usare le mappe codice per il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Trovare problemi potenziali usando analizzatori di mappe codice](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**Comprendere le strutture di classe:**<br /><br /> Visualizzare la struttura delle classi in un progetto mediante la creazione di diagrammi classi dal codice.|[Procedura: Aggiungere diagrammi classi ai progetti (Creazione classi)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**Descrivere la progettazione di alto livello del sistema e convalidare codice rispetto a tale progettazione:**<br /><br /> Descrivere la progettazione di alto livello del sistema e le dipendenze previste mediante la creazione di diagrammi di dipendenza. Convalidare il codice rispetto a tale progettazione per garantire che le dipendenze nel codice rimangano coerenti con la progettazione.|-   [Creare diagrammi di dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md)<br />-   [Diagrammi di dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md)<br />-   [Convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>Risorse esterne  
  
|**Categoria**|**Collegamenti**|  
|------------------|---------------|  
|**Forum**|-   [Visualizzazione di Visual Studio / strumenti di modellazione](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visualizzazione di Visual Studio / Modeling SDK (strumenti DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blog**|[Visual Studio ALM e Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Registrazioni e articoli tecnici**|[Forum MSDN sull'architettura](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Vedere anche  
 [Scenario: Modificare la progettazione mediante visualizzazione e modellazione](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [L'analisi e la modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)   
 [L'architettura dell'applicazione del modello](../modeling/model-your-app-s-architecture.md)   
 [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

