---
title: "Procedura: non visualizzare gli avvisi relativi all&#39;analisi del codice generato | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedura: non visualizzare gli avvisi relativi all&#39;analisi del codice generato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I compilatori di codice gestito spesso generano codice che viene aggiunto a un progetto per facilitare un rapido sviluppo del codice.  Inoltre, gli sviluppatori spesso utilizzano strumenti di terze parti che consentono lo sviluppo rapido delle applicazioni.  Tali strumenti generano anche codice che viene aggiunto al progetto.  
  
 Può essere necessario visualizzare le violazioni delle regole che l'analisi del codice individua nel codice generato.  Tuttavia, se non è possibile visualizzare e gestire il codice contenente la violazione, è preferibile non visualizzare le violazioni.  
  
 La casella di controllo **Non visualizzare i risultati del codice generato** nella pagina delle proprietà Analisi codice di un progetto consente di scegliere se visualizzare o meno gli avvisi di analisi del codice generato con uno strumento di terze parti.  
  
> [!NOTE]
>  Questa scelta non nasconde comunque gli errori dell'analisi del codice e gli avvisi da codice generato quando gli errori e gli avvisi vengono visualizzati in moduli e modelli.  È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.  
  
### Per non visualizzare gli avvisi per il codice generato in un progetto  
  
1.  Fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni, quindi scegliere **Proprietà**.  
  
2.  Fare clic su **Analisi codice**.  
  
3.  Selezionare la casella di controllo **Non visualizzare i risultati del codice generato**.