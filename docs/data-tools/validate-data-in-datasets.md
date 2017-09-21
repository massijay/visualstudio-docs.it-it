---
title: "Convalida dei dati nei dataset | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataTable.ColumnChanging"
  - "System.Data.DataTable.ColumnChanging"
  - "System.Data.DataTable.RowChanging"
  - "DataTable.RowChanging"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "convalida dei dati"
  - "convalida dei dati, dataset"
  - "aggiornamento di dataset, convalida dei dati"
  - "convalida dei dati, dataset"
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 24
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Convalida dei dati nei dataset
La convalida dei dati è il processo mediante il quale si conferma che i valori immessi negli oggetti dati sono conformi ai vincoli specificati all'interno di uno schema del dataset, nonché alle regole stabilite per l'applicazione.  La convalida dei dati che precede l'invio degli aggiornamenti al database sottostante è un'operazione consigliata in quanto consente di ridurre gli errori nonché il numero potenziale di round trip tra un'applicazione e il database.  È possibile confermare la validità dei dati scritti in un dataset compilando controlli di convalida nel dataset stesso.  Per il dataset è possibile controllare i dati indipendentemente dal modo in cui viene svolto l'aggiornamento: direttamente dai controlli di un form, all'interno di un componente o in un altro modo.  Poiché il dataset fa parte dell'applicazione, è il posto più adatto per compilare una convalida specifica dell'applicazione, anziché compilare gli stessi controlli all'interno del database back\-end.  
  
 La posizione suggerita per l'aggiunta della convalida nell'applicazione è il file di classe parziale del dataset.  In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aprire **Progettazione DataSet** e fare doppio clic sulla colonna o sulla tabella per la quale si desidera creare una convalida.  Questa azione comporta la creazione automatica di un gestore eventi <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging>.  Per ulteriori informazioni, vedere [Procedura: convalidare i dati durante la modifica delle colonne](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md) o [Procedura: convalidare i dati durante la modifica delle righe](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  Per un esempio completo, vedere [Procedura dettagliata: aggiunta di convalida a un dataset](../Topic/Walkthrough:%20Adding%20Validation%20to%20a%20Dataset.md).  
  
## Convalida dei dati  
 La convalida all'interno di un dataset può essere svolta nei seguenti modi:  
  
-   Mediante la creazione di una convalida specifica dell'applicazione in grado di verificare i dati durante la modifica dei valori di una singola colonna dati.  Per ulteriori informazioni, vedere [Procedura: convalidare i dati durante la modifica delle colonne](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md).  
  
-   Mediante la creazione di una convalida specifica dell'applicazione in grado di verificare i dati durante la modifica dei valori, mentre è in corso la modifica di un'intera riga di dati.  Per ulteriori informazioni, vedere [Procedura: convalidare i dati durante la modifica delle righe](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
-   Creare chiavi, vincoli UNIQUE e così via, come parte dell'effettiva definizione di schema del dataset.  Per ulteriori informazioni su come incorporare la convalida nella definizione dello schema, vedere [Limitare un oggetto DataColumn a valori univoci](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md#SpecifyUniqueConstraint).  
  
-   Mediante l'impostazione delle proprietà dell'oggetto <xref:System.Data.DataColumn>, quali <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A> e <xref:System.Data.DataColumn.Unique%2A>.  
  
 Quando viene apportata una modifica a un record, l'oggetto <xref:System.Data.DataTable> può generare diversi eventi:  
  
-   Gli eventi <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> vengono generati durante e dopo ogni modifica apportata a una singola colonna.  L'evento <xref:System.Data.DataTable.ColumnChanging> è utile quando si desidera convalidare le modifiche in determinate colonne.  Le informazioni relative alla modifica proposta vengono passate come argomento con l'evento.  Per ulteriori informazioni, vedere [Procedura: convalidare i dati durante la modifica delle colonne](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md).  
  
-   Gli eventi <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> vengono generati durante e dopo qualsiasi modifica apportata a una riga.  L'evento <xref:System.Data.DataTable.RowChanging> è più generale, in quanto indica semplicemente che si sta effettuando una modifica nella riga, ma non si conosce la colonna in cui avviene tale modifica.  Per ulteriori informazioni, vedere [Procedura: convalidare i dati durante la modifica delle righe](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
 Per impostazione predefinita, ogni modifica apportata a una colonna genera pertanto quattro eventi: in primo luogo gli eventi <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> per la specifica colonna modificata, quindi gli eventi <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged>.  Se vengono apportate più modifiche alla riga, per ciascuna modifica verranno generati degli eventi.  
  
> [!NOTE]
>  Il metodo <xref:System.Data.DataRow.BeginEdit%2A> della riga di dati disattiva gli eventi <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> in seguito a ogni singola modifica di colonna.  In tale caso, l'evento non viene generato finché non viene chiamato il metodo <xref:System.Data.DataRow.EndEdit%2A>, quando gli eventi <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> vengono generati una sola volta.  Per ulteriori informazioni, vedere [Procedura: disattivare i vincoli durante il riempimento di un dataset](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 L'evento scelto dipende dal livello di dettaglio che si desidera conferire alla convalida.  Se è importante intercettare un errore immediatamente dopo la modifica di una colonna, compilare la convalida utilizzando l'evento <xref:System.Data.DataTable.ColumnChanging>.  In caso contrario, utilizzare l'evento <xref:System.Data.DataTable.RowChanging>, che potrebbe determinare l'intercettazione di diversi errori contemporaneamente.  Inoltre, se i dati sono strutturati in modo che il valore di una colonna viene convalidato in base al contenuto di un'altra, sarà necessario effettuare la convalida durante l'evento <xref:System.Data.DataTable.RowChanging>.  
  
 Quando i record vengono aggiornati, l'oggetto <xref:System.Data.DataTable> genera gli eventi ai quali è possibile rispondere durante e dopo l'inserimento di modifiche.  
  
 Se nell'applicazione è in uso un dataset tipizzato, sarà possibile creare gestori eventi fortemente tipizzati.  Ciò comporta l'aggiunta di altri quattro eventi tipizzati per i quali è possibile creare gestori, ovvero `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting` e `dataTableNameRowDeleted`.  Questi gestori eventi tipizzati passano un argomento nel quale sono compresi i nomi delle colonne della tabella che facilitano la lettura e la scrittura del codice.  
  
## Eventi di aggiornamento dei dati  
  
|Evento|Descrizione|  
|------------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|È in corso la modifica del valore di una colonna.  L'evento passa la riga e la colonna insieme al nuovo valore proposto.|  
|<xref:System.Data.DataTable.ColumnChanged>|Il valore di una colonna è stato modificato.  L'evento passa la riga e la colonna insieme al valore proposto.|  
|<xref:System.Data.DataTable.RowChanging>|Sta per essere eseguito il commit nel dataset delle modifiche apportate a un oggetto <xref:System.Data.DataRow>.  Se il metodo <xref:System.Data.DataRow.BeginEdit%2A> non è stato chiamato, viene generato l'evento <xref:System.Data.DataTable.RowChanging> per ogni modifica apportata a una colonna, immediatamente dopo la generazione dell'evento <xref:System.Data.DataTable.ColumnChanging>.  Se <xref:System.Data.DataRow.BeginEdit%2A> è stato chiamato prima dell'inserimento di modifiche, l'evento <xref:System.Data.DataTable.RowChanging> viene generato solo quando si chiama il metodo <xref:System.Data.DataRow.EndEdit%2A>.<br /><br /> L'evento passa la riga insieme a un valore che indica il tipo di operazione che sta per essere eseguita, ad esempio modifica, inserimento e così via.|  
|<xref:System.Data.DataTable.RowChanged>|Una riga è stata modificata.  L'evento passa la riga insieme a un valore che indica il tipo di operazione che sta per essere eseguita, ad esempio modifica, inserimento e così via.|  
|<xref:System.Data.DataTable.RowDeleting>|È in corso l'eliminazione di una riga.  L'evento passa la riga insieme a un valore che indica il tipo di operazione che sta per essere eseguita, in questo caso l'eliminazione.|  
|<xref:System.Data.DataTable.RowDeleted>|Una riga è stata eliminata.  L'evento passa la riga insieme a un valore che indica il tipo di operazione che sta per essere eseguita, in questo caso l'eliminazione.|  
  
 Gli eventi <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowDeleting> vengono generati durante il processo di aggiornamento.  È possibile utilizzare questi eventi per convalidare i dati o per svolgere altri tipi di elaborazione.  Poiché gli aggiornamenti vengono elaborati durante questi eventi, è possibile annullare l'aggiornamento lanciando un'eccezione, in modo da impedire il completamento della modifica.  
  
 Gli eventi <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> e <xref:System.Data.DataTable.RowDeleted> sono eventi di notifica generati al termine dell'aggiornamento.  sono utili quando si desidera svolgere ulteriori azioni basate su un aggiornamento completato con esito positivo.  
  
## Vedere anche  
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Procedura: convalidare dati nel controllo DataGridView di Windows Form](../Topic/How%20to:%20Validate%20Data%20in%20the%20Windows%20Forms%20DataGridView%20Control.md)   
 [Procedura: visualizzare le icone di errori per la convalida dei form con il componente ErrorProvider di Windows Form](../Topic/How%20to:%20Display%20Error%20Icons%20for%20Form%20Validation%20with%20the%20Windows%20Forms%20ErrorProvider%20Component.md)