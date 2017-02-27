---
title: "Impossibile eliminare la propriet&#224; &lt;nome propriet&#224;&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# Impossibile eliminare la propriet&#224; &lt;nome propriet&#224;&gt;
Impossibile eliminare la proprietà \<nome proprietà\> perché è utilizzata come proprietà Discriminator per l'ereditarietà tra \<nome classe\> e \<nome classe\>  
  
 La proprietà selezionata viene impostata come **Discriminator Property** per l'ereditarietà tra le classi indicate nel messaggio di errore.Le proprietà non possono essere eliminate se partecipano alla configurazione dell'ereditarietà tra le classi di dati.  
  
 Impostare **Discriminator Property** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.  
  
### Per correggere l'errore  
  
1.  In Progettazione relazionale oggetti selezionare la linea di ereditarietà che connette le classi di dati indicate nel messaggio di errore.  
  
2.  Impostare **Discriminator Property** su una diversa proprietà.  
  
3.  Provare a eliminare nuovamente la proprietà.  
  
## Vedere anche  
 [Procedura: configurare l'ereditarietà utilizzando Progettazione relazionale oggetti](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Ereditarietà delle classi di dati \(Progettazione relazionale oggetti\)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL utilizzando l'ereditarietà a tabella singola \(Progettazione relazionale oggetti\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)