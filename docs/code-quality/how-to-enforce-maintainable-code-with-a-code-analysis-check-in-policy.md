---
title: "Procedura: Applicare codice di facile manutenibilit&#224; con criteri di archiviazione dell&#39;analisi del codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analisi codice, criteri di archiviazione"
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# Procedura: Applicare codice di facile manutenibilit&#224; con criteri di archiviazione dell&#39;analisi del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli sviluppatori possono utilizzare lo strumento metrica codice per misurare la complessità e la manutenibilità del codice, ma non possono richiamare la metrica del codice nei criteri di archiviazione.  Tuttavia, un team può abilitare le regole dell'analisi del codice che verificano la conformità del codice agli standard della metrica del codice e applicare le regole tramite i criteri di archiviazione.  Per ulteriori informazioni sulla metrica del codice, vedere [Valori della metrica del codice](../code-quality/code-metrics-values.md).  
  
 Gli sviluppatori possono abilitare le regole Profondità dell'ereditarietà, Accoppiamenti di classi, Indice di manutenibilità e Complessità per applicare il codice di facile manutenibilità tramite i criteri di archiviazione dell'analisi del codice.  Le quattro regole sono disponibili nella categoria "Regole di manutenibilità" nell'editor dei criteri analisi codice.  
  
 Gli amministratori del controllo della versione per [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] possono aggiungere le regole di manutenibilità dell'analisi del codice ai requisiti dei criteri di archiviazione.  Questi criteri di archiviazione richiedono che gli sviluppatori eseguano l'analisi del codice sulla base di queste regole modificate prima di iniziare un'archiviazione.  
  
### Per aprire l'editor dei criteri analisi codice  
  
1.  In **Team Explorer**, fare clic con il pulsante destro del mouse sul progetto team, fare clic su **Impostazioni progetto team**, quindi su **Controllo del codice sorgente**.  
  
     Viene visualizzata la finestra di dialogo **Controllo del codice sorgente**.  
  
2.  Nella scheda **Criteri di archiviazione**, fare clic su **Aggiungi**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi criteri di archiviazione**.  
  
3.  Nell'elenco **Criteri di archiviazione**, selezionare la casella di controllo **Analisi codice** e scegliere **OK**.  
  
     Viene visualizzata la finestra di dialogo **Editor dei criteri analisi codice**.  
  
### Per attivare le regole di gestibilità dell'analisi del codice  
  
1.  Nella finestra di dialogo **Editor dei criteri analisi codice**, in **Impostazioni regole**, espandere il nodo **Regole di manutenibilità**.  
  
2.  Selezionare le caselle di controllo per le regole seguenti:  
  
    -   Profondità dell'ereditarietà: **CA1501 AvoidExcessiveInheritance** \- Soglia: avviso a una profondità superiore ai 5 livelli  
  
    -   Complessità: **CA1502 AvoidExcessiveComplexity** \- Soglia: avviso per un valore superiore a 25  
  
    -   Indice di manutenibilità: **CA1505 AvoidUnmaintainableCode** \- Soglia: avviso per un valore inferiore a 20  
  
    -   Accoppiamenti di classi: **CA1506 AvoidExcessiveClassCoupling** \- Soglia: avviso per un valore superiore a 80 per una classe e superiore a 30 per un metodo  
  
    -   Inoltre, se si desidera che la violazione di una regola impedisca la compilazione, selezionare la casella di controllo **Considera gli avvisi come errori** accanto alla descrizione della regola.  
  
3.  Fare clic su **OK**.  A questo punto verranno applicati i nuovi criteri alle future archiviazioni.  
  
## Vedere anche  
 [Valori della metrica del codice](../code-quality/code-metrics-values.md)   
 [Creazione e utilizzo di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)