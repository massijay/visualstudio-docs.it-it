---
title: "Questo metodo correlato &#232; il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Questo metodo correlato &#232; il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione
Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione.Se viene eliminato, verranno eliminati anche questi metodi.Continuare?  
  
 Il metodo `DataContext` selezionato viene utilizzato attualmente come uno dei metodi di inserimento, aggiornamento o eliminazione per una delle classi di entità in Progettazione relazionale oggetti.L'eliminazione del metodo selezionato determinerà, per la classe di entità che lo stava utilizzando, il ripristino del comportamento in fase di esecuzione predefinito per l'esecuzione dei comandi di inserimento, aggiornamento o eliminazione durante un aggiornamento.  
  
### Per eliminare il metodo selezionato e determinare l'utilizzo degli aggiornamenti in fase di esecuzione da parte della classe di entità  
  
-   Scegliere **Sì**.  
  
     Il metodo selezionato viene eliminato e per tutte le classi che utilizzavano tale metodo per l'override del comportamento di aggiornamento viene ripristinato l'utilizzo del comportamento in fase di esecuzione LINQ to SQL predefinito.  
  
### Per chiudere la finestra di messaggio e lasciare invariato il metodo selezionato  
  
-   Scegliere **No**.  
  
     La finestra di messaggio viene chiusa e non vengono apportate modifiche.  
  
## Vedere anche  
 [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: assegnare stored procedure per l'esecuzione dei comandi di aggiornamento, inserimento ed eliminazione \(Progettazione relazionale oggetti\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Cenni preliminari su Progettazione relazionale oggetti](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)