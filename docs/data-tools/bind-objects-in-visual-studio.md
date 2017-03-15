---
title: "Associazione di oggetti in Visual Studio | Microsoft Docs"
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
  - "associazione, a oggetti"
  - "dati [Visual Studio], associazione a oggetti"
  - "dati [Visual Studio], associazione oggetto"
  - "associazione oggetto"
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associazione di oggetti in Visual Studio
Visual Studio fornisce strumenti in fase di progettazione che consentono di utilizzare oggetti personalizzati \(anziché altre origini dati, quali entità, dataset e servizi\) come origine dati nell'applicazione in uso.  
  
## Requisiti degli oggetti  
 Per utilizzare gli strumenti di progettazione dati in Visual Studio, è necessario unicamente che l'oggetto disponga di almeno una proprietà pubblica.  
  
 Per essere utilizzati come origine dati per un'applicazione, generalmente gli oggetti personalizzati non richiedono un'interfaccia, costruttori o attributi specifici.  Se tuttavia si desidera trascinare l'oggetto dalla finestra **Origini dati** in un'area di progettazione per creare un controllo associato a dati, e se l'oggetto implementa l'interfaccia <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource>, l'oggetto deve disporre di un costruttore predefinito \(ovvero, un costruttore senza parametri\).  In caso contrario, Visual Studio non sarà in grado di creare un'istanza dell'oggetto origine dati e verrà visualizzato un errore quando si trascina l'elemento nell'area di progettazione.  
  
## Esempi dell'utilizzo di oggetti personalizzati come origini dati  
 Sebbene esistano molti metodi per implementare la logica dell'applicazione quando si utilizzano oggetti quali un'origine dati, le operazioni standard che è possibile semplificare utilizzando i nuovi oggetti [TableAdapter](../data-tools/tableadapter-overview.md) generati in VIsual Studio sono poche.  In questa pagina viene spiegato come implementare questi processi standard utilizzando i TableAdapter; la pagina non è destinata a essere una guida per la creazione di oggetti personalizzati.  Ad esempio, le operazioni standard riportate di seguito saranno utilizzate indipendentemente dall'implementazione specifica degli oggetti o dalla logica dell'applicazione:  
  
-   Caricamento dei dati negli oggetti \(in genere da un database\).  
  
-   Creazione di una raccolta tipizzata di oggetti.  
  
-   Aggiunta e rimozione di oggetti in una raccolta.  
  
-   Visualizzazione agli utenti dei dati degli oggetti in un form.  
  
-   Variazione\/modifica dei dati in un oggetto.  
  
-   Salvataggio dei dati dagli oggetti al database.  
  
> [!NOTE]
>  Per una migliore comprensione di tale procedura e per fornire un contesto per gli esempi di questa pagina, si consiglia di completare la seguente procedura: [Procedura dettagliata: connessione ai dati negli oggetti \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  Mediante tale procedura dettagliata è possibile creare gli oggetti di cui si è trattato in questa pagina della Guida.  
  
### Caricamento dei dati negli oggetti  
 Per questo esempio, caricare i dati negli oggetti in uso utilizzando i TableAdapter.  Per impostazione predefinita, i TableAdapter sono creati con due tipi di metodo che consentono di recuperare i dati da un database e compilare tabelle dati.  
  
-   Il metodo `TableAdapter.Fill` consente di riempire una tabella dati esistente con i dati restituiti.  
  
-   Il metodo `TableAdapter.GetData` consente di restituire una nuova tabella dati compilata con dati.  
  
 Il modo più semplice per caricare gli oggetti personalizzati con i dati consiste nel chiamare il metodo `TableAdapter.GetData`, scorrere la raccolta di righe della tabella dati restituita e popolare ciascun oggetto con i valori in ciascuna riga.  È possibile creare un metodo `GetData` che restituisce una tabella dati compilata per le query aggiunte a un TableAdapter.  
  
> [!NOTE]
>  In Visual Studio, le query del TableAdapter sono denominate `Fill` e `GetData` per impostazione predefinita; tuttavia tali nomi possono essere modificati in qualsiasi nome di metodo valido.  
  
 Nell'esempio riportato di seguito viene illustrato come scorrere le righe di una tabella dati e compilare un oggetto con i dati:  
  
 Per un esempio di codice completo, vedere [Procedura dettagliata: connessione ai dati negli oggetti \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
 [!code-cs[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### Creazione di una raccolta tipizzata di oggetti  
 È possibile creare classi di raccolte per gli oggetti in uso oppure utilizzare le raccolte tipizzate fornite in modo automatico da [Il componente BindingSource](../Topic/BindingSource%20Component.md).  
  
 Quando si crea una classe di raccolte personalizzata, è opportuno ereditarla dall'oggetto <xref:System.ComponentModel.BindingList%601>.  Questa classe generica fornisce sia la funzionalità per amministrare la raccolta, sia la possibilità di generare eventi che inviano notifiche all'infrastruttura di associazione dati in Windows Forms.  
  
 Nella raccolta generata in modo automatico nell'oggetto <xref:System.Windows.Forms.BindingSource> viene utilizzato un oggetto <xref:System.ComponentModel.BindingList%601> per la relativa raccolta tipizzata.  Se l'applicazione non richiede alcuna funzionalità aggiuntiva, sarà possibile mantenere la raccolta all'interno dell'oggetto <xref:System.Windows.Forms.BindingSource>.  Per ulteriori informazioni, vedere la proprietà <xref:System.Windows.Forms.BindingSource.List%2A> della classe <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  Se nella raccolta saranno richieste funzionalità non fornite dall'implementazione di base dell'oggetto <xref:System.ComponentModel.BindingList%601>, sarà necessario creare una raccolta personalizzata in modo da effettuare l'aggiunta alla classe come richiesto.  
  
 Nel codice riportato di seguito viene illustrato come creare la classe per una raccolta fortemente tipizzata di oggetti `Order`:  
  
 [!code-cs[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### Aggiunta di oggetti a una raccolta  
 Gli oggetti vengono aggiunti a una raccolta chiamando il metodo `Add` della classe di raccolte personalizzata oppure dell'oggetto <xref:System.Windows.Forms.BindingSource>.  
  
 Per un esempio di aggiunta a una raccolta mediante un oggetto <xref:System.Windows.Forms.BindingSource>, vedere il metodo `LoadCustomers` in [Procedura dettagliata: connessione ai dati negli oggetti \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
 Per un esempio di aggiunta di oggetti a una raccolta personalizzata, vedere il metodo `LoadOrders` in [Procedura dettagliata: connessione ai dati negli oggetti \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
> [!NOTE]
>  Il metodo `Add` viene fornito automaticamente per la raccolta personalizzata quando si eredita dall'oggetto <xref:System.ComponentModel.BindingList%601>.  
  
 Nel codice riportato di seguito viene illustrato come aggiungere oggetti alla raccolta tipizzata in un oggetto <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-cs[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 Nel codice riportato di seguito viene illustrato come aggiungere oggetti a una raccolta tipizzata che eredita da un oggetto <xref:System.ComponentModel.BindingList%601>:  
  
> [!NOTE]
>  In questo esempio la raccolta `Orders` è una proprietà dell'oggetto `Customer`.  
  
 [!code-cs[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### Rimozione degli oggetti da una raccolta  
 Gli oggetti vengono rimossi da una raccolta chiamando il metodo `Remove` oppure `RemoveAt` della classe di raccolte personalizzata oppure dell'oggetto <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  I metodi `Remove` e `RemoveAt` sono forniti automaticamente per la raccolta personalizzata quando si eredita dall'oggetto <xref:System.ComponentModel.BindingList%601>.  
  
 Nel codice riportato di seguito viene illustrato come individuare e rimuovere gli oggetti dalla raccolta tipizzata in un oggetto <xref:System.Windows.Forms.BindingSource> con il metodo <xref:System.Windows.Forms.BindingSource.RemoveAt%2A>:  
  
 [!code-cs[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### Visualizzazione dei dati degli oggetti agli utenti  
 Per visualizzare agli utenti i dati presenti negli oggetti, è necessario creare un'origine dati oggetti utilizzando [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) e quindi trascinare l'intero oggetto o le singole proprietà nel form dalla finestra **Origini dati**.  
  
 Per ulteriori informazioni sulla creazione di un'origine dati oggetti, vedere [Procedura: connettersi ai dati negli oggetti](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
 Per ulteriori informazioni sulla visualizzazione di dati degli oggetti in Windows Forms, vedere [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
### Modifica dei dati negli oggetti  
 Per modificare i dati negli oggetti personalizzati con associazione a dati ai controlli Windows Form, è sufficiente modificare i dati nel controllo associato \(oppure direttamente nelle proprietà dell'oggetto\).  L'architettura di associazione dati aggiornerà i dati nell'oggetto.  
  
 Se nell'applicazione è richiesta la traccia delle modifiche e il rollback delle modifiche proposte ai relativi valori originali, sarà necessario implementare questa funzionalità nel modello a oggetti in uso.  Per esempi del modo in cui nelle tabelle dati viene tenuta traccia delle modifiche proposte, vedere <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A> e <xref:System.Data.DataTable.GetChanges%2A>.  
  
### Salvataggio dei dati dagli oggetti al database  
 I dati vengono salvati nel database passando i valori dall'oggetto personalizzato ai metodi DBDirect del TableAdapter.  
  
 Visual Studio consente la creazione di metodi DBDirect che è possibile eseguire direttamente sul database.  Questi metodi non richiedono oggetti DataSet o DataTable.  
  
|Metodo DBDirect di TableAdapter|Descrizione|  
|-------------------------------------|-----------------|  
|`TableAdapter.Insert`|Aggiunge nuovi record a un database e consente di passare valori di colonna singoli come parametri di metodo.|  
|`TableAdapter.Update`|Aggiorna i record esistenti in un database  Il metodo Update accetta valori di colonna originali e quelli nuovi come parametri di metodo.  I valori originali sono utilizzati per individuare il record originale, mentre i valori nuovi sono utilizzati per aggiornarlo.<br /><br /> Il metodo `TableAdapter.Update` è anche utilizzato per risolvere le differenze tra le modifiche apportate a un dataset e il database utilizzando un oggetto <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, oppure una matrice di oggetti <xref:System.Data.DataRow> come parametri di metodo.|  
|`TableAdapter.Delete`|Elimina i record esistenti dal database in base ai valori di colonna originali passati come parametri di metodo.|  
  
 Per salvare i dati di una raccolta di oggetti, scorrere la raccolta di oggetti \(ad esempio, utilizzando un ciclo For\-Next\) e inviare i valori per ciascun oggetto al database utilizzando i metodi DBDirect del TableAdapter.  
  
 Nell'esempio riportato di seguito viene illustrato come utilizzare il metodo DBDirect `TableAdapter.Insert` per aggiungere un nuovo cliente direttamente nel database:  
  
 [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## Vedere anche  
 [Procedura: connettersi ai dati negli oggetti](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [Procedura dettagliata: connessione ai dati negli oggetti \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [Procedura: salvare dati da un oggetto in un database](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Procedura: accedere direttamente al database mediante un oggetto TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Procedura dettagliata: salvataggio di dati con i metodi DBDirect di TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)