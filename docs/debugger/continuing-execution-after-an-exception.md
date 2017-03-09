---
title: "Continuazione dell&#39;esecuzione dopo un&#39;eccezione | Microsoft Docs"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, eccezioni"
  - "gestione eccezioni, continuazione dell'esecuzione"
  - "Eccezioni (finestra di dialogo)"
  - "eccezioni, continuazione dell'esecuzione"
  - "esecuzione, continuazione dopo un'eccezione"
  - "codice gestito, gestione eccezioni"
  - "eccezioni gestite, continuazione dell'esecuzione"
  - "esecuzione di programmi"
  - "programmi, esecuzione"
  - "threading [Visual Studio], continuazione dell'esecuzione dopo le eccezioni"
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Continuazione dell&#39;esecuzione dopo un&#39;eccezione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando l'esecuzione viene interrotta dal debugger a causa di un'eccezione, viene visualizzata una finestra di dialogo.  Per impostazione predefinita, per Visual Basic o C\# viene visualizzata la finestra di dialogo [Exception Assistant](../Topic/Exception%20Assistant.md).  Per C\+\+, viene visualizzata la finestra di dialogo **Eccezione** precedente.  Se si utilizza Visual Basic o C\#, ma l'opzione **Informazioni sulle eccezioni** è stata disabilitata nella finestra di dialogo **Opzioni**, viene visualizzata la finestra di dialogo **Eccezione**.  
  
 Quando viene visualizzata la finestra di dialogo **Informazioni sulle eccezioni** o **Eccezione**, è possibile tentare di risolvere il problema che ha provocato l'eccezione.  
  
## Codice gestito  
 Nel codice gestito, è possibile continuare l'esecuzione nello stesso thread dopo un'eccezione non gestita.  La funzionalità **Informazioni sulle eccezioni** rimuove lo stack di chiamate fino al punto in cui è stata generata l'eccezione.  
  
## Codice nativo  
 In C\/C\+\+ nativo, sono disponibili due opzioni:  
  
-   È possibile fare clic su **Interrompi** e tentare di risolvere il problema.  Nella modalità di interruzione, è possibile rimuovere lo stack di chiamate facendo clic con il pulsante destro del mouse su un frame nella finestra **Stack di chiamate** e selezionando **Rimuovi fino a questo frame** dal menu di scelta rapida.  Quando si continua il debug, se il problema non è stato risolto, verrà nuovamente visualizzata la finestra di dialogo **Eccezione**.  In caso contrario, la finestra di dialogo **Eccezione** non verrà più visualizzata.  
  
-   È possibile fare clic su **Continua** per continuare l'esecuzione senza tentare di risolvere il problema.  In tal caso, verrà nuovamente visualizzata la finestra di dialogo **Eccezione**.  
  
## Codice misto  
 Se si rileva un'eccezione non gestita durante il debug di codice misto nativo e gestito, i vincoli del sistema operativo impediscono la rimozione dello stack di chiamate.  Se si tenta di rimuovere lo stack di chiamate utilizzando il menu di scelta rapida, un messaggio di errore indica che il debugger non può eseguire la rimozione da un'eccezione non gestita durante il debug di codice misto.  
  
## Vedere anche  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)