---
title: "Finestra di dialogo Personalizza associazione controllo | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datauicustomization"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Personalizza associazione controlli (finestra di dialogo)"
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Finestra di dialogo Personalizza associazione controllo
Utilizzare la finestra di dialogo **Personalizza associazione controllo** per specificare quali controlli sono disponibili per gli elementi nella [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  
  
 A ogni elemento nella finestra **Origini dati** è abbinato un elenco di controlli che possono essere associati all'elemento.  I controlli disponibili per ciascun elemento sono determinati dal tipo di dati dell'elemento.  In questa finestra di dialogo è definito, per ciascun tipo di dati, un elenco di controlli associati validi, incluso un controllo predefinito.  
  
 Prima di trascinare un elemento in un'area di progettazione per creare un controllo associato a dati, è possibile selezionare quale controllo creare.  Se si trascina un elemento dalla finestra **Origini dati** in un'area di progettazione senza selezionare un controllo, all'area di progettazione verrà aggiunto il controllo predefinito per il tipo di dati dell'elemento selezionato.  
  
 Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo per personalizzare l'elenco di controlli per gli elementi presenti nella finestra **Origini dati**, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## Elenco UIElement  
 **Tipo di dati**  
 Consente di visualizzare un elenco di tipi da associare ai controlli:  
  
-   Tabelle, entità e oggetti vengono rappresentati come tipi **\[Elenco\]**.  
  
-   Le colonne o le proprietà pubbliche di entità e oggetti vengono rappresentate come tipo di dati effettivo della colonna o della proprietà nell'archivio dati sottostante.  
  
-   Gli oggetti con forme definite dall'utente vengono rappresentati come **\[Altro\]**.  Se ad esempio l'applicazione include un controllo personalizzato che visualizza i dati di più proprietà di un oggetto, selezionare il tipo di dati **\[Altro\]** per il controllo.  
  
 **Controlli associati**  
 Consente di visualizzare un elenco di controlli ai quali è possibile associare un particolare tipo di dati.  Se si desidera associare un particolare controllo al tipo di dati selezionato nell'elenco **Tipo di dati**, selezionare la corrispondente casella di controllo.  Per rimuovere un'associazione, invece, deselezionare la casella di controllo.  I controlli selezionati vengono visualizzati nel menu di scelta rapida presentato dalla finestra **Origini dati** per un elemento del tipo di dati associato.  
  
 È possibile aggiungere controlli all'elenco aggiungendo alla **Casella degli strumenti** controlli che dispongono di uno dei diversi attributi di associazione dati.  Per ulteriori informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 **Imposta predefinito**  
 Consente di assegnare il tipo di controllo selezionato come controllo predefinito per gli elementi del tipo di dati selezionato.  Il controllo predefinito viene visualizzato come prima selezione nel menu di scelta rapida presentato dalla finestra **Origini dati** per un elemento.  È possibile assegnare un solo tipo di controllo come controllo predefinito per il tipo di dati.  
  
 **Cancella predefinito**  
 Consente di rimuovere la designazione di un controllo come predefinito per il tipo di dati selezionato.  Se non esiste alcun controllo predefinito per il tipo di dati selezionato, verrà visualizzato **\[Nessuno\]** come prima selezione nel menu di scelta rapida presentato dalla finestra **Origini dati** per un elemento del tipo associato.  
  
## Vedere anche  
 [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)