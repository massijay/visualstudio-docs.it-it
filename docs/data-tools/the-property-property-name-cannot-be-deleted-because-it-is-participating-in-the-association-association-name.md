---
title: "Impossibile eliminare la propriet&#224; &lt;nome propriet&#224;&gt; perch&#233; partecipa all&#39;associazione &lt;nome associazione&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Impossibile eliminare la propriet&#224; &lt;nome propriet&#224;&gt; perch&#233; partecipa all&#39;associazione &lt;nome associazione&gt;
La proprietà selezionata viene impostata come **Proprietà associazione** per l'associazione tra le classi indicate nel messaggio di errore.Le proprietà non possono essere eliminate se partecipano a un'associazione tra classi di dati.  
  
 Impostare **Proprietà associazione** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.  
  
### Per correggere l'errore  
  
1.  Selezionare la linea di associazione in Progettazione relazionale oggetti che connette le classi di dati indicate nel messaggio di errore.  
  
2.  Fare doppio clic sulla linea per aprire la finestra di dialogo **Editor di associazione**.  
  
3.  Rimuovere la proprietà dalle **Proprietà associazione**.  
  
4.  Provare a eliminare nuovamente la proprietà.  
  
## Vedere anche  
 [Cenni preliminari su Progettazione relazionale oggetti](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procedura: creare un'associazione \(relazione\) tra classi LINQ to SQL \(Progettazione relazionale oggetti\)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)