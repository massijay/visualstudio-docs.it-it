---
title: "Procedura: esaminare il codice di sistema dopo un&#39;eccezione | Microsoft Docs"
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
  - "debug, eccezioni"
  - "eccezioni, debug"
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: esaminare il codice di sistema dopo un&#39;eccezione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si verifica un'eccezione, potrebbe essere necessario esaminare il codice di una chiamata al sistema per determinare la causa dell'eccezione.  Nella procedura riportata di seguito viene illustrato come determinare la causa se non sono disponibili simboli caricati per il codice di sistema o se Just My Code è attivato.  
  
### Per esaminare il codice di sistema dopo un'eccezione  
  
1.  Fare clic con il pulsante destro del mouse sulla finestra **Stack di chiamate** e scegliere **Mostra codice esterno**.  
  
     Se Just My Code non è attivato, questa opzione non è disponibile nel menu di scelta rapida e il codice di sistema viene visualizzato per impostazione predefinita.  
  
2.  Fare clic con il pulsante destro del mouse sui frame di codice esterni presenti nella finestra **Stack di chiamate**.  
  
3.  Scegliere **Carica simboli da**, quindi fare clic su **Server dei simboli Microsoft**.  
  
    1.  Se Just My Code è attivato, viene visualizzata una finestra di dialogo  indicante che Just My Code è stato disabilitato.  Tale operazione è necessaria per eseguire le chiamate di sistema.  
  
    2.  Viene visualizzata la finestra di dialogo **Download dei simboli pubblici**.  La finestra viene chiusa al termine del download.  
  
4.  È possibile ora esaminare il codice di sistema nella finestra **Stack di chiamate** e in altre finestre.  Ad esempio, è possibile fare doppio clic su un frame dello stack di chiamate per visualizzare il codice nella finestra **Disassembly** o nella finestra origine.  
  
## Vedere anche  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)