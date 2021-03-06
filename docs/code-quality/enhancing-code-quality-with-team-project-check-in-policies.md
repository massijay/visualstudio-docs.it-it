---
title: "Miglioramento della qualità del codice con i criteri di controllo del progetto Team | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5b421f5512e51d83e7f6e4edfbbe2869a1484200
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Miglioramento della qualità del codice con i criteri di archiviazione del progetto team
Quando si usa il controllo della versione di Team Foundation (TFVC), è possibile creare criteri di archiviazione per i progetti team. per applicare procedure che consentono di ottimizzare il codice e lo sviluppo dei gruppi. I criteri di archiviazione sono regole che vengono impostate a livello di progetto team e applicate nei computer degli sviluppatori prima che sia consentita l'archiviazione del codice.  
  
 È possibile specificare i seguenti criteri di archiviazione del progetto team:  
  
-   **Compilazioni**: richiede che le interruzioni di compilazione create durante una compilazione vengano corrette prima di una nuova archiviazione.  
  
-   **Commenti per gli insiemi di modifiche**: richiede che gli utenti forniscano commenti quando archiviano le modifiche.  
  
-   **Analisi codice**: richiede che venga eseguita l'analisi del codice prima dell'archiviazione.  
  
-   **Elementi di lavoro**: richiede l'associazione di uno o più elementi di lavoro all'archiviazione.  
  
> [!IMPORTANT]
>  Per usare i criteri di archiviazione, è necessario essere connessi a [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)].  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto di supporto|  
|----------|------------------------|  
|**Creare e usare criteri di archiviazione:** i criteri di archiviazione vengono creati tramite Impostazioni progetto team di [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)].|[Impostare e applicare controlli di qualità](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Creare e usare criteri di archiviazione dell'analisi codice:** è possibile effettuare una selezione all'interno di un set standard di regole di analisi del codice oppure creare un set personalizzato.|[Creazione e uso di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Attività|Contenuto di supporto|  
|----------|------------------------|  
|**Configurare un ambiente di sviluppo:** prima di poter creare o modificare il codice, è necessario configurare gli ambienti di sviluppo e test usando il codice sorgente appropriato. Se si usano database, è necessario anche avere accesso alla relativa rappresentazione offline.|[Configurazione di ambienti di sviluppo](http://msdn.microsoft.com/en-us/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Usare Analisi codice nel processo di sviluppo:** i membri del team eseguono l'analisi del codice nei propri computer di sviluppo. In Visual Studio gli sviluppatori configurano ed eseguono esecuzioni dell'analisi del codice per i singoli progetti di codice, visualizzano e analizzano i problemi rilevati dalle esecuzioni e creano elementi di lavoro per gli avvisi.|[Analisi della qualità delle applicazioni](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Creare ed eseguire unit test:** gli unit test offrono a sviluppatori e tester un modo rapido per individuare errori logici nei metodi delle classi in progetti C#, Visual Basic .NET e C++. Uno unit test può essere creato una volta ed eseguito ogni volta che il codice sorgente viene modificato per assicurarsi che non siano stati introdotti bug.|[Eseguire unit test del codice](../test/unit-test-your-code.md)|  
|**Tenere traccia di elementi di lavoro e difetti:** è possibile usare elementi di lavoro per tenere traccia e gestire il lavoro e le informazioni sul progetto team. Un elemento di lavoro è un record di database che viene usato da [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] per monitorare l'assegnazione e lo stato del lavoro. Si possono usare diversi tipi di elementi di lavoro per tenere traccia di vari tipi di lavoro, ad esempio requisiti del cliente, bug del prodotto e attività di sviluppo.|[Tenere traccia del lavoro e gestire il flusso di lavoro &#91; reindirizzato &#93;](http://msdn.microsoft.com/en-us/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>Risorse esterne  
  
### <a name="guidance"></a>Materiale sussidiario  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside](http://go.microsoft.com/fwlink/?LinkID=255188) (Test per la distribuzione continua con Visual Studio 2012 - Capitolo 2: Testing unità: Test interni)