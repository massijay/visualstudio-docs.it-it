---
title: "Procedura: creare una condizione della regola dichiarativa (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "istruzioni condizionali, condizioni di regole dichiarative"
  - "condizioni di regole dichiarative"
  - "Finestra di dialogo Editor condizione della regola"
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Procedura: creare una condizione della regola dichiarativa (legacy)
In questo argomento viene descritto come dichiarare una condizione della regola utilizzando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 L'istruzione relativa a una condizione restituisce **True** o **False**.La condizione della regola dichiarativa è un'istruzione relativa alla condizione che viene creata utilizzando la [Finestra di dialogo Editor condizione della regola \(legacy\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e viene archiviata in formato XML insieme al flusso di lavoro.Può includere predicati che confrontano lo stato del flusso di lavoro con l’algebra booleana che combina più predicati.  
  
 Le condizioni di regole dichiarative vengono utilizzate nelle attività predefinite di Windows Workflow Foundation di seguito riportate:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### Per creare una condizione di regole dichiarative utilizzando l’Editor della condizione della regola  
  
1.  Nella finestra dell’attività **Proprietà**, fare clic sulla proprietà **Condizione** o sulla proprietà **UntilCondition** a seconda dell'attività.  
  
2.  Selezionare **Condizione di regole dichiarative** dall'elenco della proprietà.  
  
3.  Espandere la proprietà **Condizione** o **UntilCondition**.  
  
4.  Fare clic sulla proprietà **ConditionName**.  
  
5.  Fare clic sui puntini di sospensione **\[…\]** di **ConditionName** per aprire la finestra di dialogo **Seleziona condizione**.  
  
6.  Fare clic su **Nuova condizione** per aprire la finestra di dialogo **Editor condizione della regola**.  
  
7.  Digitare l'espressione per la condizione nella casella di testo **Condizione**.  
  
     Per ulteriori informazioni su come creare espressioni della condizione, vedere [Finestra di dialogo Editor condizione della regola \(legacy\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Quando si è finito di creare l'espressione della condizione, fare clic su **OK** per chiudere la finestra di dialogo e creare la condizione della regola con un nome assegnato.  
  
     Verrà visualizzata la finestra di dialogo **Seleziona condizione**.  
  
     Per informazioni sull'utilizzo della finestra di dialogo **Seleziona condizione**, vedere [Finestra di dialogo Seleziona condizione \(legacy\)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## Vedere anche  
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)   
 [Utilizzo dell'attività ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Utilizzo dell'attività IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Utilizzo del ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Utilizzo dell'attività While](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Finestra di dialogo Editor condizione della regola \(legacy\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Finestra di dialogo Seleziona condizione \(legacy\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Utilizzo di condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)