---
title: "Procedura: aggiungere la convalida a un dataset a pi&#249; livelli | Microsoft Docs"
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
  - "applicazioni a più livelli, convalida"
  - "convalida delle applicazioni dati a più livelli"
  - "convalida [Visual Basic], applicazioni dati a più livelli"
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 23
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: aggiungere la convalida a un dataset a pi&#249; livelli
L'aggiunta della convalida in un dataset separato in una soluzione a più livelli è fondamentalmente uguale all'aggiunta della convalida in un dataset costituito da un singolo file, ovvero un dataset in un solo progetto.  È consigliabile eseguire la convalida dei dati durante gli eventi <xref:System.Data.DataTable.ColumnChanging> e\/o <xref:System.Data.DataTable.RowChanging> di una tabella dati.  
  
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md) fornisce la funzionalità per creare le classi parziali alle quali è possibile aggiungere il codice utente per gli eventi di modifica colonne e righe delle tabelle dati del dataset.  Per ulteriori informazioni sull'aggiunta di codice in un dataset in una soluzione a più livelli, vedere [Procedura: aggiungere il codice nei dataset di applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md) e [Procedura: aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md).  Per ulteriori informazioni sulle classi parziali, vedere [How to: Split a Class into Partial Classes \(Class Designer\)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) o [Classi e metodi parziali](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
> [!NOTE]
>  Quando si separano i dataset dai TableAdapter impostando la proprietà **Progetto DataSet**, le classi del dataset parziale presenti nel progetto non verranno spostate automaticamente.  Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
> [!NOTE]
>  Progettazione DataSet non crea automaticamente i gestori eventi in C\# per gli eventi <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging>.  È necessario creare manualmente un gestore eventi e associarlo all'evento sottostante.  Le procedure descritte di seguito forniscono i passaggi per creare i gestori eventi necessari in Visual Basic e C\#.  
  
## Convalida delle modifiche a singole colonne  
 Convalidare i valori nelle singole colonne gestendo l'evento <xref:System.Data.DataTable.ColumnChanging>.  L'evento <xref:System.Data.DataTable.ColumnChanging> viene generato quando si modifica il valore in una colonna.  Creare un gestore eventi per l'evento <xref:System.Data.DataTable.ColumnChanging> facendo doppio clic sulla colonna desiderata in [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  
  
 La prima volta che si fa doppio clic su una colonna, la finestra di progettazione genera un gestore eventi per l'evento <xref:System.Data.DataTable.ColumnChanging>.  Oltre all'evento <xref:System.Data.DataTable.ColumnChanging>, viene creata anche un'istruzione `If…Then` per verificare la colonna specifica.  Ad esempio, il codice seguente viene generato quando si fa doppio clic sulla colonna RequiredDate della tabella Orders di Northwind:  
  
```vb#  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  Nei progetti in C\#, Progettazione DataSet consente di creare solo classi parziali per il dataset e singole tabelle all'interno del dataset.  Progettazione DataSet non crea automaticamente i gestori eventi per gli eventi <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> in C\# come per i progetti in Visual Basic.  Nei progetti in C\#, è necessario costruire manualmente un metodo per gestire l'evento e associare il metodo all'evento sottostante.  La procedura descritta di seguito fornisce i passaggi per creare i gestori eventi necessari in Visual Basic e C\#.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Per aggiungere la convalida durante le modifiche ai valori di una singola colonna  
  
1.  Aprire il dataset in [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md) facendo doppio clic sul file con estensione **xsd** in Esplora soluzioni.  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Fare doppio clic sulla colonna da convalidare.  Attraverso questa azione viene creato il gestore eventi <xref:System.Data.DataTable.ColumnChanging>.  
  
    > [!NOTE]
    >  Progettazione DataSet non crea automaticamente un gestore eventi per l'evento C\#.  Il codice necessario per la gestione dell'evento in C\# è incluso di seguito.  `SampleColumnChangingEvent` viene creato, quindi collegato all'evento <xref:System.Data.DataTable.ColumnChanging> nel metodo <xref:System.Data.DataTable.EndInit%2A>.  
  
3.  Aggiungere codice per verificare che `e.ProposedValue` contenga dati che soddisfano i requisiti dell'applicazione.  Se il valore proposto non è accettabile, impostare la colonna in modo da indicare che contiene un errore.  
  
     L'esempio di codice seguente verifica che la colonna della Quantity contiene più di 0.  Se il valore di Quantity è minore o uguale a 0, la colonna viene impostata su un errore.  La clausola `Else` elimina l'errore se la quantità è maggiore di 0.  Il codice nel gestore eventi di modifica delle colonne deve essere analogo al seguente:  
  
    ```vb#  
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then  
        If CType(e.ProposedValue, Short) <= 0 Then  
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")  
        Else  
            e.Row.SetColumnError(e.Column, "")  
        End If  
    End If  
    ```  
  
    ```c#  
    // C#  
    // Add this code to the DataTable   
    // partial class.  
  
        public override void EndInit()  
        {  
            base.EndInit();  
            // Hook up the ColumnChanging event  
            // to call the SampleColumnChangingEvent method.  
            ColumnChanging += SampleColumnChangingEvent;  
        }  
  
        public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)  
        {  
            if (e.Column.ColumnName == QuantityColumn.ColumnName)  
            {  
                if ((short)e.ProposedValue <= 0)  
                {  
                    e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
                }  
                else  
                {  
                    e.Row.SetColumnError("Quantity", "");  
                }  
            }  
        }  
    ```  
  
## Convalida delle modifiche a intere righe  
 Convalidare i valori in intere righe gestendo l'evento <xref:System.Data.DataTable.RowChanging>.  L'evento <xref:System.Data.DataTable.RowChanging> viene generato quando vengono applicati i valori in tutte le colonne.  È necessario eseguire la convalida nell'evento <xref:System.Data.DataTable.RowChanging> quando il valore di una colonna si basa sul valore di un'altra colonna.  Si considerino ad esempio OrderDate e RequiredDate nella tabella Orders di Northwind.  Quando vengono immessi gli ordini, la convalida verifica che un ordine non venga immesso con un valore RequiredDate uguale o precedente al valore OrderDate.  In questo esempio, devono essere confrontati i valori di entrambe le colonne RequiredDate e OrderDate, per cui non ha senso eseguire la convalida della modifica apportata in una singola colonna.  
  
 Creare un gestore eventi per l'evento <xref:System.Data.DataTable.RowChanging> facendo doppio clic sul nome della tabella nella barra del titolo della tabella in [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  
  
#### Per aggiungere la convalida durante le modifiche a intere righe  
  
1.  Aprire il dataset in [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md) facendo doppio clic sul file con estensione **xsd** in Esplora soluzioni.  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Fare doppio clic sulla barra del titolo della tabella dati nella finestra di progettazione.  
  
     Viene creata una classe parziale con un gestore eventi `RowChanging` e visualizzata nell'editor del codice.  
  
    > [!NOTE]
    >  Progettazione DataSet non crea automaticamente un gestore eventi per l'evento <xref:System.Data.DataTable.RowChanging> nei progetti C\#.  È necessario creare un metodo per gestire l'evento <xref:System.Data.DataTable.RowChanging> ed eseguire il codice per associare tale evento nel metodo di inizializzazione della tabella.  
  
3.  Aggiungere il codice utente nella dichiarazione di classe parziale.  
  
4.  Nel codice seguente viene illustrato dove aggiungere il codice utente per eseguire la convalida durante l'evento <xref:System.Data.DataTable.RowChanging> per Visual Basic:  
  
    ```vb#  
    Partial Class OrdersDataTable  
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging  
            ' Add logic to validate columns here.  
            If e.Row.RequiredDate <= e.Row.OrderDate Then  
                ' Set the RowError if validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"  
            Else  
                ' Clear the RowError when validation passes.  
                e.Row.RowError = ""  
            End If  
        End Sub  
    End Class  
    ```  
  
5.  Nel codice seguente viene illustrato come creare il gestore eventi `RowChanging` e dove aggiungere il codice utente per eseguire la convalida durante l'evento <xref:System.Data.DataTable.RowChanging> per C\#:  
  
    ```c#  
    partial class OrdersDataTable  
    {  
        public override void EndInit()  
        {  
            base.EndInit();  
            // Hook up the event to the  
            // RowChangingEvent method.  
            OrdersRowChanging += RowChangingEvent;  
        }  
  
        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)  
        {  
            // Perfom the validation logic.  
            if (e.Row.RequiredDate <= e.Row.OrderDate)  
            {  
                // Set the row to an error when validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";  
            }  
            else  
            {  
                // Clear the RowError if validation passes.  
                e.Row.RowError = "";  
            }  
        }  
    }  
    ```  
  
## Vedere anche  
 [Cenni preliminari sull'applicazione dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
 [Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Convalida dei dati nei dataset](../data-tools/validate-data-in-datasets.md)