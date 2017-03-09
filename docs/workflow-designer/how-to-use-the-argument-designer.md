---
title: "Procedura: utilizzare la finestra di progettazione argomenti | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ArgumentDesigner.UI"
  - "System.Activities.Presentation.View.DesignTimeArgument.UI"
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: utilizzare la finestra di progettazione argomenti
Se confrontata con le versioni precedenti di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], la finestra di progettazione argomenti semplifica il flusso di dati da e verso un'attività.Per accedere alla finestra di progettazione, è possibile fare clic sul pulsante **Argomenti** nell'angolo inferiore sinistro dell'area di progettazione.La finestra di progettazione contiene un elenco degli argomenti in formato tabella, che possono essere ordinati in base alle singole intestazioni di colonna, ad eccezione della colonna **Valore predefinito**.Ogni argomento include un nome, una direzione per la proprietà in\/out\/in\-out, un tipo e un valore di espressione predefinito \(se presente\).Il nome e il valore di espressione predefinito sono campi di testo modificabili, mentre il tipo e la direzione sono elenchi a discesa.[!INCLUDE[crabout](../test/includes/crabout_md.md)] gli argomenti, vedere [Variabili e argomenti](../Topic/Variables%20and%20Arguments.md).  
  
### Per creare un nuovo argomento  
  
1.  Aprire una soluzione per flusso di lavoro o attività in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Aprire la finestra di progettazione facendo clic sul pulsante **Argomenti** nell'angolo inferiore sinistro dell'area di progettazione.Verrà visualizzata la finestra di progettazione argomenti.  
  
3.  Fare clic sulla riga vuota denominata **Crea argomento**.In questo modo viene aggiunta una nuova riga con un nuovo argomento con i valori predefiniti seguenti: argomentox per **Nome**, in cui x è un numero intero con un valore iniziale pari a 1 che viene incrementato automaticamente per creare nomi di argomenti univoci, **In** per **Direzione** e **Stringa** per **Tipo di argomento**.Non vengono aggiunti valori per **Valore predefinito**.Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.  
  
    > [!NOTE]
    >  Per eliminare un argomento, selezionarlo facendo clic su di esso, quindi premere **Canc**.  
  
## Vedere anche  
 [Utilizzo di Progettazione flussi di lavoro](../workflow-designer/using-the-workflow-designer.md)   
 [Variabili e argomenti](../Topic/Variables%20and%20Arguments.md)