---
title: 'Procedura: esclusione di avvisi di analisi codice per il codice generato | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24b94c0c4ce6031876f5ad26ce01a22299f7056a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedura: non visualizzare gli avvisi relativi all'analisi del codice generato
I compilatori di codice gestito spesso generano codice che viene aggiunto a un progetto per facilitare lo sviluppo rapido di codice. Inoltre, gli sviluppatori spesso utilizzano gli strumenti di terze parti per sviluppare rapidamente applicazioni. Questi strumenti generano anche il codice che viene aggiunto al progetto.  
  
 Si potrebbe voler visualizzare le violazioni delle regole individuate dall'analisi nel codice generato. Tuttavia, si potrebbe non si desidera visualizzarli se non è possibile visualizzare e gestire il codice che contiene la violazione.  
  
 Il **Elimina i risultati dal codice generato** casella di controllo nella pagina delle proprietà di un progetto di analisi del codice consente di selezionare se si desidera visualizzare gli avvisi di analisi del codice dal codice generato da uno strumento di terze parti.  
  
> [!NOTE]
>  Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e avvisi vengono visualizzati nel form e i modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Esclusione di avvisi per il codice generato in un progetto  
  
1.  Fare clic sul progetto in Esplora soluzioni e quindi fare clic su **proprietà**.  
  
2.  Fare clic su **l'analisi del codice**.  
  
3.  Selezionare il **Elimina i risultati dal codice generato** casella di controllo.