---
title: "Novità &#39; s nuova per la progettazione di Visual Studio | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: "32"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: ce1172baf41cf670b253b2420f5538607addfeb7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="what39s-new-for-design-in-visual-studio"></a>Novità &#39; s nuova per la progettazione di Visual Studio

## <a name="live-dependency-validation"></a>Convalida della dipendenza in tempo reale

La rimozione di dipendenze indesiderate è una parte importante della gestione del debito tecnico.
Convalida in tempo reale delle dipendenze è incluso, che fornisce informazioni dettagliate sui problemi e beneficiano completamente le nuove funzionalità nell'elenco errori e nell'editor.

![Convalida della dipendenza in tempo reale in azione](media/dep-validation-whatsnew-01.png)

L'esperienza di creazione e modifica è stata modificata per apportare convalida della dipendenza di più facilmente individuabili e più facilmente accessibile, modificare la terminologia da "Diagramma livello" a "Diagramma dipendenze".

Il **architettura** menu contiene ora un comando per creare direttamente un diagramma di dipendenze:

![Elemento di dipendenza in tempo reale dal menu di architettura](media/dep-validation-whatsnew-02.png)

... e i nomi delle proprietà di un livello in un diagramma di dipendenze e le relative descrizioni, sono stati modificati per renderli più significativi:

![Nomi delle proprietà di dipendenza in tempo reale aggiornato](media/dep-validation-whatsnew-03.png)

Verranno visualizzati l'impatto delle modifiche immediatamente nei risultati di analisi per il codice nella soluzione corrente ogni volta che si salva il diagramma. Non è necessario più attendere il completamento del comando "Convalidare dipendenze".

Per ulteriori informazioni, vedere [questo post di blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/). 
 
## <a name="uml-designers-have-been-removed"></a>Finestre di progettazione UML sono state rimosse.

Le finestre di progettazione UML sono state rimosse da questa versione di Visual Studio Enterprise.

* Diagrammi UML sono ora presentati come file XML
* Esplora modelli UML non esiste più
* I riferimenti non vengono più utilizzati per la convalida della dipendenza di progetto di modello
* Il nodo "Livello Riferimenti" in Esplora soluzioni non viene più visualizzato
* L'azione di compilazione "Convalida" in un diagramma di dipendenza (Layer) non viene più utilizzato, l'attività di compilazione è stato rimosso 
* La struttura del progetto viene mantenuta per le sequenze di andata e ritorno tra versioni
* È comunque aprire, creare, modificare e salvare un diagramma di dipendenze (Layer) in formato XML
* Elementi di lavoro TFS collegati a un diagramma di dipendenze (Layer) non sono accessibili nell'area di progettazione
* Collegamento back da DSL o un livello non è più supportato 
* Non è più supportata l'estensibilità di SDK di modellazione UML

Tuttavia, il supporto per l'architettura del codice .NET e C++ di visualizzazione è disponibile tramite [mappe del codice](map-dependencies-across-your-solutions.md)e i miglioramenti significativi alla convalida dipendenza descritte in precedenza.

Se si utilizza un significativo delle finestre di progettazione UML, è possibile continuare a utilizzare Visual Studio 2015 o versioni precedenti, mentre si decide in uno strumento alternativo alle proprie esigenze UML.

Per ulteriori informazioni, vedere [questo post di blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/). 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>Supporto della versione per gli strumenti di architettura e modellazione  

Visual Studio è disponibile in diverse versioni. Non tutte le versioni forniscono il supporto per gli strumenti di architettura e modellazione. La tabella seguente illustra la disponibilità di ogni strumento.  
  
|**Funzionalità**|**Enterprise**|**Professional**|**Community**|**Express**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**Mappe codice**|Sì|Vedere la nota (1)|-|-|  
|**Diagrammi di dipendenza**|Sì|Vedere la nota (2)|Vedere la nota (2)|-|  
|**Grafici diretti** (diagrammi DGML)|Sì|Sì|Sì|-|  
|**Clone di codice**|Sì|-|-|-|  
  
Nota (1): supporta solo la lettura delle mappe del codice, l'applicazione di filtri alle mappe del codice, l'aggiunta di nuovi nodi generici e la creazione di un grafico diretto da una selezione.

Nota (2): Supporta solo la lettura diagrammi di dipendenza.
