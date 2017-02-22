---
title: "Applicazioni server SDI | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "applicazioni server SDI"
  - "applicazioni server SDI, debug"
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Applicazioni server SDI
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si esegue il debug di un'applicazione server SDI, è necessario specificare `/Embedding` o `/Automation` nella proprietà **Argomenti della riga di comando** disponibile nella finestra di dialogo Pagine delle proprietà di *Project* per i progetti C\/C\+\+, C\# o Visual Basic.  
  
 Grazie a questi argomenti della riga di comando, il debugger è in grado di avviare l'applicazione server come se tale avvio venisse eseguito da un contenitore.  In seguito all'avvio del contenitore da Program Manager o File Manager, il contenitore utilizzerà l'istanza del server già avviata dal debugger.  
  
## Ricerca della proprietà Argomenti della riga di comando  
 Per accedere alla finestra di dialogo Pagine delle proprietà di *Project*, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere Proprietà dal menu di scelta rapida  Per individuare la proprietà Argomenti della riga di comando, espandere la categoria Proprietà di configurazione e fare clic sulla pagina Debug.  
  
## Vedere anche  
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Procedura: eseguire il debug di server COM](../debugger/how-to-debug-com-servers.md)