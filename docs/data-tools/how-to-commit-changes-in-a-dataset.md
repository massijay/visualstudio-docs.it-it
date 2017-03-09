---
title: "Procedura: eseguire il commit delle modifiche in un dataset | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataSet.AcceptChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dataset [Visual Basic], commit di modifiche"
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: eseguire il commit delle modifiche in un dataset
Quando si apportano modifiche ai record di un dataset aggiornando, inserendo ed eliminando record, nel dataset vengono conservate la versione originale e la versione corrente dei record.  Inoltre, ciascuna proprietà <xref:System.Data.DataRow.RowState%2A> della riga viene impostata per indicare se i record si trovano nello stato originale o se sono stati aggiornati, inseriti o eliminati.  Queste informazioni risultano utili quando si desidera trovare una versione specifica di una riga.  In genere viene recuperato un sottoinsieme di tutti i record modificati, che viene quindi inviato a un altro processo.  Per ulteriori informazioni, vedere [Procedura: recuperare le righe modificate](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  Una volta elaborate tutte le righe modificate, è possibile eseguire il commit delle modifiche chiamando il metodo `AcceptChanges` di <xref:System.Data.DataSet>, <xref:System.Data.DataTable> o <xref:System.Data.DataRow>.  Il metodo `AcceptChanges` viene chiamato automaticamente quando si chiamano i metodi Update di un [TableAdapter](../data-tools/tableadapter-overview.md) o un adattatore dati.  Chiamare `AcceptChanges` dopo aver inviato le modifiche a un database.  
  
 Quando si chiama il metodo <xref:System.Data.DataSet.AcceptChanges%2A> su <xref:System.Data.DataSet>, vengono completate correttamente tutte le operazioni di modifica sugli oggetti <xref:System.Data.DataRow> ancora in modalità di modifica.  Cambia anche la proprietà <xref:System.Data.DataRow.RowState%2A> di ciascun oggetto <xref:System.Data.DataRow>; le righe <xref:System.Data.DataRowState> e <xref:System.Data.DataRowState> diventano <xref:System.Data.DataRowState>, mentre le righe <xref:System.Data.DataRowState> vengono rimosse.  
  
 Se l'oggetto <xref:System.Data.DataSet> contiene oggetti <xref:System.Data.ForeignKeyConstraint>, il richiamo del metodo <xref:System.Data.DataSet.AcceptChanges%2A> comporterà anche l'attivazione della proprietà <xref:System.Data.AcceptRejectRule>.  
  
### Per applicare le modifiche in un dataset  
  
-   Chiamare il metodo `AcceptChanges` su un <xref:System.Data.DataSet>, un <xref:System.Data.DataTable> o un <xref:System.Data.DataRow> per eseguire il commit delle modifiche in tali oggetti.  
  
     Nell'esempio che segue viene illustrata la procedura per chiamare il metodo `AcceptChanges` in modo da eseguire il commit delle modifiche nella tabella `Customers` dopo aver aggiornato un'origine dati:  
  
     [!CODE [VbRaddataEditing#11](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#11)]  
  
## Vedere anche  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Salvataggio di dati](../data-tools/saving-data.md)   
 [Procedura: recuperare le righe modificate](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)