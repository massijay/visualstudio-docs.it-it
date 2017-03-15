---
title: Analizzare e modellare l&quot;architettura | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 127
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 98d1214d1cda81102f9e03a8ce8b83886aa2c0ec
ms.openlocfilehash: 78217396085aa5531ec2cbdd5dff522201287777
ms.lasthandoff: 02/22/2017

---
# <a name="analyze-and-model-your-architecture"></a>Analizzare e modellare l'architettura
Assicurarsi che l'applicazione soddisfi i requisiti dell'architettura tramite l'architettura di Visual Studio e strumenti per progettare e modellare l'applicazione di modellazione. 

* Comprendere più facilmente il codice del programma esistente tramite Visual Studio per visualizzare la struttura, il comportamento e le relazioni del codice. 

* Informare il team necessario per soddisfare l'esigenza di dipendenze dell'architettura.  
  
* Creare modelli con diversi livelli di dettaglio in tutto il ciclo di vita dell'applicazione nel contesto del processo di sviluppo.

Vedere [Scenario: modificare la progettazione mediante visualizzazione e modellazione](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
## <a name="to"></a>A  
  
|||  
|-|-|  
|**Visualizzare il codice**:<br /><br /> -Consente di visualizzare il codice dell'organizzazione e le relazioni creando mappe codici. Visualizzare le dipendenze tra assembly, spazi dei nomi, classi, metodi e così via.<br />-Consente di visualizzare la struttura di classi e membri per un progetto specifico tramite la creazione di diagrammi classi dal codice.<br />-Trovare conflitti tra il codice e la progettazione creando diagrammi di dipendenza per convalidare il codice.|-   [Visualizzare il codice](../modeling/visualize-code.md)<br />-   [Utilizzo di classi e altri tipi (Progettazione classi)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: Comprendere la struttura dal codice con le mappe di codice di Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Video: Convalidare le dipendenze di architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**Definire l'architettura**:<br /><br /> : Consente di definire e applicare vincoli sulle dipendenze tra i componenti del codice tramite la creazione di diagrammi di dipendenza.|-   [Video: Convalidare le dipendenze di architettura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Convalidare il sistema con i requisiti e la progettazione desiderata:**<br /><br /> : Convalida delle dipendenze del codice con diagrammi di dipendenza che descrivono l'architettura desiderata e impedire modifiche che potrebbero essere in conflitto con la progettazione.|-   [Video: Convalidare le dipendenze di architettura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Condividere modelli, diagrammi e mappe codice usando il controllo della versione di Team Foundation**:<br /><br /> -Inserire codice mappe, progetti e diagrammi deoendency nel controllo della versione di Team Foundation in modo da poterli condividere.|Se sono presenti più utenti che usano questi elementi nel controllo della versione di Team Foundation, attenersi a queste linee guida per evitare problemi di controllo della versione:<br /><br /> -   [Gestire modelli e diagrammi nel controllo della versione](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Personalizzare modelli e diagrammi**:<br /><br /> : Consente di creare il proprio linguaggio specifico di dominio.|-   [Modeling SDK per Visual Studio - linguaggi specifici di dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Generare testo usando i modelli T4**:<br /><br /> -Utilizzare blocchi di testo e la logica di controllo all'interno dei modelli per generare file di testo.<br /> -Compilazione di modelli T4 con MSBuild inclusi in Visual Studio|-   [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)|

Per informazioni sulle versioni di Visual Studio supportano ogni funzionalità, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="types-of-models-and-their-uses"></a>Tipo di modelli e relativi usi  
  
|**Tipo di modello e usi tipici**|  
|-------------------------------------|  
|**Mappe codici**<br /><br /> Le mappe codice consentono di visualizzare l'organizzazione e le relazioni nel codice.<br /><br /> Usi tipici:<br /><br /> -Esaminare il codice del programma in modo da comprendere meglio la struttura e le relative dipendenze, come aggiornarla e stimare il costo delle modifiche proposte.<br /><br /> Vedere:<br /><br /> -   [Mappare le dipendenze delle soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Usare le mappe codice per il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Trovare problemi potenziali usando analizzatori di mappe codice](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Diagramma di dipendenze**<br /><br /> Diagrammi di dipendenza consentono di definire la struttura di un'applicazione come un set di livelli o blocchi con dipendenze esplicite. È possibile eseguire la convalida per individuare i conflitti tra le dipendenze nel codice e le dipendenze in un diagramma di dipendenza.<br /><br /> Usi tipici:<br /><br /> -Stabilizzazione della struttura dell'applicazione tramite numerose modifiche durante il ciclo di vita.<br />-Individuare i conflitti di dipendenza non intenzionali prima di archiviare le modifiche apportate al codice.<br /><br /> Vedere:<br /><br /> -   [Creare diagrammi di dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md)<br />-   [Convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md)|  
|**Linguaggio specifico di dominio (DSL)**<br /><br /> Un linguaggio DSL è una notazione progettata per uno scopo specifico. In Visual Studio, è generalmente grafico.<br /><br /> Usi tipici:<br /><br /> -Consente di generare o configurare parti dell'applicazione. Per sviluppare la notazione e gli strumenti sono necessarie alcune operazioni. Il risultato può essere più adatto al dominio rispetto alla personalizzazione di un modello UML.<br />-Per progetti di grandi dimensioni o linee di prodotto in cui viene restituito l'investimento nello sviluppo di DSL e dei relativi strumenti per l'utilizzo in più progetti.<br /><br /> Vedere:<br /><br /> -   [Modeling SDK per Visual Studio - linguaggi specifici di dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>Dove è possibile ottenere altre informazioni?  
  
[Visualizzazione di Visual Studio / Forum per gli strumenti di modellazione](http://go.microsoft.com/fwlink/?LinkId=184720)  
  
## <a name="see-also"></a>Vedere anche  
 [Novità](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [Gestione del ciclo di vita delle applicazioni e DevOps](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)

