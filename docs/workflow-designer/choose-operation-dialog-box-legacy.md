---
title: "Finestra di dialogo Seleziona operazione (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Design.OperationPickerDialog.UI"
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Finestra di dialogo Seleziona operazione (legacy)
In questo argomento viene descritto come utilizzare la finestra di dialogo **Seleziona operazione** in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy.Utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 La finestra di dialogo **Seleziona operazione** viene utilizzata per selezionare un'operazione da associare a un'attività <xref:System.Workflow.Activities.ReceiveActivity> o a un'attività <xref:System.Workflow.Activities.SendActivity>.Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo con tali attività, vedere [Procedura: implementare un'operazione del contratto WCF \(legacy\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) e [Procedura: richiamare un'operazione del contratto WCF \(legacy\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente \(Interfaccia utente\) della finestra di dialogo **Seleziona operazione**.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|--------------------------------------|-----------------|  
|**Aggiungi contratto**|Crea un nuovo contratto,in cui è possibile definire nuove operazioni.\(Utilizzato solo con <xref:System.Workflow.Activities.ReceiveActivity>.\)|  
|**Aggiungi operazione**|Aggiunge nuove operazioni a un nuovo contratto creato nella finestra di dialogo **Seleziona operazione**. **Note:**  È possibile aggiungere nuove operazioni solo ai contratti creati tramite la finestra di dialogo **Seleziona operazione**. <br /><br /> \(Utilizzato solo con <xref:System.Workflow.Activities.ReceiveActivity>.\)|  
|**Importa…**|Importa un contratto definito in precedenza e consente di selezionare un'operazione da tale contratto.|  
|**Nome operazione**|Nome dell'operazione attualmente selezionata.Questa casella di testo è disponibile per la modifica solo se è stata creata un'operazione tramite la finestra di dialogo **Seleziona operazione**.|  
|**Parametri**|Scheda contenente le definizioni di parametro per l'operazione attualmente selezionata. **Note:**  Le definizioni di parametro possono essere modificate solo se è stata creata un'operazione tramite la finestra di dialogo **Seleziona operazione**.|  
|**Proprietà**|Scheda contenente le impostazioni di <xref:System.Net.Security.ProtectionLevel> per i messaggi scambiati fra il client e il servizio. **Note:**  Questa scheda è abilitata solo se è stata creata un'operazione tramite la finestra di dialogo **Seleziona operazione**.|  
|**Autorizzazioni**|Scheda contenente le proprietà <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> e <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> degli utenti autorizzati a chiamare tale operazione.Ad esempio, se solo gli utenti del gruppo Administrators sono autorizzati a chiamare tale operazione, è necessario scrivere "Amministratori" nella casella di testo **Ruolo**.<br /><br /> Questa scheda è abilitata per le operazioni create tramite la finestra di dialogo **Selezionaoperazione** e per quelle importate tramite il pulsante **Importa**.|  
  
> [!NOTE]
>  Nella finestra di dialogo **Seleziona operazione** vengono visualizzati solo i contratti o le operazioni utilizzati da altre attività <xref:System.Workflow.Activities.SendActivity> nel flusso di lavoro.Analogamente, nella finestra di dialogo **Seleziona operazione** per le attività <xref:System.Workflow.Activities.ReceiveActivity> vengono visualizzati solo i contratti o le operazioni utilizzati da altre attività **ReceiveActivity** nel flusso di lavoro.  
  
## Vedere anche  
 [Procedura: implementare un'operazione del contratto WCF \(legacy\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Procedura: richiamare un'operazione del contratto WCF \(legacy\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Finestra di progettazione legacy per la Guida interfaccia utente di Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)