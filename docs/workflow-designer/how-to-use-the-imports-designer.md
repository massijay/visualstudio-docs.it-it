---
title: "Procedura: utilizzare la finestra di progettazione importazioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ImportDesigner.UI"
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: utilizzare la finestra di progettazione importazioni
La finestra di progettazione importazioni consente di immettere gli spazi dei nomi per i tipi utilizzati nelle espressioni.Analogamente alle parole chiave **Imports** o **using** in Visual Basic .NET e C\#, la specifica degli spazi dei nomi nella finestra di progettazione importazioni consente di immettere semplicemente il nome di un tipo nell'espressione anziché il nome di un tipo nella versione completa.  
  
 Sulla finestra di progettazione importazioni influiscono sia le modifiche all'interfaccia utente che quelle eseguite quando viene salvato il flusso di lavoro.Quando viene salvato il flusso di lavoro, alla finestra di progettazione importazioni è possibile aggiungere automaticamente spazi dei nomi,tra cui:  
  
-   Spazi dei nomi per qualsiasi tipo utilizzato nelle dichiarazioni di variabili e argomenti.  
  
-   Spazi dei nomi per qualsiasi tipo utilizzato nelle espressioni.  
  
-   Qualsiasi altro spazio dei nomi necessario per la serializzazione del flusso di lavoro \(ad esempio, gli spazi dei nomi utilizzati da attività personalizzate rilasciate nel flusso di lavoro\).  
  
 Quando viene salvato il flusso di lavoro, è possibile notare che alcuni spazi dei nomi eliminati manualmente sono stati aggiunti di nuovo automaticamente alla finestra di progettazione importazioni a causa della logica descritta nell'elenco precedente.  
  
### Per aggiungere uno spazio dei nomi all'elenco degli spazi dei nomi importati  
  
1.  Aprire un'applicazione di servizi di flussi di lavoro WCF, un'applicazione console del flusso di lavoro o un progetto Libreria attività in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] o in un'applicazione flusso di lavoro riallocata.  
  
2.  Fare clic su **Importazioni** nella parte inferiore dell'area di disegno principale.Verrà visualizzata la finestra di progettazione importazioni.  
  
3.  Immettere o selezionare uno spazio dei nomi dal controllo dell'elenco a discesa nella parte superiore della finestra di progettazione importazioni.  
  
     Mentre si digita, viene visualizzato un elenco degli spazi dei nomi validi che corrispondono ai caratteri tipizzati.  
  
4.  Premere **Invio** per aggiungere lo spazio dei nomi all'elenco.  
  
5.  Se si desidera rimuovere uno spazio dei nomi dall'elenco, selezionarlo, quindi premere **Canc**.Si noti che è possibile eliminare uno spazio dei nomi solo se non è valido per qualsiasi motivo, ad esempio se il progetto non fa più riferimento all'assembly che lo contiene.