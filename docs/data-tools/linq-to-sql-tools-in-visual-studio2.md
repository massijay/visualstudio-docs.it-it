---
title: "LINQ to SQL Tools in Visual Studio2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LINQ to SQL Tools in Visual Studio
LINQ to SQL è la prima tecnologia di mapping relazionale a oggetti rilasciata da Microsoft. Funziona bene in scenari di base e continua a essere supportato in Visual Studio, ma non è più in fase di sviluppo attivo. Utilizzo di LINQ to SQL per la manutenzione di un'applicazione legacy che sta già utilizzando, o in semplici applicazioni che utilizzano SQL Server e non necessitano del mapping di più tabelle. In generale, le nuove applicazioni devono utilizzare Entity Framework quando è necessario un livello di mapping relazionale a oggetti.  
  
 In Visual Studio creare classi LINQ to SQL che rappresentano le tabelle SQL utilizzando il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 Il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sono presenti due aree distinte nell'area di progettazione: il riquadro delle entità a sinistra e il riquadro dei metodi a destra. Il riquadro delle entità rappresenta l'area di progettazione principale in cui vengono visualizzate le classi di entità, le associazioni e le gerarchie di ereditarietà. Nel riquadro dei metodi è l'area di progettazione che consente di visualizzare il <xref:System.Data.Linq.DataContext> metodi con mapping a stored procedure e funzioni.  
  
 Il [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) fornisce un'area di progettazione visiva per la creazione di [LINQ to SQL](../Topic/LINQ%20to%20SQL.md) classi di entità e associazioni (relazioni) basate sugli oggetti in un database. In altre parole, [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] viene usato per creare un modello a oggetti in un'applicazione con mapping agli oggetti in un database Viene inoltre generato l'oggetto fortemente tipizzato <xref:System.Data.Linq.DataContext> utilizzato per inviare e ricevere dati tra le classi di entità e il database. Il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] inoltre fornisce funzionalità per il mapping di stored procedure e funzioni ai <xref:System.Data.Linq.DataContext> metodi per la restituzione di dati e il popolamento delle classi di entità. Infine, in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] viene fornita la possibilità di progettare relazioni di ereditarietà tra le classi di entità.  
  
## <a name="opening-the-or-designer"></a>Apertura di Progettazione relazionale oggetti  
 Per aggiungere un LINQ al modello di entità SQL al progetto, scegliere **progetto &#124; Aggiungi nuovo elemento** e quindi scegliere  **classi LINQ to SQL** dall'elenco di elementi di progetto:  
  
 ![Classi LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL Classes")  
  
 Visual Studio crea un file con estensione dbml e aggiungerlo alla soluzione. Questo è il file di mapping XML e i relativi file di codice correlate.  
  
 ![Classi LINQ to SQL in Esplora soluzioni](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes in Solution Explorer")  
  
 Quando si seleziona il file. dbml, Visual Studio Mostra l'area di Progettazione relazionale consente di creare visivamente il modello. Nella figura seguente viene illustrata la finestra di progettazione dopo che sono stati trascinati tabella Northwind Customers e Orders da Esplora Server. Si noti la relazione tra le tabelle.  
  
 ![Progettazione LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")  
  
> [!IMPORTANT]
>  Il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] è un mapper relazionale a oggetti semplice, poiché supporta solo relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Il mapping complesso, quale il mapping di una classe di entità a una tabella unita in join, non è supportato. utilizzo di Entity Framework per il mapping complesso. Inoltre, la finestra di progettazione rappresenta un generatore di codice unidirezionale: pertanto, nel file di codice vengono riflesse solo le modifiche apportate all'area di progettazione. Le modifiche manuali apportate al file di codice non vengono riflesse in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Tutte le modifiche apportate manualmente nel file di codice vengono sovrascritte durante il salvataggio della finestra di progettazione e il codice viene rigenerato. Per informazioni su come aggiungere il codice utente ed estendere le classi generate dal [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], vedere [procedura: estendere il codice generato da Progettazione relazionale](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Creazione e configurazione dell'oggetto DataContext  
 Dopo aver aggiunto un **classi LINQ to SQL** elemento a un progetto e aprire il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], l'area di progettazione vuota rappresenta un oggetto vuoto <xref:System.Data.Linq.DataContext> può essere configurato. il <xref:System.Data.Linq.DataContext> è configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Pertanto, il <xref:System.Data.Linq.DataContext> è configurata con le informazioni di connessione del primo elemento rilasciato nell'area di progettazione. Per ulteriori informazioni sui <xref:System.Data.Linq.DataContext> classe, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Creazione di classi di entità con mapping a tabelle e visualizzazioni di database  
 È possibile creare classi di entità mappate a tabelle e visualizzazioni trascinando le tabelle di database e le viste da **Esplora Server**/**Esplora Database** nella [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Come indicato nella sezione precedente di <xref:System.Data.Linq.DataContext> è configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Se viene aggiunto un elemento successivo che usa una connessione diversa per il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], è possibile modificare la connessione per il <xref:System.Data.Linq.DataContext>. Per ulteriori informazioni, vedere [procedura: creare classi LINQ to SQL mappate a tabelle e visualizzazioni (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Creazione di metodi DataContext che chiamano stored procedure e funzioni  
 È possibile creare <xref:System.Data.Linq.DataContext> metodi che chiamano (viene eseguito il mapping a) stored procedure e funzioni trascinandole da **Esplora Server**/**Esplora Database** nella [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Stored procedure e funzioni vengono aggiunti per il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] come metodi del <xref:System.Data.Linq.DataContext>.  
  
> [!NOTE]
>  Quando si trascinano stored procedure e funzioni da **Esplora Server**/**Esplora Database** nella [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], il tipo restituito dell'oggetto generato <xref:System.Data.Linq.DataContext> metodo varia a seconda della posizione in cui si rilascia l'elemento. Per ulteriori informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurazione di un oggetto DataContext in modo che utilizzi stored procedure per salvare i dati tra le classi di entità e un database  
 Come affermato in precedenza, è possibile creare <xref:System.Data.Linq.DataContext> metodi che chiamano stored procedure e funzioni. Inoltre, è anche possibile assegnare stored procedure utilizzabili per il comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito che esegue i comandi di inserimento, aggiornamento ed eliminazione. Per ulteriori informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Ereditarietà e Progettazione relazionale oggetti  
 Analogamente ad altri oggetti, le classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] possono usare l'ereditarietà ed essere derivate da altre classi. In un database le relazioni di ereditarietà vengono create in diversi modi. [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] supporta il concetto di ereditarietà a tabella singola come viene spesso implementato nei sistemi relazionali. Per ulteriori informazioni, vedere [procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>Query [LINQ to SQL]  
 Le classi di entità create dal [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sono progettati per l'utilizzo con [LINQ (Language-Integrated Query)](../Topic/LINQ%20\(Language-Integrated%20Query\).md). Per ulteriori informazioni, vedere [procedura: eseguire Query per informazioni](../Topic/How%20to:%20Query%20for%20Information.md).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separazione del codice delle classi di entità e DataContext generate in diversi spazi dei nomi  
 Il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fornisce il **Context Namespace** e **Entity Namespace** le proprietà di <xref:System.Data.Linq.DataContext>. Queste proprietà determinano quale spazio dei nomi di <xref:System.Data.Linq.DataContext> e viene generato il codice di classe di entità in. Per impostazione predefinita, tali proprietà sono vuote e <xref:System.Data.Linq.DataContext> e le classi di entità vengono generate nello spazio dei nomi dell'applicazione. Per generare il codice in uno spazio dei nomi diversi da spazio dei nomi dell'applicazione, immettere un valore nel **Context Namespace** e/o **Entity Namespace** proprietà.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)  
 Spiega come <xref:System.Data.Linq.DataContext> metodi e come crearli.  
  
 [Ereditarietà delle classi di dati (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md)  
 Vengono illustrati il concetto di ereditarietà a tabella singola e le relative modalità di implementazione in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Procedura: creare LINQ to SQL classi mappate a tabelle e visualizzazioni (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)  
 Viene descritto come creare classi di entità con mapping a tabelle e visualizzazioni in un database.  
  
 [Procedura: creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)  
 Viene descritto come creare una relazione tra classi di entità [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
 [Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)  
 Viene descritto come creare <xref:System.Data.Linq.DataContext> metodi che eseguono stored procedure o funzioni quando vengono chiamati.  
  
 [Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
 Viene descritto come configurare un <xref:System.Data.Linq.DataContext> per utilizzare le stored procedure durante il salvataggio di dati da entità classi nuovamente in un database.  
  
 [Procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)  
 Viene descritto come impostare il tipo restituito di un <xref:System.Data.Linq.DataContext> metodo deve essere il tipo di una classe di entità o un tipo generato automaticamente creato da O/R Designer.  
  
 [Procedura: aggiungere la convalida alle classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md)  
 Viene descritto come generare metodi parziali che consentano l'aggiunta di codice durante le modifiche delle proprietà e gli aggiornamenti delle classi di entità.  
  
 [Procedura: attivare e disattivare (O/R Designer) la pluralizzazione](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)  
 Viene descritto come attivare e disattivare la ridenominazione automatica delle classi aggiunte a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)  
 Viene descritto come configurare le classi di entità usando l'ereditarietà a tabella singola con [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Procedura: estendere il codice generato da O/R Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)  
 Viene descritto come e dove aggiungere codice che non verrà sovrascritto quando le modifiche agli oggetti in Progettazione relazionale oggetti determinano una rigenerazione del codice.  
  
 [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)  
 Vengono fornite istruzioni dettagliate per la configurazione delle classi di entità usando l'ereditarietà a tabella singola con [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Procedura dettagliata: Personalizzazione dell'inserimento, aggiornamento ed eliminazione di comportamento delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
 Vengono fornite istruzioni dettagliate per la configurazione di un <xref:System.Data.Linq.DataContext> per utilizzare le stored procedure durante il salvataggio di dati da entità classi nuovamente in un database.  
  
## <a name="reference-content"></a>Contenuto di riferimento  
 <xref:System.Linq>  
  
 <xref:System.Data.Linq>  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti di dati di Visual Studio per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Domande frequenti](../Topic/Frequently%20Asked%20Questions.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [L'accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)