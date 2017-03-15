---
title: "Procedura: creare tabelle di ricerca nelle applicazioni Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "tabelle di ricerca"
  - "tabelle di ricerca, creazione"
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: creare tabelle di ricerca nelle applicazioni Windows Form
È possibile creare tabelle di ricerca trascinando il nodo principale di una tabella padre \(da [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md)\) in un controllo del form già associato alla colonna nella tabella figlio correlata.  
  
 Il termine *tabella di ricerca* indica i controlli associati a due tabelle dati correlate.  Questi controlli di ricerca consentono di visualizzare i dati a della prima tabella in base a un valore selezionato nella seconda tabella.  
  
 Si consideri, ad esempio, una tabella `Orders` in un database Sales.  Ciascun record contenuto nella tabella `Orders` include un `CustomerID` che indica il cliente che ha effettuato l'ordine.  Si tratta di una chiave esterna che punta a un record cliente nella tabella `Customers`.  In questo scenario, è necessario espandere la tabella `Orders` nella finestra **Origini dati**, impostare il nodo principale su **Dettagli**, impostare la colonna `CustomerID` in modo che utilizzi un controllo <xref:System.Windows.Forms.ComboBox> \(oppure qualsiasi altro controllo che supporti l'associazione di ricerche\) e trascinare il nodo `Orders` nel form.  Successivamente, trascinare il nodo `Customers` nel controllo associato alla colonna correlata, in questo caso il controllo <xref:System.Windows.Forms.ComboBox> associato alla colonna `CustomerID`.  
  
### Per eseguire l'associazione dati di un controllo di ricerca  
  
1.  Aprire la finestra **Origini dati**.  
  
    > [!NOTE]
    >  Le tabelle di ricerca richiedono l'esistenza di due tabelle o di due oggetti correlati nella finestra **Origini dati**.  Per ulteriori informazioni, vedere [Procedura: visualizzare dati correlati in un'applicazione Windows Form](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
2.  Espandere i nodi nella finestra **Origini dati** fino a visualizzare la tabella padre e tutte le relative colonne e la tabella correlata e tutte le relative colonne.  
  
    > [!NOTE]
    >  Il nodo della tabella figlio è il nodo che viene visualizzato come nodo figlio espandibile nella tabella padre.  
  
3.  Modificare il tipo di trascinamento della tabella figlio in **Dettagli** selezionando **Dettagli** dall'elenco di controllo del nodo della tabella figlio.  Per ulteriori informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
4.  Individuare il nodo che correla le due tabelle \(il nodo `CustomerID` riportato nell'esempio precedente\) e modificarne il tipo di trascinamento in un controllo <xref:System.Windows.Forms.ComboBox> selezionando **ComboBox** dall'elenco dei controlli.  
  
5.  Trascinare il nodo della tabella figlio principale dalla finestra **Origini dati** al form.  
  
     Nel form vengono visualizzati i controlli associati a dati \(con etichette descrittive\) e un controllo Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\).  Nella barra dei componenti sono visualizzati gli oggetti [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
6.  A questo punto, trascinare il nodo della tabella padre principale dalla finestra **Origini dati** direttamente al controllo di ricerca \(<xref:System.Windows.Forms.ComboBox>\).  
  
     In tal modo vengono infine stabilite le associazioni di ricerca.  Fare riferimento alla tabella riportata di seguito per le proprietà specifiche impostate sul controllo.  
  
    |Proprietà|Descrizione dell'impostazione|  
    |---------------|-----------------------------------|  
    |**DataSource**|In Visual Studio questa proprietà viene impostata sull'oggetto <xref:System.Windows.Forms.BindingSource> creato per la tabella trascinata nel controllo \(piuttosto che sull'oggetto <xref:System.Windows.Forms.BindingSource> creato al momento della creazione del controllo\).<br /><br /> Per effettuare eventuali modifiche, impostare tale proprietà sul <xref:System.Windows.Forms.BindingSource> della tabella che contiene la colonna da visualizzare.|  
    |**DisplayMember**|In Visual Studio la proprietà viene impostata sulla prima colonna successiva alla chiave primaria in cui è presente un tipo di dati String per la tabella trascinata nel controllo.<br /><br /> Per effettuare eventuali modifiche, impostare tale proprietà sul nome della colonna da visualizzare.|  
    |**ValueMember**|In Visual Studio la proprietà viene impostata sulla prima colonna che fa parte della chiave primaria o sulla prima colonna della tabella se non è definita alcuna chiave.<br /><br /> Per effettuare eventuali modifiche, impostare tale proprietà sulla chiave primaria nella tabella in cui è presente la colonna da visualizzare.|  
    |**SelectedValue**|In Visual Studio la proprietà viene impostata sulla colonna originale trascinata dalla finestra **Origini dati**.<br /><br /> Per effettuare eventuali modifiche, impostare tale proprietà sulla colonna chiave esterna nella tabella correlata.|  
  
## Vedere anche  
 [Procedura dettagliata: creazione di una tabella di ricerca in un'applicazione Windows Form](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)   
 [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)   
 [Procedura: creare una tabella di ricerca per un controllo ComboBox, ListBox o CheckedListBox Windows Form](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20for%20a%20Windows%20Forms%20ComboBox,%20ListBox,%20or%20CheckedListBox%20Control.md)   
 [Procedura: creare una tabella di ricerca con il componente BindingSource di Windows Form](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)