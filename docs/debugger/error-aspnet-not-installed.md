---
title: "Errore: ASP.NET non &#232; installato | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http_not_supported"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, messaggi di errore di installazione"
  - "debugger, errori dell'applicazione Web"
  - "messaggi di errore, ASP.NET"
  - "applicazioni Web, errori"
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: ASP.NET non &#232; installato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo errore si verifica quando [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è installato correttamente nel computer di cui si sta tentando di eseguire il debug.  Questo errore potrebbe essere dovuto al fatto che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è mai stato installato o che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è stato installato prima di IIS.  
  
### Per reinstallare ASP.NET  
  
1.  Da una finestra del prompt dei comandi eseguire il comando seguente:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     dove *version* rappresenta il numero della versione di .NET Framework installata nel computer, ad esempio v1.0.370.  È possibile determinare la versione di :NET Framework aprendo la directory `\WINDOWS\Microsoft.NET\Framework`.  
  
    > [!NOTE]
    >  Con Windows Server 2003 è possibile installare [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dall'applicazione **Installazione applicazioni** del Pannello di controllo.  
  
## Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)