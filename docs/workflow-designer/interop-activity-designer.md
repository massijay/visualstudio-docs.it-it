---
title: "ActivityDesigner Interop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Interop.UI"
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# ActivityDesigner Interop
L'ActivityDesigner **Interop** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.Interop>.  
  
## Attività Interop  
 L'attività <xref:System.Activities.Statements.Interop> gestisce l'esecuzione dei tipi che derivano da <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> all'interno di un flusso di lavoro.  
  
### Utilizzo dell'ActivityDesigner Interop  
 L'ActivityDesigner **Interop** è disponibile nella categoria **Migrazione** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti**. In alternativa, è possibile scegliere **Casella degli strumenti**  dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 La categoria [Migrazione](../workflow-designer/migration-activity-designers.md) che contiene l'attività <xref:System.Activities.Statements.Interop> è presente nella **Casella degli strumenti** solo se il progetto è destinato alla versione completa di [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)].  
  
 Per i progetti in C\#, è possibile modificare la destinazione del progetto in modo che venga utilizzata la versione completa di [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] facendo clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliendo **Proprietà**.Nella scheda **Applicazione** selezionare l'opzione **.NET Framework 4** in **Framework di destinazione**.Selezionare il pulsante **Sì** nella finestra di dialogo **Modifica versione .NET Framework di destinazione**. Verrà richiesto di confermare la modifica.  
  
 Per i progetti in VB, è possibile modificare la destinazione del progetto in modo che venga utilizzata la versione completa di **[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] facendo clic con il pulsante destro del mouse sul progetto in Esplora soluzioni** e scegliendo **Proprietà**.Nella scheda **Compilazione** fare clic sul pulsante **Opzioni di compilazione avanzate**.Selezionare **.Net Framework 4** nell'elenco **Framework di destinazione** e quindi fare clic su **OK**.Fare clic sul pulsante **Sì** nella finestra di dialogo **Modifica versione .NET Framework di destinazione**. Verrà richiesto di confermare la modifica.  
  
 È possibile trascinare l'ActivityDesigner **Interop** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.Interop> con la proprietà **DisplayName** impostata sul valore predefinito Interop.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **Interop** o nella casella **DisplayName** della griglia delle proprietà.  
  
 Fare clic sul testo **Fare clic per cercare** nella casella **ActivityType**, sull'ActivityDesigner **Interop**  oppure nella griglia delle proprietà per visualizzare la finestra di dialogo **Cerca e seleziona un tipo .NET**.Vengono visualizzati solo i tipi relativi alle attività del flusso di lavoro 3.0 o del flusso di lavoro 3.5, ovvero solo i tipi derivati da <xref:System.Workflow.ComponentModel.Activity>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] utilizzo di questa casella per specificare un tipo, vedere gli argomenti di [Finestra di dialogo Cerca e seleziona un tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).  
  
### Proprietà di Interop  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.Interop> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Interop>.L'impostazione predefinita è Interop.Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'utilizzo.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Consente di specificare il tipo di attività incluso nell'attività <xref:System.Activities.Statements.Interop>.Tale tipo specificato deve derivare da <xref:System.Workflow.ComponentModel.Activity>.|  
  
## Vedere anche  
 [Migrazione](../workflow-designer/migration-activity-designers.md)