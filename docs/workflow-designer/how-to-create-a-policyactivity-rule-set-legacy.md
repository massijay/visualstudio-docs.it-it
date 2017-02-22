---
title: "Procedura: creare un set di regole per l&#39;attivit&#224; PolicyActivity (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Attività PolicyActivity, creazione set di regole"
  - "attività PolicyActivity, selezione set di regole"
  - "Finestra di dialogo Editore set di regole"
  - "set di regole, creazione per PolicyActivity"
  - "Finestra di dialogo Seleziona set di regole"
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: creare un set di regole per l&#39;attivit&#224; PolicyActivity (legacy)
In questo argomento viene descritto come creare un set di regole per PolicyActivity utilizzando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Dopo avere trascinato un elemento dell'attività **Policy** dalla **Casella degli strumenti** all'area di progettazione del flusso di lavoro, sarà necessario selezionare un set di regole esistente o crearne uno nuovo per l'attività [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019).Selezionare un insieme di regole esistente utilizzando [Finestra di dialogo Seleziona set di regole \(legacy\)](../workflow-designer/select-rule-set-dialog-box-legacy.md) e creare insieme di regole utilizzando [Finestra di dialogo Editor set di regole \(legacy\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  È possibile aprire direttamente la finestra di dialogo [Finestra di dialogo Editor set di regole \(legacy\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) facendo doppio clic su un'attività [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) sull'area di progettazione del flusso di lavoro.  
  
### Per selezionare o creare un insieme di regole per un'attività di Policy  
  
1.  Fare clic con il pulsante destro del mouse sull'attività [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), quindi scegliere **Proprietà** per aprire la finestra **Proprietà**.  
  
2.  Fare clic sulla proprietà **RuleSetReference**.  
  
3.  Eseguire una delle operazioni seguenti:  
  
    -   Fare clic sui puntini di sospensione **\[…\]** di **RuleSetReference** e selezionare un set di regole esistente in [Finestra di dialogo Seleziona set di regole \(legacy\)](../workflow-designer/select-rule-set-dialog-box-legacy.md).Andare al passaggio 10.  
  
         \-oppure\-  
  
    -   Digitare il nome da assegnare al set di regole.Fare clic sui puntini di sospensione **\[.\]** di **RuleSetReference** e selezionare **Modifica** in [Finestra di dialogo Seleziona set di regole \(legacy\)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         \-oppure\-  
  
    -   Digitare il nome da assegnare al set di regole.Espandere la proprietà **RuleSetReference** e selezionare i puntini di sospensione **\[.\]** nella proprietà **RuleSet Definition**.  
  
         Viene aperta la [Finestra di dialogo Editor set di regole \(legacy\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
4.  Nella [Finestra di dialogo Editor set di regole \(legacy\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), fare clic su **Aggiungi regola** per aggiungere una regola nuova al set di regole.  
  
5.  Immettere **Nome**, **Priorità** e proprietà **Nuova valutazione** oppure mantenere i valori predefiniti.  
  
6.  Immettere il testo per la **Condizione**.  
  
7.  Immettere il testo per **Azioni THEN** e **Azioni ELSE**.  
  
8.  Fare clic nuovamente su **Aggiungi regola** per aggiungere un'altra regola.  
  
9. Al termine, scegliere **OK**.  
  
## Vedere anche  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Finestra di dialogo Seleziona set di regole \(legacy\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Finestra di dialogo Editor set di regole \(legacy\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)