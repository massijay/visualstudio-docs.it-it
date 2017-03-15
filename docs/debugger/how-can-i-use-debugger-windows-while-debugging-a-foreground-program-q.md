---
title: "Come &#232; possibile utilizzare le finestre debugger mentre si esegue il debug di un programma in primo piano? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.background"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "debug [Visual Studio], programmi in primo piano"
  - "debug [Visual Studio], durante l'osservazione di programmi in primo piano"
  - "stato attivo, debug durante l'osservazione di programmi in primo piano"
  - "debug di programmi in primo piano"
  - "debug remoto, debug di programmi in primo piano"
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Come &#232; possibile utilizzare le finestre debugger mentre si esegue il debug di un programma in primo piano?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrizione del problema  
 Si sta tentando di effettuare il debug di un problema relativo a un disegno dello schermo.  Per osservare questo problema è necessario mantenere il programma in primo piano, ma in questo modo è impossibile accedere alle finestre di debug.  Come è possibile procedere?  
  
## Soluzione  
 Se si dispone di un secondo computer, sarà possibile ricorrere al debug remoto.  Con una configurazione su due computer sarà possibile osservare il disegno dello schermo sul computer remoto mentre si esegue il debugger sull'host.  Per ulteriori informazioni sul debug remoto, vedere [Impostazione del debug remoto](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
## Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)