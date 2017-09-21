---
title: "Procedura: eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati | Microsoft Docs"
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
  - "BindingSource (classe), esecuzione del commit di record modificati"
  - "esecuzione del commit di record modificati"
  - "DataBinding (classe), esecuzione del commit di record modificati"
  - "controlli con associazione a dati, modifiche in-process"
  - "EndEdit (metodo)"
  - "aggiornamento gerarchico, esecuzione del commit di record modificati"
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati
Quando si modificano i valori nei controlli con associazione a dati, è necessario spostarsi dal record corrente per eseguire il commit del valore aggiornato nell'origine dati sottostante a cui è associato il controllo.  Quando si trascinano gli elementi dalla [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md) in un form, il primo elemento rilasciato genera il codice nell'evento Click del pulsante Salva di <xref:System.Windows.Forms.BindingNavigator>.  Il codice chiama il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> dell'oggetto <xref:System.Windows.Forms.BindingSource>.  Pertanto, la chiamata al metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> viene generata solo per il primo oggetto <xref:System.Windows.Forms.BindingSource> aggiunto al form.  
  
 La chiamata al metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> esegue il commit di tutte le modifiche in corso nei controlli con associazione a dati che si stanno modificando.  Pertanto, se un controllo con associazione a dati ha lo stato attivo e si fa clic sul pulsante **Salva**, prima del salvataggio effettivo verrà eseguito il commit di tutte le modifiche in sospeso nel controllo \(metodo `TableAdapterManager.UpdateAll`\).  
  
 È possibile configurare l'applicazione in modo da eseguire automaticamente il commit delle modifiche, anche se un utente tenta di salvare i dati senza eseguire il commit delle modifiche, come parte del processo di salvataggio.  
  
> [!NOTE]
>  La finestra di progettazione aggiunge il codice `BindingSource.EndEdit` solo per il primo elemento rilasciato in un form.  Pertanto, è necessario aggiungere una riga di codice per chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni oggetto <xref:System.Windows.Forms.BindingSource> nel form.  È possibile aggiungere manualmente una riga di codice per chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni oggetto <xref:System.Windows.Forms.BindingSource>.  In alternativa, è possibile aggiungere il metodo `EndEditOnAllBindingSources` al form e chiamarlo prima di eseguire un salvataggio.  
  
 Nel codice seguente viene utilizzata una query [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) per scorrere tutti i componenti <xref:System.Windows.Forms.BindingSource> e chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni oggetto <xref:System.Windows.Forms.BindingSource> in un form.  
  
### Per chiamare il metodo EndEdit per tutti i componenti BindingSource in un form  
  
1.  Aggiungere il codice seguente al form contenente i componenti <xref:System.Windows.Forms.BindingSource>.  
  
     [!code-cs[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]  
  
2.  Aggiungere la seguente riga di codice prima di qualsiasi chiamata per salvare i dati del form \(metodo `TableAdapterManager.UpdateAll()`\):  
  
     [!code-cs[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]  
  
## Vedere anche  
 [Cenni preliminari sull'aggiornamento gerarchico](../Topic/Hierarchical%20Update%20Overview.md)   
 [Panoramica di TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cenni preliminari sul componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)