---
title: "Controllo XMLNodes | Microsoft Docs"
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
  - "XMLNodes (controllo)"
  - "XMLNodes (controllo), eventi"
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Controllo XMLNodes
  **importante** le informazioni relative in questo argomento relative a Microsoft Word è verificato esclusivamente per il vantaggio e l'utilizzo degli utenti e le organizzazioni che si trovano fuori dagli Stati Uniti e i relativi territori, o sviluppano programmi eseguiti con prodotti, Microsoft Word che sono stati concessi in licenza da Microsoft prima del gennaio 2010, quando È stato rimosso un'implementazione di determinata funzionalità correlata alla classe personalizzata XML da Microsoft Word.  Queste informazioni relative a Microsoft Word non possono essere lette o utilizzate dagli individui o delle organizzazioni che si trovano negli Stati Uniti o nei relativi territori oppure che usano o sviluppano programmi eseguiti con prodotti Microsoft Word concessi in licenza da Microsoft dopo il 10 gennaio 2010. Questi prodotti funzioneranno in modo diverso rispetto a quelli concessi in licenza prima di tale data oppure acquistati e concessi in licenza per l'uso all'esterno degli Stati Uniti.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Il controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> è una raccolta di oggetti nodo XML mappati che espone eventi.  Il controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> viene creato solo quando un elemento ripetuto dello schema viene mappato in un documento di Microsoft Office Word.  Se l'elemento ripetuto contiene elementi figlio, questi verranno creati come controlli <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
 Una volta che Visual Studio ha creato la raccolta di nodi XML è possibile eseguire la programmazione per il controllo direttamente, senza dover passare al modello a oggetti di Word.  Il controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> può essere eliminato solo rimuovendo il mapping dell'elemento dal documento.  
  
> [!NOTE]  
>  Se si accede a un elemento figlio del controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> mediante la proprietà <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A>, viene restituito un oggetto <xref:Microsoft.Office.Interop.Word.XMLNode> invece di un controllo <xref:Microsoft.Office.Tools.Word.XMLNode>.  Per ulteriori informazioni, vedere [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## Associazione di dati al controllo  
 Un controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> non supporta l'associazione dati.  Questa condizione si verifica perché il controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> non dispone della funzionalità di associazione dati complessa e l'associazione dati semplice non è in grado di rappresentare i dati ripetuti.  
  
## Formattazione  
 La formattazione che è possibile applicare al testo all'interno del documento può essere applicata a un controllo <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## Eventi  
 Gli eventi disponibili per il controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> sono:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## Confronto di eventi  
 È possibile acquisire un evento quando l'utente sposta il cursore nel contesto di un particolare controllo <xref:Microsoft.Office.Tools.Word.XMLNodes>.  Ad esempio, è possibile disporre di un controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> denominato `Customer` che dispone di un controllo figlio <xref:Microsoft.Office.Tools.Word.XMLNodes> denominato `Company` e di un controllo `Company` che dispone di due controlli figlio <xref:Microsoft.Office.Tools.Word.XMLNodes> denominati `CompanyName` e `CompanyRegion` come illustrato di seguito.  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Se si desidera visualizzare un controllo nel riquadro delle azioni ogni volta che il cursore viene spostato nel nodo `Company`, la posizione del cursore in `CompanyName` o in `CompanyRegion` non è determinante, poiché questi due controlli sono entrambi nel contesto di `Company`.  In questo caso, il codice può essere creato nell'evento <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> di `Company`.  
  
 Nella maggior parte dei casi, quando il cursore è spostato su un controllo <xref:Microsoft.Office.Tools.Word.XMLNodes>, vengono generati gli eventi <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> e <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>.  Nella tabella che segue sono illustrate le differenze tra questi eventi.  
  
|Evento Select|Evento ContextEnter|  
|-------------------|-------------------------|  
|Viene generato quando il cursore viene posizionato all'interno di uno dei nodi della raccolta <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Viene generato quando il cursore viene posizionato in uno dei nodi o dei nodi di discendente della raccolta <xref:Microsoft.Office.Tools.Word.XMLNodes>, da un'area esterna del contesto del nodo.  In altre parole, l'evento viene generato solo quando il contesto cambia e può essere generato per più controlli <xref:Microsoft.Office.Tools.Word.XMLNodes> annidati.|  
  
 Ad esempio, quando si sposta il cursore da `Customer` a `CompanyName`, vengono generati gli eventi <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> per `Customer`, `Company` e `CompanyName`.  Se poi si sposta il cursore da `CompanyName` a `CompanyRegion`, viene generato solo l'evento <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> per `CompanyRegion`, in quanto il contesto di `Company` e `Customer` è uguale.  Nel documento possono essere presenti più nodi `Company`.  Se si sposta il cursore dal nodo `CompanyName` di un nodo `Company` al nodo `CompanyName` di un altro nodo `Company`, il contesto è lo stesso, per cui viene generato solo l'evento <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>.  
  
 Le stesse differenze distinguono l'evento <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> dall'evento <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>.  
  
## Vedere anche  
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Controllo XMLNode](../vsto/xmlnode-control.md)   
 [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Procedura: effettuare il mapping degli schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  