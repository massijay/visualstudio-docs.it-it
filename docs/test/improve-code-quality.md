---
title: "Migliorare la qualità del codice"
ms.custom: na
ms.date: 10/14/2016
ms.reviewer: na
ms.suite: na
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: na
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- team-based development
ms.assetid: 73baa961-c21f-43fe-bb92-3f59ae9b5945
caps.latest.revision: 39
ms.author: mlearned
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
translationtype: Human Translation
ms.sourcegitcommit: 93f70de0acfa8b5efcfe141a1f8060061a4ba15d
ms.openlocfilehash: 0c439304b8a23166293fc4cc6d984947fd51f133
ms.lasthandoff: 02/22/2017

---
# <a name="improve-code-quality"></a>Migliorare la qualità del codice
Che cos'è la qualità del codice? Precisione, manutenibilità e anche eleganza sono tutti aspetti di cui tenere conto per la creazione di codice eccellente. Indipendentemente dalla definizione, gli strumenti di test di Visual Studio consentono allo sviluppatore e al team di creare e gestire standard elevati di eccellenza del codice.  
  
 **Requirements**  
  
-   Alcuni degli strumenti e delle funzionalità descritte in questa sezione sono disponibili solo in edizioni specifiche di Visual Studio; non sono disponibili in tutte le versioni. I requisiti di edizione specifici sono elencati nella documentazione per questi strumenti e funzionalità.  
  
## <a name="in-this-section"></a>In questa sezione  
 Nella tabella seguente sono riportate descrizioni di attività comuni e collegamenti a informazioni aggiuntive sulla corretta esecuzione di queste attività.  
  
|||  
|-|-|  
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|Esplora test facilita l'integrazione degli unit test nelle procedure di sviluppo. È possibile utilizzare il framework per unit test di Microsoft o uno tra i diversi framework di terze parti o open source.|  
|[Analisi della qualità delle applicazioni](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|Gli strumenti di analisi del codice statico trovano errori di progettazione, utilizzo, gestibilità e stile nel codice C++ e gestito. Molti di questi problemi possono causare bug che sono difficili da riprodurre nell'ambiente di test standard.|  
|[Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando. Le metriche includono un indice di manutenibilità per funzioni e classi, complessità ciclomatica di funzioni, profondità dell'ereditarietà delle classi e quantità di accoppiamenti tra le classi.|  
|[PreEmptive Analytics per Team Foundation Server](http://msdn.microsoft.com/library/hh973124.aspx)|PreEmptive Analytics for TFS CE aiuta a integrare i processi di sviluppo basati su feedback nel flusso di lavoro di sviluppo. Le applicazioni reinviano automaticamente i dati di report delle eccezioni al servizio endpoint PreEmptive Analytics quando si verificano errori durante l'esecuzione. Il servizio quindi crea o aggiorna elementi di lavoro in Microsoft Team Foundation Server in base alle regole e alle soglie che vengono specificate.|  
|[PreEmptive Dotfuscator e Analytics CE](assetId:///25d195d4-9f76-4dcc-9fbb-eeb9bdca9a3f)|PreEmptive Dotfuscator è una soluzione per l'offuscamento e la compattazione .NET che consente di proteggere i programmi dalla decompilazione nonché di renderli più snelli ed efficienti.|  
  
## <a name="related-scenarios"></a>Scenari correlati  
 [Adozione di Visual Studio e Team Foundation Server per la gestione del ciclo di vita delle applicazioni](assetId:///7ae9182f-4762-4bd3-b238-39ce987932e5)  
 Se non si ha familiarità con Visual Studio Team Foundation, è possibile acquisire ulteriori informazioni sul suo utilizzo in un ambiente di sviluppo team per migliorare la produttività e ridurre i rischi correlati allo sviluppo dell'applicazione.  
  
 [Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)  
 È possibile utilizzare [!INCLUDE[vsPreExt](../test/includes/vspreext_md.md)] per gestire le problematiche e le difficoltà legate alla progettazione del software. [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] consente di modellare visivamente l'applicazione, sia nello stato attuale sia nello stato futuro. È possibile creare e gestire diagrammi con i quali visualizzare i modelli logici dell'applicazione mentre vengono mappati ai modelli fisici allo scopo di poter modificare, convalidare e analizzare il software in fase di progettazione.  
  
 [Test dell'applicazione](https://www.visualstudio.com/docs/test/overview)  
 È possibile utilizzare [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] e [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] per migliorare la produttività nell'intero ciclo di vita dei test. [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] o [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] consentono di pianificare il lavoro di test richiesto. È possibile creare, gestire, modificare ed eseguire sia test manuali che automatici. È inoltre possibile rivedere lo stato di avanzamento dei test in base al piano.  
  
 [Compilare l'applicazione](https://www.visualstudio.com/docs/build/overview)  
 È possibile utilizzare [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] per creare e gestire compilazioni automatiche per il codice. [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] consente di creare ed eliminare server per distribuire le compilazioni. Inoltre, è possibile analizzare le tendenze di compilazione.  
  
 [Tenere traccia del lavoro tramite Visual Studio Online o Team Foundation Server](https://www.visualstudio.com/docs/work/overview)  
 È possibile utilizzare [!INCLUDE[vstsTfsLong](../test/includes/vststfslong_md.md)] per pianificare e tenere traccia dei progetti sia che si utilizzi il processo Agile, il processo formale o una variazione dei due. Pianificando i progetti, tenendo traccia dello stato di avanzamento rispetto al piano e apportando le modifiche necessarie, è possibile ridurre i rischi, evitare imprevisti e gestire il costo dei progetti.
