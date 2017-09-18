---
title: "Procedura: filtrare e ordinare i dati in un&#39;applicazione Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "visualizzazioni dati, applicazione di filtri"
  - "visualizzazioni dati, ordinamento"
  - "dataset (applicazione di filtri), utilizzo di visualizzazioni dati"
  - "stati righe"
  - "stati righe, applicazione di filtri"
  - "versione righe, applicazione di filtri"
  - "ordinamento di dataset, utilizzo di visualizzazioni dati"
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: filtrare e ordinare i dati in un&#39;applicazione Windows Form
Per filtrare i dati, impostare la proprietà <xref:System.Windows.Forms.BindingSource.Filter%2A> su un'espressione in formato stringa che restituisca i record desiderati.  
  
 Per ordinare i dati, impostare la proprietà <xref:System.Windows.Forms.BindingSource.Sort%2A> sul nome della colonna in base a cui eseguire l'ordinamento, aggiungendo `DESC` per eseguire un ordinamento decrescente o `ASC` per eseguire un ordinamento crescente.  
  
> [!NOTE]
>  Se nell'applicazione non vengono utilizzati componenti <xref:System.Windows.Forms.BindingSource>, è possibile filtrare e ordinare i dati utilizzando oggetti <xref:System.Data.DataView>.  Per ulteriori informazioni, vedere [DataView](../Topic/DataViews.md).  
  
### Per filtrare i dati mediante un componente BindingSource  
  
-   Impostare la proprietà <xref:System.Windows.Forms.BindingSource.Filter%2A> sull’espressione che si desidera venga restituita.  Il codice seguente, ad esempio, restituisce i clienti il cui `CompanyName` inizia con "B":  
  
     [!code-cs[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]  
  
### Per ordinare i dati mediante un componente BindingSource  
  
-   Impostare la proprietà <xref:System.Windows.Forms.BindingSource.Sort%2A> sulla colonna in base a cui eseguire l'ordinamento.  Il codice seguente, ad esempio, consente di ordinare i clienti della colonna `CompanyName` secondo un criterio decrescente:  
  
     [!code-cs[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)