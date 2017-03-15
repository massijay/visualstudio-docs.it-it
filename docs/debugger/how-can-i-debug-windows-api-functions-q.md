---
title: "Come &#232; possibile eseguire il debug di funzioni API Windows? | Microsoft Docs"
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
  - "vs.debug.api"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "API, debug"
  - "debug [C++], funzioni API Windows"
  - "simboli NT e debug di funzioni API Windows"
  - "funzioni API Windows, debug"
  - "API Windows, debug di funzioni API"
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Come &#232; possibile eseguire il debug di funzioni API Windows?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per eseguire il debug di una funzione API Windows con NT Symbols caricato, effettuare le operazioni seguenti.  
  
### Per impostare un punto di interruzione su una funzione Windows API con NT Symbols caricato  
  
-   Immettere il nome della funzione e il nome della DLL in cui risiede la funzione.  Nel codice a 32 bit, utilizzare la forma decorata del nome della funzione.  Per impostare un punto di interruzione su **MessageBeep**, ad esempio, è necessario immettere quanto segue.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Per ottenere il nome decorato, vedere [Viewing Decorated Names](http://msdn.microsoft.com/it-it/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)