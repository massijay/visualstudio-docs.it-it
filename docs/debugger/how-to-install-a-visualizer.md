---
title: "Procedura: installare un visualizzatore | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, visualizzatori"
  - "visualizzatori, installazione"
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# Procedura: installare un visualizzatore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dopo avere creato un visualizzatore, è necessario installarlo in modo da renderlo disponibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Per installare un visualizzatore è sufficiente seguire una semplice procedura.  
  
> [!NOTE]
>  Nelle app di **Store** sono supportati solo i visualizzatori di testo standard, HTML, XML e JSON.  Non sono supportati i visualizzatori personalizzati \(creati dall'utente\).  
  
### Per installare un visualizzatore  
  
1.  Individuare la DLL contenente il visualizzatore compilato.  
  
2.  Copiare la DLL in uno dei seguenti percorsi:  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  Se si desidera usare un visualizzatore gestito per il debug remoto, copiare la DLL nello stesso percorso nel computer remoto.  
  
4.  Riavviare la sessione di debug.  
  
## Vedere anche  
 [Visualizzatori](../debugger/create-custom-visualizers-of-data.md)   
 [Procedura: scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)