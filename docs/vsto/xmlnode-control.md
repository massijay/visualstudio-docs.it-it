---
title: "Controllo XMLNode"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "XMLNode (controllo)"
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Controllo XMLNode
  **importante** le informazioni relative in questo argomento relative a Microsoft Word è verificato esclusivamente per il vantaggio e l'utilizzo degli utenti e le organizzazioni che si trovano fuori dagli Stati Uniti e i relativi territori, o sviluppano programmi eseguiti con prodotti, Microsoft Word che sono stati concessi in licenza da Microsoft prima del gennaio 2010, quando È stato rimosso un'implementazione di determinata funzionalità correlata alla classe personalizzata XML da Microsoft Word.  Queste informazioni relative a Microsoft Word non possono essere lette o utilizzate dagli individui o delle organizzazioni che si trovano negli Stati Uniti o nei relativi territori oppure che usano o sviluppano programmi eseguiti con prodotti Microsoft Word concessi in licenza da Microsoft dopo il 10 gennaio 2010. Questi prodotti funzioneranno in modo diverso rispetto a quelli concessi in licenza prima di tale data oppure acquistati e concessi in licenza per l'uso all'esterno degli Stati Uniti.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Il controllo <xref:Microsoft.Office.Tools.Word.XMLNode> rappresenta un nodo XML mappato che espone eventi e può essere associato a dati.  Il controllo <xref:Microsoft.Office.Tools.Word.XMLNode> viene creato solo quando un elemento non ripetuto dello schema viene mappato in un documento di Microsoft Office Word.  Una volta che Visual Studio ha creato il nodo XML è possibile eseguire la programmazione per questo oggetto in modo diretto, senza dover passare al modello a oggetti di Word.  
  
 Il controllo <xref:Microsoft.Office.Tools.Word.XMLNode> può essere eliminato solo rimuovendo il mapping dell'elemento in Word.  
  
## Associazione di dati al controllo  
 Un controllo <xref:Microsoft.Office.Tools.Word.XMLNode> supporta solo l'associazione dati semplice.  Il nodo XML deve essere associato a un'origine dati tramite la proprietà <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>.  Se i dati nel dataset associato vengono aggiornati, il controllo <xref:Microsoft.Office.Tools.Word.XMLNode> rifletterà tali modifiche.  
  
## Formattazione  
 La formattazione applicabile a un oggetto <xref:Microsoft.Office.Interop.Word.XMLNode> può essere applicata anche a un controllo <xref:Microsoft.Office.Tools.Word.XMLNode>.  Sono inclusi i tipi di carattere, gli stili di sottolineatura e gli stili dei caratteri.  
  
## Eventi  
 I seguenti eventi sono disponibili per il controllo <xref:Microsoft.Office.Tools.Word.XMLNode>:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## Confronto di eventi  
 È possibile acquisire un evento quando l'utente sposta il cursore nel contesto di un particolare controllo <xref:Microsoft.Office.Tools.Word.XMLNode>.  Ad esempio, è possibile disporre di un controllo <xref:Microsoft.Office.Tools.Word.XMLNode> denominato `Customer` che dispone di un controllo figlio <xref:Microsoft.Office.Tools.Word.XMLNode> denominato `Company` e di un controllo `Company` che dispone di due controlli figlio <xref:Microsoft.Office.Tools.Word.XMLNode> denominati `CompanyName` e `CompanyRegion` come illustrato di seguito.  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Se si desidera visualizzare un controllo nel riquadro delle azioni ogni volta che il cursore viene spostato nel nodo `Company`, la posizione del cursore in `CompanyName` o in `CompanyRegion` non è determinante, poiché questi due controlli sono entrambi nel contesto di `Company`.  In questo caso, il codice può essere creato nell'evento <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> di `Company`.  
  
 Nella maggior parte dei casi, quando il cursore è spostato su un controllo <xref:Microsoft.Office.Tools.Word.XMLNode>, vengono generati gli eventi <xref:Microsoft.Office.Tools.Word.XMLNode.Select> e <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>.  Nella tabella che segue sono illustrate le differenze tra questi eventi.  
  
|Evento Select|Evento ContextEnter|  
|-------------------|-------------------------|  
|Viene generato quando il cursore è posizionato all'interno di un controllo <xref:Microsoft.Office.Tools.Word.XMLNode>.|Viene generato quando il cursore viene posizionato in un nodo <xref:Microsoft.Office.Tools.Word.XMLNode> o in uno dei nodi figlio, da un'area esterna dal contesto del nodo.  In altre parole, viene generato solo quando il contesto cambia.|  
  
 Ad esempio, quando si sposta il cursore da `Customer` a `CompanyName`, viene generato l'evento <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> per `Customer`, `Company` e `CompanyName`.  Se poi si sposta il cursore da `CompanyName` a `CompanyRegion`, viene generato solo l'evento <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> per `CompanyRegion`, in quanto il cursore rimane nel contesto di `Company` e `Customer`.  
  
 Le stesse differenze distinguono l'evento <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> dall'evento <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>.  
  
## Vedere anche  
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Controllo XMLNodes](../vsto/xmlnodes-control.md)   
 [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Procedura: effettuare il mapping degli schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  