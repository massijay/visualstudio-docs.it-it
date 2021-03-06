---
title: "Uso di più processori per la compilazione di progetti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2d8309ead037097b8205245feabdb67c68d0d6b2
ms.lasthandoff: 02/22/2017

---
# <a name="using-multiple-processors-to-build-projects"></a>Utilizzo di più processori per la compilazione di progetti
MSBuild è in grado di trarre vantaggio dai sistemi che dispongono di più processori o di più componenti principali. Per ogni processore disponibile viene creato un processo di compilazione separato. Se, ad esempio, nel sistema sono presenti quattro processori, vengono creati quattro diversi processi di compilazione. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è in grado di elaborare queste compilazioni simultaneamente e il tempo di compilazione globale risulta quindi ridotto. Tuttavia, la compilazione parallela introduce alcune modifiche ai processi di compilazione. Questo argomento descrive queste modifiche.  
  
## <a name="project-to-project-references"></a>Riferimenti da progetto a progetto  
 Se il [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] rileva un riferimento da progetto a progetto (P2P) mentre usa processi paralleli per la compilazione di un progetto, il riferimento viene compilato una sola volta. Se due progetti presentano lo stesso riferimento P2P, questo non viene ricompilato per ogni progetto. Il motore di compilazione restituisce invece lo stesso riferimento P2P a entrambi i progetti dipendenti. Eventuali richieste successive nella sessione per la stessa destinazione offriranno lo stesso riferimento P2P.  
  
## <a name="cycle-detection"></a>Rilevamento del ciclo  
 Il rilevamento del ciclo funziona esattamente come in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, con la sola differenza che [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] può segnalarlo ora anche in un momento diverso o durante la compilazione.  
  
## <a name="errors-and-exceptions-during-parallel-builds"></a>Errori ed eccezioni durante le compilazioni parallele  
 Nelle compilazioni parallele possono verificarsi errori ed eccezioni in momenti diversi rispetto a quanto avviene nelle compilazioni non parallele e, se un progetto non viene compilato, gli altri processi di compilazione di progetti proseguono normalmente. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] non interromperà alcuna compilazione di progetti eseguita in parallelo con quella che ha avuto esito negativo. La compilazione degli altri progetti continua finché non viene completata correttamente o non si verifica un errore. Se, tuttavia, è stato abilitato <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, non verrà arrestata alcuna compilazione, anche se si è verificato un errore.  
  
## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>File di progetto Visual C++ (vcproj) e file di soluzione (sln)  
 Sia i file di progetto [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] (con estensione vcproj) sia i file di soluzione (con estensione sln) possono essere passati all'[attività MSBuild](../msbuild/msbuild-task.md). Per i progetti [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] viene chiamato VCWrapperProject e quindi viene creato il progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] interno, mentre per le soluzioni [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] viene chiamato SolutionWrapperProject e quindi viene creato il progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] interno. In entrambi casi, il progetto risultante viene considerato come qualsiasi altro progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## <a name="multi-process-execution"></a>Esecuzione di più processi  
 Quasi tutte le attività correlate alla compilazione richiedono che la directory corrente rimanga costante durante l'intero processo di compilazione per evitare errori di percorso. Pertanto, non è possibile eseguire progetti su thread diversi in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], poiché in questo caso verrebbero create più directory.  
  
 Per evitare questo problema ma consentire comunque compilazioni su più processori, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usa il cosiddetto "isolamento dei processi". Con questa tecnica, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] può creare un massimo di `n` processi, dove `n` è uguale al numero di processori disponibili nel sistema. Se, ad esempio, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] compila una soluzione in un sistema con due processori, vengono creati solo due processi di compilazione. Questi processi vengono poi riusati per compilare tutti i progetti nella soluzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)   
 [Attività](../msbuild/msbuild-tasks.md)
