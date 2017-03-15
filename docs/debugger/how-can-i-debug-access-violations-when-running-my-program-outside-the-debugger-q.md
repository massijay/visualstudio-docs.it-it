---
title: "Come &#232; possibile eseguire il debug di violazioni di accesso quando si esegue un programma fuori dal debugger? | Microsoft Docs"
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
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "violazione di accesso (debug)"
  - "debug [Visual Studio], violazioni di accesso"
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Come &#232; possibile eseguire il debug di violazioni di accesso quando si esegue un programma fuori dal debugger?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrizione del problema  
 Il programma viene eseguito correttamente nell'ambiente di Visual Studio, ma quando viene eseguito autonomamente con il sistema operativo Windows, genera una violazione di accesso.  Come è possibile effettuare il debug di questo problema?  
  
## Soluzione  
 Impostare l'opzione di [debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md) ed eseguire il programma autonomamente finché non si verifica la violazione di accesso.  Nella finestra di dialogo **Violazione di accesso** sarà quindi possibile fare clic su **Annulla** per avviare il debugger.  
  
 Vedere inoltre l'articolo Q133174 di Knowledge Base "How to Locate Where a General Protection \(GP\) Fault Occurs". Gli articoli della Knowledge Base sono disponibili nel CD di MSDN Library o all'indirizzo [http:\/\/support.microsoft.com\/](http://support.microsoft.com/).  
  
## Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)