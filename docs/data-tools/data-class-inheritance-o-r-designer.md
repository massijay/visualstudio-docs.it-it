---
title: "Ereditariet&#224; delle classi di dati (Progettazione relazionale oggetti) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ereditariet&#224; delle classi di dati (Progettazione relazionale oggetti)
Analogamente ad altri oggetti, le classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] possono utilizzare l'ereditarietà ed essere derivate da altre classi.Nel codice è possibile specificare le relazioni di ereditarietà tra oggetti dichiarando che una classe eredita da un'altra.In un database le relazioni di ereditarietà vengono create in diversi modi.[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) supporta il concetto di ereditarietà a tabella singola in quanto viene spesso implementato nei sistemi relazionali.  
  
 Nell'ereditarietà a tabella singola è presente una singola tabella di database che contiene colonne per le classi base e derivate.Insieme ai dati relazionali, una colonna discriminante contiene il valore che determina la classe a cui appartiene uno specifico record.Ad esempio, si consideri una tabella Persons che contiene tutte le persone impiegate in una società,alcune delle quali sono dipendenti mentre altre sono manager.La tabella Persons contiene una colonna denominata Type, che presenta un valore 1 per i manager e un valore 2 per i dipendenti,e che costituisce la colonna discriminante.In questo scenario, è possibile creare una sottoclasse di dipendenti e popolare la classe solo con i record che hanno un valore 2 nella colonna Type.  
  
 Quando si configura l'ereditarietà nelle classi dell'entità utilizzando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], trascinare due volte la singola tabella che contiene i dati di ereditarietà sulla finestra di progettazione: una volta per ogni classe nella gerarchia di ereditarietà.Dopo avere aggiunto le tabelle alla finestra di progettazione, connetterle con un elemento di ereditarietà della casella degli strumenti **Progettazione relazionale oggetti**, quindi impostare le quattro proprietà di ereditarietà nella finestra **Proprietà**.  
  
## Proprietà di ereditarietà  
 Nella tabella riportata di seguito sono elencate le proprietà di ereditarietà e le rispettive descrizioni:  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|Proprietà Discriminator|Proprietà \(mappata alla colonna\) che determina a quale classe appartiene il record corrente.|  
|Valore discriminante classe base|Valore \(nella colonna definita come proprietà Discriminator\) che determina che un record fa parte della classe base.|  
|Valore discriminante classe derivata|Valore \(nella proprietà definita come proprietà Discriminator\) che determina che un record fa parte della classe derivata.|  
|Valore predefinito di ereditarietà|Classe da popolare quando il valore nella proprietà definita come **Proprietà Discriminator** non corrisponde a **Valore discriminante classe base** o a **Valore discriminante classe derivata**.|  
  
 La creazione di un modello a oggetti che utilizza l'ereditarietà e corrisponde ai dati relazionali può generare una certa confusione.Questo argomento fornisce informazioni sui concetti di base e sulle proprietà singole richieste per la configurazione dell'ereditarietà.Negli argomenti seguenti viene fornita una spiegazione più chiara di come configurare l'ereditarietà con [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
|Argomento|Descrizione|  
|---------------|-----------------|  
|[Procedura: configurare l'ereditarietà utilizzando Progettazione relazionale oggetti](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Viene descritto come configurare le classi di entità che utilizzano l'ereditarietà mediante [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|  
|[Procedura dettagliata: creazione di classi LINQ to SQL utilizzando l'ereditarietà a tabella singola \(Progettazione relazionale oggetti\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Vengono fornite istruzioni dettagliate per la configurazione delle classi di entità che utilizzano l'ereditarietà a tabella singola con [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|  
  
## Vedere anche  
 [Cenni preliminari su Progettazione relazionale oggetti](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL utilizzando l'ereditarietà a tabella singola \(Progettazione relazionale oggetti\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [Introduzione](../Topic/Getting%20Started.md)