---
title: "DebugBreak e __debugbreak | Microsoft Docs"
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
  - "DebugBreak"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "punti di interruzione, DebugBreak (funzione)"
  - "DebugBreak (funzione)"
  - "debug [C++], DebugBreak (funzione)"
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DebugBreak e __debugbreak
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile chiamare la funzione Win32 DebugBreak o la funzione intrinseca [\_\_debugbreak](/visual-cpp/intrinsics/debugbreak) in qualunque punto del codice.  `DebugBreak` e `__debugbreak` hanno lo spesso effetto dell'impostazione di un punto di interruzione nella stessa posizione.  
  
 Poiché `DebugBreak` è una chiamata a una funzione di sistema, è necessario che siano installati i simboli di debug del sistema per garantire che vengano visualizzate le informazioni corrette sullo stack di chiamate dopo l'interruzione.  In alternativa, le informazioni sullo stack di chiamate visualizzate dal debugger possono essere spostate di un frame.  Se si usa `__debugbreak`, i simboli non sono obbligatori.  
  
## Vedere anche  
 [Intrinseci del compilatore](/visual-cpp/intrinsics/compiler-intrinsics)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)