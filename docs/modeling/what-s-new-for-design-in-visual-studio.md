---
title: "Novità relative alla progettazione in Visual Studio | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 32
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
ms.sourcegitcommit: 17bc5792d4fa9fac0b97705e61372dcc884c82a2
ms.openlocfilehash: 2704914ab8607e0a7442a45589e6a6cab08b7338
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-for-design-in-visual-studio"></a>Novità relative alla progettazione in Visual Studio

## <a name="live-dependency-validation"></a>Convalida della dipendenza Live

La rimozione di dipendenze indesiderate è una parte importante della gestione del debito tecnico.
La convalida delle dipendenze è ora incluso, fornendo informazioni precise sui problemi e beneficiano completamente le nuove funzionalità nell'elenco errori e nell'editor.

![Convalida della dipendenza Live in azione](~/modeling/media/dep-validation-whatsnew-01.png)

L'esperienza di creazione e modifica è stata modificata per modificare più facilmente individuabili e più accessibile, la terminologia da "Diagramma livello" a "Diagramma dipendenza" convalida della dipendenza.

Il **architettura** menu contiene ora un comando per creare direttamente un diagramma di dipendenze:

![Elemento dipendenza Live menu architettura](~/modeling/media/dep-validation-whatsnew-02.png)

... e i nomi delle proprietà di un livello in un diagramma di dipendenze e le relative descrizioni, sono stati modificati per renderli più significativi:

![Nomi delle proprietà di dipendenza Live aggiornato](~/modeling/media/dep-validation-whatsnew-03.png)

Verranno visualizzati l'impatto delle modifiche immediatamente nei risultati di analisi per il codice nella soluzione corrente ogni volta che si salva il diagramma. Non devi più attendere il completamento del comando "Convalidare le dipendenze".

Per ulteriori informazioni, vedere [questo post di blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/). 
 
## <a name="uml-designers-have-been-removed"></a>Finestre di progettazione UML sono stati rimossi

Le finestre di progettazione UML sono stati rimossi da questa versione di Visual Studio Enterprise.

* Diagrammi UML vengono presentati come file XML
* Esplora modelli UML non esiste più
* I riferimenti non vengono più utilizzati per la convalida delle dipendenze di progetto di modello
* Il nodo "Riferimenti livello" in Esplora soluzioni non viene più visualizzato
* L'azione di compilazione "Convalida" in un diagramma di dipendenza (Layer) non viene più utilizzato, l'attività di compilazione è stata rimossa. 
* La struttura del progetto viene mantenuta per sequenze di andata e ritorno tra versioni
* È comunque aprire, creare, modificare e salvare un diagramma di dipendenza (Layer) come XML
* Elementi di lavoro TFS collegati a un diagramma di dipendenza (Layer) non sono accessibili nell'area di progettazione
* Back-collegamento a un livello o DSL non è più supportato 
* Estendibilità UML Modeling SDK non è più supportata

Tuttavia, il supporto per visualizzare l'architettura di codice .NET e C++ è disponibile tramite [mappe codici](map-dependencies-across-your-solutions.md)e i miglioramenti significativi alla convalida della dipendenza descritte in precedenza.

Se si utilizza un significativo delle finestre di progettazione UML, è possibile continuare a utilizzare Visual Studio 2015 o versioni precedenti quando si sceglie uno strumento alternativo per le esigenze UML.

Per ulteriori informazioni, vedere [questo post di blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/). 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>Supporto della versione per gli strumenti di architettura e modellazione  

Visual Studio è disponibile in diverse versioni. Non tutte le versioni forniscono il supporto per gli strumenti di architettura e modellazione. La tabella seguente illustra la disponibilità di ogni strumento.  
  
|**Funzionalità**|**Enterprise**|**Professional**|**Community**|**Express**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**Mappe codici**|Sì|Vedere la nota (1)|-|-|  
|**Diagrammi di dipendenza**|Sì|Vedere la nota (2)|Vedere la nota (2)|-|  
|**Grafici diretti** (diagrammi DGML)|Sì|Sì|Sì|-|  
|**Clone di codice**|Sì|-|-|-|  
  
Nota (1): supporta solo la lettura delle mappe del codice, l'applicazione di filtri alle mappe del codice, l'aggiunta di nuovi nodi generici e la creazione di un grafico diretto da una selezione.

Nota (2): Supporta solo la lettura di diagrammi di dipendenza.

