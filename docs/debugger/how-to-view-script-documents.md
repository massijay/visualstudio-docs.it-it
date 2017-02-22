---
title: "Procedura: visualizzare documenti script | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
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
helpviewer_keywords: 
  - "Esplora script"
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: visualizzare documenti script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nelle versioni precedenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i file script sul lato client generati da uno script sul lato server venivano visualizzati nella finestra Esplora script.  La finestra Esplora script era spesso nascosta, per cui la disponibilità di script sul lato client non era sempre ovvia.  
  
 In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] i file script sul lato client generati da uno script sul lato server vengono visualizzati in Esplora soluzioni, visualizzata per impostazione predefinita.  La finestra Esplora script è stata eliminata.  
  
 I file script sul lato client sono visibili solo in modalità di debug o in modalità interruzione.  Vengono visualizzati nel nodo **Documenti script**.  
  
 I file script sul lato server sono sempre visibili.  Vengono visualizzati nel nodo **\<Percorso sito Web\>**.  Il nome del nodo è simile a quello riportato nell'esempio seguente: `c:\...\Website2\`  
  
### Per visualizzare un documento script sul lato server  
  
1.  In **Esplora soluzioni** aprire il nodo**\<Percorso sito Web\>**.  
  
2.  Fare doppio clic sul file script che si desidera visualizzare.  
  
     Il file script sul lato server verrà aperto in una finestra di origine.  
  
### Per visualizzare un documento script sul lato client  
  
1.  In **Esplora soluzioni** aprire il nodo **Documenti script**.  
  
2.  Fare doppio clic sul file script che si desidera visualizzare.  
  
     Il file script sul lato client verrà aperto in una finestra di origine.  
  
## Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)