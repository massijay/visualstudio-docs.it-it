---
title: "Messaggi di errore in Progettazione flussi di lavoro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "WFDErrorMessages.UI"
  - "System.Activities.Presentation.ErrorActivity.UI"
  - "System.Activities.Presentation.View.ErrorView.UI"
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Messaggi di errore in Progettazione flussi di lavoro
In questo argomento vengono descritti i tipi dei messaggi di errore che possono verificarsi durante l'utilizzo di [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## Situazioni nelle quali si verificano gli errori in Progettazione flussi di lavoro  
 Gli errori in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] si verificano nelle situazioni seguenti:  
  
1.  È presente un errore in un'espressione.  
  
2.  Non sono stati soddisfatti i vincoli di convalida di un'attività.  
  
3.  Sono presenti errori nel file XAML che impediscono il caricamento di un'attività.  
  
4.  Sono presenti errori nel file XAML che impediscono il caricamento del flusso di lavoro.  
  
 Espressioni non valide e vincoli di convalida non possono impedire la compilazione del flusso di lavoro.La compilazione del flusso di lavoro infatti riesce, ma viene generato un oggetto <xref:System.Activities.InvalidWorkflowException> in fase di esecuzione.In presenza di errori nel file XAML, la compilazione non riesce.  
  
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], quando viene caricato un flusso di lavoro, i relativi errori vengono visualizzati nell'**elenco degli errori**.Per passare all'attività che determina l'errore, fare doppio clic su di esso nell'**elenco degli errori**.  
  
### Errori nelle espressioni  
 Un'espressione non valida viene segnalata da un cerchio rosso con un punto esclamativo bianco accanto a essa.Se si posiziona il mouse su questa icona, viene visualizzata una descrizione comandi relativa all'origine dell'errore.In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fare clic sull'espressione per visualizzare la riga che sottolinea l'origine dell'errore.Se si posiziona il mouse sul testo sottolineato, viene visualizzata una descrizione comandi relativa all'origine dell'errore.  
  
### Errori di convalida delle attività  
 Una volta soddisfatti i vincoli di convalida di un'attività, viene visualizzato un cerchio rosso con un punto esclamativo bianco nell'angolo superiore destro dell'attività.Se si posiziona il mouse su questa icona, viene visualizzata una descrizione comandi relativa all'origine dell'errore.  
  
### Errori di caricamento di XAML  
 Quando non è possibile caricare un'attività, viene visualizzata una casella rossa contenente il testo "Impossibile caricare l'attività a causa di errori nell'XAML".Ciò si verifica in genere quando non è possibile risolvere il tipo dell'attività.L'attività non valida può essere eliminata nella finestra di progettazione selezionando ed eliminando la casella rossa.  
  
### Errori di caricamento del flusso di lavoro  
 Quando non è possibile caricare un flusso di lavoro, nell'area della finestra di progettazione viene visualizzato il testo "Progettazione flussi di lavoro ha riscontrato problemi con il documento", insieme alle informazioni sull'eccezione che ha causato l'errore di caricamento del flusso di lavoro.Ciò si verifica in genere quando non è possibile analizzare il file XAML.