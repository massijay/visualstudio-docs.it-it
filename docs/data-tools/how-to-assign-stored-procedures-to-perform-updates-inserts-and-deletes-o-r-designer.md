---
title: "Procedura: assegnare stored procedure per l&#39;esecuzione dei comandi di aggiornamento, inserimento ed eliminazione (Progettazione relazionale oggetti) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: assegnare stored procedure per l&#39;esecuzione dei comandi di aggiornamento, inserimento ed eliminazione (Progettazione relazionale oggetti)
È possibile aggiungere a Progettazione relazionale oggetti stored procedure ed eseguirle come metodi <xref:System.Data.Linq.DataContext> tipici.Le stored procedure possono essere utilizzate anche per eseguire l'override del comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito che esegue i comandi di inserimento, aggiornamento ed eliminazione durante il salvataggio delle modifiche dalle classi di entità in un database \(ad esempio, durante la chiamata al metodo <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  Se le stored procedure restituiscono valori che devono essere inviati al client, ad esempio valori calcolati nelle stesse stored procedure, creare parametri di output all'interno di esse.Se non è possibile utilizzare parametri di output, è preferibile scrivere l'implementazione di un metodo parziale anziché basarsi sugli override generati da Progettazione relazionale oggetti.I membri con mapping ai valori generati dal database devono essere impostati su valori appropriati dopo il completamento delle operazioni INSERT o UPDATE.Per ulteriori informazioni, vedere [Responsabilità dello sviluppatore nell'eseguire l'override del comportamento predefinito](../Topic/Responsibilities%20of%20the%20Developer%20In%20Overriding%20Default%20Behavior.md).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] gestisce automaticamente i valori generati dal database per le colonne identity \(incremento automatico\) e rowguidcol \(GUID generato dal database\) e timestamp.I valori degli altri tipi di colonne sono costituiti da valori null non previsti.Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> su `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> su uno dei seguenti valori: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> o <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## Configurazione del comportamento di aggiornamento di un classe di entità  
 Per impostazione predefinita, la logica per aggiornare un database \(comandi di inserimento, aggiornamento ed eliminazione\) con le modifiche apportate ai dati nelle classi di entità [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] viene fornita dal runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].Nel runtime vengono creati comandi di inserimento, aggiornamento ed eliminazione predefiniti basati sullo schema della tabella \(informazioni sulla colonna e sulla chiave primaria\).Quando non si desidera utilizzare il comportamento predefinito, è possibile configurare il comportamento di aggiornamento assegnando stored procedure specifiche per eseguire i comandi di inserimento, aggiornamento ed eliminazione necessari per la modifica dei dati nella tabella. È inoltre possibile eseguire questa operazione quando non è generato il comportamento predefinito, quando viene eseguito il mapping delle classi di entità alle viste.Infine, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Per assegnare stored procedure per l'override del comportamento predefinito di una classe di entità  
  
1.  Aprire il file **LINQ to SQL** nella finestra di progettazione\(fare doppio clic sul file .dbml in **Esplora soluzioni**\).  
  
2.  In **Esplora server**\/**Esplora database** espandere **Stored procedure** e individuare le stored procedure che si desidera utilizzare per i comandi di inserimento, aggiornamento e\/o eliminazione della classe di entità.  
  
3.  Trascinare la stored procedure in Progettazione relazionale oggetti.  
  
     La stored procedure viene aggiunta al riquadro dei metodi come metodo <xref:System.Data.Linq.DataContext>.Per ulteriori informazioni, vedere [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Selezionare la classe di entità per cui si desidera utilizzare la stored procedure per eseguire gli aggiornamenti.  
  
5.  Nella finestra **Proprietà** selezionare il comando di cui eseguire l'override \(**Insert**, **Update** o **Delete**\).  
  
6.  Fare clic sui puntini di sospensione \(...\) accanto alle parole **Usa fase di esecuzione** per aprire la finestra di dialogo **Configura comportamento**.  
  
7.  Selezionare **Personalizza**.  
  
8.  Selezionare la stored procedure desiderata nell'elenco **Personalizza**.  
  
9. Controllare l'elenco di **Argomenti metodo** e **Proprietà classe** per verificare che venga eseguito il mapping degli **Argomenti metodo** alle **Proprietà classe** appropriate.Eseguire il mapping degli argomenti di metodo originali \(Original\_*ArgumentName*\) alle proprietà originali \(*PropertyName* \(Original\)\) per i comandi di aggiornamento ed eliminazione.  
  
    > [!NOTE]
    >  Per impostazione predefinita, viene eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono.Se non vi è più corrispondenza tra i nomi modificati nella tabella e nella classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente a cui eseguire il mapping nel caso in cui la finestra di progettazione non sia in grado di determinare il mapping corretto.  
  
10. Scegliere **OK** o **Applica**.  
  
    > [!NOTE]
    >  È possibile continuare a configurare il comportamento per ogni combinazione di classe\/comportamento purché si faccia clic su **Applica** dopo ogni modifica apportata.Se si modifica la classe o il comportamento prima di fare clic su **Applica**, verrà visualizzata una finestra di dialogo di avviso che offre la possibilità di applicare le eventuali modifiche apportate.  
  
     Per ripristinare l'utilizzo della logica di runtime predefinita per gli aggiornamenti, fare clic sui puntini di sospensione accanto al comando di inserimento, aggiornamento o eliminazione nella finestra **Proprietà**, quindi selezionare **Usa fase di esecuzione** nella finestra di dialogo **Configura comportamento**.  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Procedura dettagliata: creazione delle stored procedure di aggiornamento per la tabella Customers Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Operazioni Insert, Update e Delete](../Topic/Insert,%20Update,%20and%20Delete%20Operations.md)