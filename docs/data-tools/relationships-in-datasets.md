---
title: "Relazioni nei dataset | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DesignRelation"
  - "vbdata.Microsoft.VSDesigner.DataSource.DesignRelation"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dataset [Visual Basic], relazioni"
  - "relazioni, informazioni"
  - "relazioni, dataset"
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Relazioni nei dataset
Un dataset può contenere tabelle correlate analogamente a un database relazionale.  L'oggetto che consente una relazione tra tabelle di dati è un oggetto **DataRelation**.  Negli argomenti riportati di seguito verranno fornite informazioni sugli oggetti **DataRelation** ADO.NET, sulla creazione di tali oggetti e sul relativo utilizzo per la gestione dei dati contenuti in tabelle correlate.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## In questa sezione  
 [Introduzione agli oggetti DataRelation](../Topic/Introduction%20to%20DataRelation%20Objects.md)  
 Viene fornita una descrizione generale del modo in cui i dataset consentono di definire relazioni tra le tabelle e di come possono essere utilizzate nel migliore dei modi.  
  
 [Procedura: creare DataRelation mediante Progettazione DataSet](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)  
 Viene illustrato come utilizzare **Progettazione DataSet** per aggiungere un oggetto <xref:System.Data.DataRelation> a un dataset.  
  
 [Procedura: accedere ai record di DataTable correlate](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)  
 Viene descritto come restituire in una relazione uno\-a\-molti i record correlati a livello di codice in un dataset tipizzato con tabelle.  
  
 [Procedura dettagliata: creazione di una relazione tra tabelle dati](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)  
 Vengono fornite istruzioni dettagliate per la creazione di due tabelle dati con **Progettazione DataSet** e per l'aggiunta di una relazione fra le due.  
  
## Riferimenti  
 <xref:System.Data.DataRelation>  
 Rappresenta una relazione padre\-figlio fra due oggetti T:System.Data.DataTable.  
  
 <xref:System.Data.DataRow.GetChildRows%2A>  
 Ottiene le righe figlio di una T:System.Data.DataRow.  
  
 <xref:System.Data.DataRow.GetParentRow%2A>  
 Ottiene le righe padre di una T:System.Data.DataRow.  
  
 <xref:System.Data.Rule>  
 Indica l'azione che si verifica quando viene applicato un <xref:System.Data.ForeignKeyConstraint>.  
  
 <xref:System.Data.DataColumn.Unique%2A>  
 Ottiene o imposta un valore che indica se i valori di ogni riga della colonna devono essere univoci.  
  
 <xref:System.Data.Constraint>  
 Rappresenta un vincolo che può essere applicato a uno o più oggetti <xref:System.Data.DataColumn>.  
  
## Sezioni correlate  
 [Aggiunta di DataRelation](../Topic/Adding%20DataRelations.md)  
 Viene illustrato come creare relazioni fra tabelle in un <xref:System.Data.DataSet>.  
  
 [Navigazione in DataRelations](../Topic/Navigating%20DataRelations.md)  
 Viene descritto l'utilizzo delle relazioni tra tabelle in un <xref:System.Data.DataSet> per restituire le righe padre o figlio di una relazione padre\-figlio.  
  
 [DataRelation annidati](../Topic/Nesting%20DataRelations.md)  
 Viene illustrata l'importanza degli oggetti <xref:System.Data.DataRelation> annidati durante la rappresentazione del contenuto di un <xref:System.Data.DataSet> sotto forma di dati XML e ne viene descritta la creazione.