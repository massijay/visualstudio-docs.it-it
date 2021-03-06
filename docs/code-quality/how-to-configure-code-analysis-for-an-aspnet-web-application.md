---
title: 'Procedura: configurare l''analisi codice per un''applicazione Web ASP.NET | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dbc2ba8f78cc8f38bce62adbd3d91604875bffa3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Procedura: configurare l'analisi del codice per un'applicazione Web ASP.NET
In [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] e [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] è possibile selezionare da un elenco di analisi del codice *set di regole* da applicare al [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazione Web. Il set di regole predefinito è regole minime consigliate di Microsoft. È possibile selezionare un altro set di regole da applicare al sito Web.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Per configurare un set di regole per un progetto del framework di pagine ASP.NET  
  
1.  Selezionare il sito Web in **Esplora**.  
  
2.  Nel **Analizza** menu, fare clic su **Configura analisi codice per il sito Web**.  
  
3.  Se è stata selezionata la soluzione e la soluzione contiene più di un progetto, selezionare il sistema operativo di destinazione e di configurazione compilazione dal **configurazione** e **piattaforma** Elenca.  
  
4.  Per ogni progetto nella soluzione, scegliere il **del Set di regole** colonna e quindi scegliere il nome della regola impostata per l'esecuzione.  
  
5.  Per impostazione predefinita, l'analisi del codice viene eseguito in tutti i progetti nella soluzione. Per disabilitare o abilitare l'analisi del codice per un particolare progetto, seguire questi passaggi:  
  
    1.  Fare doppio clic sul nome del progetto e quindi fare clic su proprietà.  
  
    2.  Selezionare o deselezionare il **Attiva analisi codice** casella di controllo. È anche possibile eseguire manualmente l'analisi del codice selezionando **Esegui analisi del codice sul sito Web** dal **Analizza** menu.  
  
6.  Nel **eseguire il set di regole** elenco a discesa, attenersi alla procedura seguente:  
  
    -   Selezionare il set di regole che si desidera utilizzare.  
  
    -   Selezionare  **\<Sfoglia >** per specificare set di una regola personalizzata esistente non è presente nell'elenco.  
  
    -   Definire un set di regole personalizzato. Per ulteriori informazioni, vedere [la creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md).