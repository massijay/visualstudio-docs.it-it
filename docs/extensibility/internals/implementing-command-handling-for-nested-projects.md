---
title: "Implementazione di gestione dei comandi per progetti annidati | Microsoft Docs"
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
  - "progetti annidati, che implementa la gestione dei comandi"
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementazione di gestione dei comandi per progetti annidati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'ide possibile passare i controlli che vengono passati tra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> e le interfacce di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ai progetti annidati, o i progetti padre possono filtrare o eseguire l'override dei controlli.  
  
> [!NOTE]
>  Solo i controlli normalmente gestiti dal progetto padre possono essere filtrati.  I controlli come **Build** e **Deploy** che vengono gestiti dall'IDE non possono essere filtrati.  
  
 Nei passaggi seguenti viene descritto il processo per implementare la gestione del comando.  
  
## Procedure  
  
#### Per applicare gestione di comando  
  
1.  Quando l'utente seleziona un progetto annidato o un nodo in un annidato progetti:  
  
    1.  The IDE calls the <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> method.  
  
     —oppure—  
  
    1.  Se il comando ha avuto origine in una finestra gerarchia, quale un comando in Esplora soluzioni il menu di scelta rapida, l'ide chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> nell'elemento padre del progetto.  
  
2.  Il progetto padre possibile esaminare i parametri da passare a `QueryStatus`, come `pguidCmdGroup` e `prgCmds`, per determinare se il progetto padre necessario filtrare i controlli.  Se il progetto padre viene implementato filtrare i controlli, deve impostare:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     Quindi il progetto padre deve restituire `S_OK`.  
  
     Se il progetto padre non filtra il comando, deve restituire solo `S_OK`.  In questo caso, l'ide automaticamente illustrato il comando al progetto figlio.  
  
     Il progetto padre non deve soddisfare il comando al progetto figlio.  L'ide esegue questa attività.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [I comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Progetti di annidamento](../../extensibility/internals/nesting-projects.md)