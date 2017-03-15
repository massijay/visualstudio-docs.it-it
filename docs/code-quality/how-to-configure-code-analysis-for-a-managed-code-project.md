---
title: "Procedura: Configurare l&#39;analisi codice per un progetto di codice gestito | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.csvb"
helpviewer_keywords: 
  - "analisi codice, selezione di set di regole"
  - "analisi codice, set di regole"
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 33
---
# Procedura: Configurare l&#39;analisi codice per un progetto di codice gestito
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] e [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], è possibile scegliere da un elenco i *set di regole* da applicare a un progetto di codice gestito.  Il set di regole predefinito è il set Regole minime consigliate Microsoft.  È possibile applicare un altro set di regole a un progetto o a tutti i progetti di una soluzione.  
  
> [!NOTE]
>  Per informazioni sulla modalità di configurazione di un set di regole per applicazioni Web ASP.NET, vedere [Procedura: configurare l'analisi del codice per un'applicazione Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### Per configurare un set di regole per un progetto .NET Framework  
  
1.  In **Esplora soluzioni** fare clic sul progetto.  
  
2.  Dal menu **Analizza** scegliere **Configura analisi codice per** *ProjectName*.  
  
3.  Negli elenchi **Configurazione** e **Piattaforma** fare clic sulla configurazione di compilazione e sulla piattaforma di destinazione.  
  
4.  Per eseguire l'analisi codice ogni volta che il progetto viene compilato con la configurazione selezionata, selezionare la casella di controllo **Abilita analisi codice in fase di compilazione \(definisce la costante CODE\_ANALYSIS\)**.  È inoltre possibile eseguire manualmente l'analisi codice aprendo il menu **Analizza** e facendo clic su **Esegui analisi del codice su** *ProjectName*.  
  
5.  Per impostazione predefinita, l'analisi codice non segnala gli avvisi correlati a codice generato automaticamente da strumenti esterni.  Per visualizzare gli avvisi da codice generato, deselezionare la casella di controllo **Non visualizzare i risultati del codice generato**.  
  
    > [!NOTE]
    >  Questa opzione non nasconde gli errori e gli avvisi dell'analisi del codice correlati a codice generato quando gli errori e gli avvisi vengono visualizzati in moduli e modelli.  È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.  
  
6.  Nell'elenco **Esegui set di regole** effettuare una delle operazioni seguenti:  
  
    -   Fare clic sul set di regole che si desidera utilizzare.  
  
    -   Selezionare **\<Sfoglia...\>** per specificare un set di regole personalizzato esistente non incluso nell'elenco.  
  
    -   Definire un set di regole personalizzato.  
  
         Per ulteriori informazioni, vedere [Creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## Vedere anche  
 [Procedura dettagliata: Configurazione e uso di un set di regole personalizzate](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)