---
title: "Procedura dettagliata: creazione di classi LINQ to SQL utilizzando l&#39;ereditariet&#224; a tabella singola (Progettazione relazionale oggetti) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 4
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: creazione di classi LINQ to SQL utilizzando l&#39;ereditariet&#224; a tabella singola (Progettazione relazionale oggetti)
[Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md) supporta l'ereditarietà a tabella singola come viene in genere implementata nei sistemi relazionali.In questa procedura dettagliata vengono sviluppati i passaggi generici specificati nell'argomento [Procedura: configurare l'ereditarietà utilizzando Progettazione relazionale oggetti](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) e vengono forniti alcuni dati reali per illustrare l'utilizzo dell'ereditarietà in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 In particolare, verranno illustrate le seguenti attività:  
  
-   Creazione di una tabella di database e aggiunta di dati ad essa.  
  
-   Creazione di un'applicazione Windows Form.  
  
-   Aggiunta di un file [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a un progetto.  
  
-   Creazione di nuove classi di entità.  
  
-   Configurazione delle classi di entità per l'utilizzo dell'ereditarietà.  
  
-   Esecuzione di una query sulla classe ereditata.  
  
-   Visualizzazione dei dati in un Windows Form.  
  
## Creazione di una tabella da cui ereditare  
 Per verificare il funzionamento dell'ereditarietà, verrà creata una piccola tabella Person, utilizzata come classe di base, e verrà creato quindi un oggetto Employee che eredita dalla tabella.  
  
#### Per creare una tabella di base per l'illustrazione dell'ereditarietà  
  
1.  In **Esplora server**\/**Esplora database** fare clic con il pulsante destro del mouse sul nodo **Tabelle**, quindi scegliere **Aggiungi nuova tabella**.  
  
    > [!NOTE]
    >  È possibile utilizzare il database Northwind o qualsiasi altro database a cui sia possibile aggiungere una tabella.  
  
2.  In Progettazione tabelle aggiungere le seguenti colonne alla tabella:  
  
    |Nome colonna|Tipo di dati|Consente valori null|  
    |------------------|------------------|--------------------------|  
    |ID|int|False|  
    |Tipo|int|True|  
    |FirstName|nvarchar\(200\)|False|  
    |LastName|nvarchar\(200\)|False|  
    |Manager|int|True|  
  
3.  Impostare la colonna ID come chiave primaria.  
  
4.  Salvare la tabella e denominarla Person.  
  
## Aggiunta di dati alla tabella  
 Allo scopo di verificare che l'ereditarietà sia configurata correttamente, è necessario aggiungere alcuni dati alla tabella per ogni classe nell'ereditarietà a tabella singola.  
  
#### Per aggiungere dati alla tabella  
  
1.  Aprire la tabella nella visualizzazione dati\(fare clic con il pulsante destro del mouse sulla tabella **Person** in **Esplora server**\/**Esplora database**, quindi scegliere **Mostra dati tabella**\).  
  
2.  Copiare i dati riportati di seguito nella tabella\(è possibile copiarli e incollarli nella tabella selezionando l'intera riga nel [Results Pane](http://msdn.microsoft.com/it-it/3c712f20-7c9f-4021-b1ac-fdc6f534c95a)\).  
  
    ||||||  
    |-|-|-|-|-|  
    |ID|Tipo|FirstName|LastName|Manager|  
    |1|1|Anne|Wallace|NULL|  
    |2|1|Carlos|Grilo|NULL|  
    |3|1|Yael|Peled|NULL|  
    |4|2|Gatis|Ozolins|1|  
    |5|2|Andreas|Hauser|1|  
    |6|2|Tiffany|Phuvasate|1|  
    |7|2|Alexey|Orekhov|2|  
    |8|2|Michał|Poliszkiewicz|2|  
    |9|2|Tai|Yee|2|  
    |10|2|Fabricio|Noriega|3|  
    |11|2|Mindy|Martin|3|  
    |12|2|Ken|Kwok|3|  
  
## Creazione di un nuovo progetto  
 Una volta creata la tabella, creare un nuovo progetto per illustrare la configurazione dell'ereditarietà.  
  
#### Per creare la nuova applicazione Windows  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Assegnare al progetto il nome InheritanceWalkthrough.  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] è supportato nei progetti Visual Basic e C\#.Creare il nuovo progetto in uno di questi linguaggi.  
  
3.  Fare clic sul modello **Applicazione Windows Form**, quindi scegliere **OK**.Per ulteriori informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
4.  Il progetto InheritanceWalkthrough viene creato e aggiunto a **Esplora soluzioni**.  
  
## Aggiunta di un file di classi LINQ to SQL al progetto  
  
#### Per aggiungere un file LINQ to SQL al progetto  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
2.  Fare clic sul modello **Classi LINQ to SQL**, quindi scegliere **Aggiungi**.  
  
     Il file .dbml viene aggiunto al progetto e viene aperto [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Creazione dell'ereditarietà utilizzando Progettazione relazionale oggetti  
 Configurare l'ereditarietà trascinando un oggetto **Inheritance** dalla **Casella degli strumenti** nell'area di progettazione.  
  
#### Per creare l'ereditarietà  
  
1.  In **Esplora server**\/**Esplora database** passare alla tabella **Person** creata precedentemente.  
  
2.  Trascinare la tabella **Person** nell'area di progettazione di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Trascinare una seconda tabella **Person** in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e modificarne il nome in Employee.  
  
4.  Eliminare la proprietà **Manager** dall'oggetto **Person**.  
  
5.  Eliminare le proprietà **Type**, **ID**, **FirstName** e **LastName** dall'oggetto **Employee**\(in altre parole, eliminare tutte le proprietà ad eccezione di **Manager**\).  
  
6.  Dalla scheda **Progettazione relazionale oggetti** della **Casella degli strumenti**, creare un oggetto **Inheritance** tra gli oggetti **Person** ed **Employee**.Per eseguire questa operazione, fare clic sull'elemento **Inheritance** nella **Casella degli strumenti** e rilasciare il pulsante del mouse.Quindi fare clic sull'oggetto **Employee** e sull'oggetto **Person** in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].La freccia della linea di ereditarietà punterà all'oggetto **Person**.  
  
7.  Fare clic sulla linea **Ereditarietà** nell'area di progettazione.  
  
8.  Impostare la proprietà **Discriminator Property** su **Type**.  
  
9. Impostare la proprietà **Derived Class Discriminator Value** su **2**.  
  
10. Impostare la proprietà **Base Class Discriminator Value** su **1**.  
  
11. Impostare la proprietà **Inheritance Default** su **Person**.  
  
12. Compilare il progetto.  
  
## Esecuzione di una query sulla classe ereditata e visualizzazione dei dati nel form  
 A questo punto si aggiungerà codice al form che esegue una query per una classe specifica nel modello a oggetti.  
  
#### Per creare una query LINQ e visualizzare i risultati nel form  
  
1.  Trascinare un oggetto **ListBox** in Form1.  
  
2.  Fare doppio clic sul form per creare un gestore dell'evento `Form1_Load`.  
  
3.  Aggiungere il codice seguente al gestore eventi `Form1_Load`:  
  
    ```vb#  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```c#  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## Test dell'applicazione  
 Eseguire l'applicazione e verificare che i record visualizzati nella casella di riepilogo rappresentino tutti i dipendenti \(record che presentano il valore 2 nella rispettiva colonna Type\).  
  
#### Per eseguire il test dell'applicazione  
  
1.  Premere F5.  
  
2.  Verificare che siano visualizzati solo i record che presentano il valore 2 nella rispettiva colonna Type.  
  
3.  Chiudere il form.Scegliere **Termina debug** dal menu **Debug**.  
  
## Vedere anche  
 [Cenni preliminari su Progettazione relazionale oggetti](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procedura: aggiungere classi LINQ to SQL a un progetto \(Progettazione relazionale oggetti\)](../Topic/How%20to:%20Add%20LINQ%20to%20SQL%20Classes%20to%20a%20Project%20\(O-R%20Designer\).md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Procedura: assegnare stored procedure per l'esecuzione dei comandi di aggiornamento, inserimento ed eliminazione \(Progettazione relazionale oggetti\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Procedura: generare il modello a oggetti in Visual Basic o C\#](../Topic/How%20to:%20Generate%20the%20Object%20Model%20in%20Visual%20Basic%20or%20C%23.md)