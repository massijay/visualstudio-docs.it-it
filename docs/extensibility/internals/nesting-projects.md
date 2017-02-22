---
title: "Progetti di annidamento | Microsoft Docs"
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
  - "nidificazione di progetto"
  - "progetti annidati"
  - "progetti [Visual Studio SDK], progetti figlio"
  - "nidificazione di progetti [Visual Studio SDK]"
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Progetti di annidamento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli sviluppatori di applicazioni aziendali che utilizzano il pacchetto di Visual Studio possono consentono di raggruppare tipi simili di insieme in progetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzando *progetto nidificazione*. Ad esempio, il progetto di modello Enterprise utilizza progetti annidati per i progetti di gruppo di categorie. Business facciata progetti, progetti dell'interfaccia utente Web e così via vengono raggruppati in una categoria.  
  
 In questo scenario, non esiste alcun limite al numero di progetti che lo sviluppatore può nidificati sotto ogni progetto padre, anche se lo sviluppatore può specificare a livello di codice i limiti. Questo tipo di raggruppamento può essere effettuato anche ricorsivo, nel qual caso i progetti dello stesso tipo di progetto figlio possono essere nidificati sotto l'elemento figlio per diventare un sottoprogetto del figlio, ovvero un sottoprogetto del padre.  
  
 Annidamento di progetto non è una parte intrinseca di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. È necessario scrivere il codice per abilitare l'annidamento e sottoprogetto annidamento all'interno dei progetti figlio. Il progetto principale è un VSPackage speciale, o tipo di progetto creato e registrato con un proprio GUID che include il codice necessario per implementare la nidificazione di progetto.  
  
 Nell'esempio c\# Example.Nested Project, è possibile trovare un esempio di progetti annidati.  
  
## Esempio di progetti annidati  
 ![Soluzione di progetti annidati](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Esempio di progetti annidati  
  
## Vedere anche  
 [Procedura: implementare progetti annidati](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Considerazioni per scaricare e ricaricare progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Supporto per progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementazione di gestione dei comandi per progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Il filtro nella finestra di dialogo AddItem per progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [Procedura guidata \(. File vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)