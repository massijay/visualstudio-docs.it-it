---
title: "Procedura: estendere il codice generato da Progettazione relazionale oggetti | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: estendere il codice generato da Progettazione relazionale oggetti
Il codice generato da [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] viene rigenerato quando vengono apportate modifiche alle classi di entità e ad altri oggetti nell'area di progettazione.A causa di questa rigenerazione, in genere tutto il codice aggiunto al codice generato viene sovrascritto quando la finestra di progettazione rigenera il codice.[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] offre la possibilità di generare file di classe parziale in cui è possibile aggiungere codice che non verrà sovrascritto.Un esempio di aggiunta di codice personalizzato al codice generato da [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] consiste nell'aggiungere la convalida di dati a classi \(di entità\) LINQ to SQL.Per informazioni, vedere [Procedura: aggiungere la convalida a classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Aggiunta di codice a una classe di entità  
  
#### Per creare una classe parziale e aggiungere codice a una classe di entità  
  
1.  Aprire o creare un nuovo file di classi LINQ to SQL \(file **.dbml**\) in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\(fare doppio clic sul file **.dbml** in **Esplora soluzioni**\/**Esplora database**\).  
  
2.  In [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fare clic con il pulsante destro del mouse sulla classe per cui si desidera aggiungere la convalida, quindi scegliere **Visualizza codice**.  
  
     Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.  
  
3.  Aggiungere il codice nella dichiarazione di classe parziale per la classe di entità.  
  
## Aggiunta di codice a un oggetto DataContext  
  
#### Per creare una classe parziale e aggiungere codice a un oggetto DataContext  
  
1.  Aprire o creare un nuovo file di classi LINQ to SQL \(file **.dbml**\) in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\(fare doppio clic sul file **.dbml** in **Esplora soluzioni**\/**Esplora database**\).  
  
2.  In [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fare clic con il pulsante destro del mouse su un'area vuota della finestra di progettazione, quindi scegliere **Visualizza codice**.  
  
     Viene aperto l'editor del codice con una classe parziale per l'oggetto DataContext.  
  
3.  Aggiungere il codice nella dichiarazione di classe parziale per l'oggetto DataContext.  
  
## Vedere anche  
 [Cenni preliminari su Progettazione relazionale oggetti](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Procedura dettagliata: aggiunta della convalida a classi di entità](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md)