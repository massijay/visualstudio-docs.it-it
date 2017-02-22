---
title: "Il filtro nella finestra di dialogo AddItem per progetti annidati | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applicazione di filtri, progetti annidati"
  - "progetti annidati, finestra di dialogo AddItem casella filtro"
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Il filtro nella finestra di dialogo AddItem per progetti annidati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando si visualizza una finestra di dialogo di **AddItem** per un progetto annidato, il progetto padre possibile controllare quali elementi visualizzati nella finestra di dialogo.  
  
 L'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> consente di filtrare nodi che verranno in una finestra di dialogo di **AddItem** .  Quando il progetto figlio visualizzare la finestra di dialogo di **AddItem** , il padre può implementare l'interfaccia di `IVsFilterAddProjectItemDlg` e filtrare gli elementi che sarebbe altrimenti visualizzato nel progetto figlio.  
  
 Quando i progetti vengono raggruppati dalla funzione in progetti padre specifici, è possibile implementare `IVsFilterAddProjectItemDlg` quando l'utente seleziona **aggiungere l'elemento di progetto** scegliere dal menu di scelta rapida in un progetto annidato.  Implementazione degli elementi di progetto o file di `IvsFilterAddProjectItemDlg displays` solo specifici al gruppo.  Gli elementi di progetto per altri gruppi filtrati dalla finestra di dialogo, anche se sono archiviati nella stessa directory.  
  
 Quando un utente apre la finestra di dialogo di **AddItem** per il figlio, l'implementazione del progetto padre dell'interfaccia di `IVsFilterAddProjectItemDlg` è denominata.  
  
 L'interfaccia di `IVsFilterAddProjectItemDlg` anche possibile implementare un filtro per la categoria.  Per ulteriori informazioni, vedere [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Progetti di annidamento](../../extensibility/internals/nesting-projects.md)