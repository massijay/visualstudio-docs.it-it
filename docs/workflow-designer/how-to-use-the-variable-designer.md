---
title: "Procedura: utilizzare la finestra di progettazione variabili | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.DesignTimeVariable.UI"
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: utilizzare la finestra di progettazione variabili
La finestra di progettazione variabili consente di creare variabili da utilizzare in scenari di associazione dati e istruzioni condizionali.Per accedere alla finestra di progettazione è possibile fare clic sul pulsante **Variabili** nell'angolo inferiore sinistro dell'area di progettazione.La finestra di progettazione contiene un elenco di variabili in formato tabella, che possono essere ordinati in base alle singole intestazioni di colonna, ad eccezione della colonna **Valore predefinito**.Ogni variabile contiene un nome, un tipo di variabile, un ambito e un valore predefinito \(se presente\).Il nome e il valore predefinito sono campi di testo modificabili mentre il tipo e l'ambito sono elenchi a discesa.L'ambito è l'attività selezionata al momento del richiamo della finestra di progettazione variabili.Se non è possibile creare una variabile nell'ambito della selezione, l'ambito verrà impostato in modo predefinito sull'attività predecessore più vicina della selezione in modo da consentire la creazione di variabili nel relativo ambito.[!INCLUDE[crabout](../test/includes/crabout_md.md)] variabili, vedere [Variabili e argomenti](../Topic/Variables%20and%20Arguments.md).  
  
 L'ordinamento non viene applicato fino a quando l'utente non utilizza in modo esplicito uno dei controlli di ordinamento, chiude e riapre la finestra di progettazione variabili o crea un'altra variabile.  
  
### Per creare una nuova variabile  
  
1.  Aprire una soluzione per flusso di lavoro o attività in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Nell'area di progettazione selezionare un'attività nel flusso di lavoro.  
  
3.  Aprire la finestra di progettazione variabili facendo clic sul pulsante **Variabili** nell'angolo inferiore sinistro dell'area di progettazione.Verrà visualizzata la finestra di progettazione variabili.  
  
4.  Fare clic sulla riga vuota denominata **Crea variabile**.In questo modo viene aggiunta una nuova riga con una nuova variabile con i valori predefiniti seguenti: variabilex per **Nome**, dove x è un numero intero con un valore iniziale pari a 1, che viene incrementato automaticamente per creare nomi di variabili univoche, **Stringa** per **Tipo di variabile** e **Sequenza** per **Ambito**.Non vengono aggiunti valori per **Predefinito**.Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.  
  
    > [!NOTE]
    >  Per eliminare una variabile, selezionarla facendo clic su di essa, quindi premere **Canc**.  
  
## Vedere anche  
 [Utilizzo di Progettazione flussi di lavoro](../workflow-designer/using-the-workflow-designer.md)   
 [Variabili e argomenti](../Topic/Variables%20and%20Arguments.md)   
 [Procedura: utilizzare la finestra di progettazione argomenti](../workflow-designer/how-to-use-the-argument-designer.md)