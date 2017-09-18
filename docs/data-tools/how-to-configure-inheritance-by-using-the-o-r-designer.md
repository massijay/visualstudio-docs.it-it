---
title: "Procedura: configurare l&#39;ereditariet&#224; utilizzando Progettazione relazionale oggetti | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 4
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: configurare l&#39;ereditariet&#224; utilizzando Progettazione relazionale oggetti
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) supporta il concetto di ereditarietà a tabella singola poiché è spesso implementato in sistema relazionali. Nell'ereditarietà a tabella singola, esiste un database singolo che contiene campi sia per le informazioni padre che figlio.Insieme ai dati relazionali, una colonna discriminatore contiene il valore che determina la classe a cui appartiene un record.  
  
 Ad esempio, si consideri una tabella Persons che contiene tutte le persone impiegate in una società,alcune delle quali sono dipendenti mentre altre sono manager.La tabella Persons contiene una colonna denominata `EmployeeType` con un valore 1 per i manager e un valore 2 per i dipendenti e che costituisce la colonna discriminatore.In questo scenario è possibile creare una sottoclasse di dipendenti e popolarla solo con i record che hanno un valore 2 in `EmployeeType`.È anche possibile rimuovere le colonne non appropriate da ognuna delle classi.  
  
 La creazione di un modello a oggetti che utilizza l'ereditarietà \(e corrisponde ai dati relazionali\) può generare una certa confusione.Nella procedura riportata di seguito vengono illustrati i passaggi necessari per la configurazione dell'ereditarietà con Progettazione relazionale oggetti.Poiché potrebbe essere difficile seguire passaggi generici senza fare riferimento a una tabella e a colonne esistenti, viene fornita una procedura dettagliata in cui vengono utilizzati dati effettivi.Per istruzioni dettagliate per la configurazione dell'ereditarietà mediante [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], vedere [Procedura dettagliata: creazione di classi LINQ to SQL utilizzando l'ereditarietà a tabella singola \(Progettazione relazionale oggetti\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
### Per creare classi di dati ereditate  
  
1.  Aprire [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] aggiungendo una voce **Classi LINQ to SQL** a un progetto Visual Basic o C\# esistente.  
  
2.  Trascinare la tabella che si desidera utilizzare come classe di base in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Trascinare una seconda copia della tabella in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e rinominarla.In tal modo si otterrà la classe derivata o sottoclasse.  
  
4.  Fare clic su **Inheritance** nella scheda **Progettazione relazionale oggetti** della **Casella degli strumenti**, quindi selezionare la sottoclasse \(ovvero, la tabella rinominata\) e connetterla alla classe di base.  
  
    > [!NOTE]
    >  Fare clic sull'elemento **Inheritance** nella **Casella degli strumenti** e rilasciare il pulsante del mouse, selezionare la seconda copia della classe creata nel passaggio 3, quindi selezionare la prima classe creata nel passaggio 2.La freccia della linea di ereditarietà punterà alla prima classe.  
  
5.  In ogni classe eliminare le proprietà dell'oggetto che non si desidera visualizzare e che non sono utilizzate per le associazioni.Se si tenta di eliminare le proprietà dell'oggetto utilizzate per le associazioni, verrà restituito un errore: [Impossibile eliminare la proprietà \<nome proprietà\> perché partecipa all'associazione \<nome associazione\>](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Poiché una classe derivata eredita le proprietà definite nella relativa classe di base, non è possibile definire le stesse colonne in ogni classe\(le colonne vengono implementate come proprietà\). Per consentire la creazione di colonne nella classe derivata, è possibile impostare il modificatore di ereditarietà sulla proprietà della classe di base.Per ulteriori informazioni, vedere [NOT IN BUILD: Overriding Properties and Methods](http://msdn.microsoft.com/it-it/2167e8f5-1225-4b13-9ebd-02591ba90213).  
  
6.  Selezionare la linea di ereditarietà in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
7.  Nella finestra **Proprietà** impostare **Discriminator Property** sul nome di colonna utilizzato per distinguere i record nelle classi.  
  
8.  Impostare la proprietà **Derived Class Discriminator Value** sul valore nel database che designa il record come tipo ereditato\(si tratta del valore archiviato nella colonna discriminatore e utilizzato per designare la classe ereditata\).  
  
9. Impostare la proprietà **Base Class Discriminator Value** sul valore che designa il record come tipo di base\(si tratta del valore archiviato nella colonna discriminatore e utilizzato per designare la classe di base\).  
  
10. È anche possibile impostare eventualmente la proprietà **Inheritance Default** per definire un tipo in una gerarchia di ereditarietà utilizzata durante il caricamento di righe che non corrispondono ad alcun codice di ereditarietà definito.In altre parole, se un record include un valore nella relativa colonna discriminatore che non corrisponde al valore nelle proprietà **Derived Class Discriminator Value** o **Base Class Discriminator Value**, il record verrà caricato nel tipo designato come **Valore predefinito di ereditarietà**.  
  
## Vedere anche  
 [Cenni preliminari su Progettazione relazionale oggetti](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/it-it/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL utilizzando l'ereditarietà a tabella singola \(Progettazione relazionale oggetti\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/it-it/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Ereditarietà](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)