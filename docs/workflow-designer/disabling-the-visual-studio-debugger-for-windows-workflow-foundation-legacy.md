---
title: "Disattivazione del debugger di Visual Studio per Windows Workflow Foundation (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "debug dei flussi di lavoro, disattivazione debugger"
  - "debugger del flusso di lavoro, disattivazione"
  - "flussi di lavoro, disattivazione debugger"
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Disattivazione del debugger di Visual Studio per Windows Workflow Foundation (legacy)
In questo argomento viene descritto come disabilitare il Debugger [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizzando il file di configurazione in caso di compilazione di applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy.Utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Per impostazione predefinita, il debugger di [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] per [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] è abilitato per un processo host.Per disabilitare il flusso di lavoro è necessario disattivarlo in modo esplicito aggiungendo la voce "DisableWorkflowDebugging" all'elemento **\<switches\>** nella sezione **\<system.diagnostics\>** del file di configurazione dell’host.  
  
 Nell’esempio seguente viene illustrato come modificare il file di configurazione dell’host per disabilitare il debug del flusso di lavoro.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="DisableWorkflowDebugging" value="true"/>  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## Vedere anche  
 [Richiamo del debugger di Visual Studio per Windows Workflow Foundation \(legacy\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)