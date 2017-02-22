---
title: "Come &#232; possibile accedere ai codici di errore di Win32? | Microsoft Docs"
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
  - "vc.errors"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "codici di errore, Win32"
  - "Win32, codici di errore"
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Come &#232; possibile accedere ai codici di errore di Win32?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il file WINERROR.H nella directory INCLUDE della directory di installazione di sistema predefinita contiene le definizioni dei codici di errore per le funzioni API Win32.  
  
 È possibile cercare un codice di errore digitando tale codice nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**.  Di seguito è riportato un esempio:  
  
```  
0x80000004,hr  
```  
  
## Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)