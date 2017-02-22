---
title: "La gestione di annullamento e ripristino mediante l&#39;API Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - annullare gestione"
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# La gestione di annullamento e ripristino mediante l&#39;API Legacy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Editor devono supportare le operazioni di annullamento che consentono agli utenti di annullare le modifiche recenti quando si modifica il codice. La maggior parte degli editor implementati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] può avere il supporto di annullamento fornito automaticamente dall'ambiente di sviluppo integrato \(IDE\).  
  
## In questa sezione  
 [Procedura: implementare la gestione di annullamento](../extensibility/how-to-implement-undo-management.md)  
 Fornisce funzionalità di annullamento per gli editor con uno o più viste.  
  
 [Procedura: cancellare lo Stack di annullamento](../extensibility/how-to-clear-the-undo-stack.md)  
 Viene descritto come cancellare un stack di annullamento.  
  
 [Procedura: utilizzare la gestione di annullamento collegato](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora gestione annullamento collegato nell'editor.  
  
## Riferimenti  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fornisce la gestione di annullamento per un editor che supporta più viste.  
  
## Sezioni correlate