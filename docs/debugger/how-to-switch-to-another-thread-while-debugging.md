---
title: "Procedura: passare a un altro thread durante il debug | Microsoft Docs"
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
  - "thread, passaggio [debug]"
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: passare a un altro thread durante il debug
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si esegue il debug di un'applicazione multithreading, è possibile utilizzare diversi metodi per cambiare contesto passando dal thread utilizzato a un altro thread.  
  
### Per passare a un thread visualizzato nella finestra Thread  
  
-   Fare doppio clic sul thread.  
  
### Per passare a un thread in una finestra di origine  
  
-   Nella barra sinistra fare clic con il pulsante destro del mouse su un indicatore del thread, scegliere **Passa a**, quindi fare clic sul nome del thread al quale si desidera passare.  Nel menu di scelta rapida vengono visualizzati solo i thread presenti in quella determinata posizione.  
  
     Se non viene visualizzato alcun indicatore, fare clic con il pulsante destro del mouse nella finestra **Thread** e verificare che **Mostra thread nell'origine** sia selezionato.  
  
### Per passare a un thread nella barra degli strumenti Posizione di debug  
  
1.  Nella barra degli strumenti **Posizione di debug** fare clic sulla casella **Thread**.  
  
2.  Nell'elenco, fare clic sul thread al quale si desidera passare.  
  
## Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)