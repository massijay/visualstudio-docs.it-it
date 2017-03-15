---
title: "Supporto per progetti annidati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aggiunta guidata elemento"
  - "progetti annidati, supporto della procedura guidata"
  - "Creazione guidata nuovo progetto"
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Supporto per progetti annidati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'ide esegue due procedure guidate che il progetto padre per i progetti annidati possibile implementare: la procedura guidata di **nuovo progetto** e la procedura guidata di **aggiungere l'elemento** .  
  
 Se un utente avvia la procedura guidata di **nuovo progetto** selezionando **aggiungere il progetto** e facendo clic su **nuovo progetto** il menu File o selezionando **aggiungere** e fare clic con il pulsante destro del mouse **nuovo progetto** in Esplora soluzioni, le esecuzioni dell'IDE il comando di **AddProject** e l'implementazione del progetto padre del comando di **AddProject** restituisce un file di progetto di modello, o un file della procedura guidata \(.vsz\) contenente un set di parametri di contesto.  
  
 Analogamente, un'implementazione del progetto padre delle procedure guidate di **AddItem** restituisce un file VSZ che dispone di un set diverso di parametri di contesto.  
  
 Per ulteriori informazioni sulle procedure guidate, vedere [Procedura guidata \(. File vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md) [Parametri di contesto](../../extensibility/internals/context-parameters.md) [Procedura guidata \(. File vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)e [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Progetti di annidamento](../../extensibility/internals/nesting-projects.md)