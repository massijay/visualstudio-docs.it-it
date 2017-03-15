---
title: "Procedura: tornare alla funzione che ha chiamato MFC se interrotta | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.mfc"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Interrompi (comando)"
  - "debug [MFC], funzioni"
  - "debug [MFC], ritorno alla funzione chiamante"
  - "chiamate di funzione, ritorno alla funzione chiamante"
  - "funzioni [C++], debug"
  - "funzioni [debugger]"
  - "programmi, interruzione"
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Procedura: tornare alla funzione che ha chiamato MFC se interrotta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere Importa\/Esporta impostazioni dal menu Strumenti.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se è stato utilizzato il comando **Interrompi** del menu **Debug** per interrompere il programma ma la chiamata di MFC è stata comunque eseguita, è possibile utilizzare la finestra Stack di chiamate per tornare alla funzione, dopo aver verificato che il problema dipende dal codice.  Per ulteriori informazioni, vedere [Procedura: utilizzare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).  
  
 Talvolta è possibile che il codice si interrompa nel message pump.  In questo caso, non è disponibile codice utente nello stack di chiamate.  Per evitare questo problema, utilizzare i punti di interruzione \(se possibile con condizioni e conteggi dei passaggi\) anziché il comando **Interrompi**.  Per ulteriori informazioni, vedere [Breakpoints and Tracepoints](http://msdn.microsoft.com/it-it/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### Per tornare alla funzione da cui è stata eseguita la chiamata di MFC  
  
-   Utilizzare la finestra **Stack di chiamate**.  
  
## Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)