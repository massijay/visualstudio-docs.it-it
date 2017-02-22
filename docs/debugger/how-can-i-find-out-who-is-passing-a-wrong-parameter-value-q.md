---
title: "Come &#232; possibile individuare chi passa un valore di parametro errato? | Microsoft Docs"
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
  - "vs.debug.parameters"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "debug [C++], parametri"
  - "funzioni [debugger], rilevamento di valori di parametri errati"
  - "valori di parametro, risoluzione dei problemi"
  - "parametri [debugger]"
  - "passaggio di parametri, risoluzione dei problemi di valori errati"
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Come &#232; possibile individuare chi passa un valore di parametro errato?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrizione del problema  
 Il valore di parametro errato è stato passato a una delle funzioni utilizzate.  Questa funzione viene chiamata da numerosissime posizioni.  Come è possibile capire quale elemento passa il valore errato?  
  
## Soluzione  
  
#### Per risolvere questo problema  
  
1.  Impostare un punto di interruzione del percorso all'inizio della funzione.  
  
2.  Fare clic con il pulsante destro del mouse sul punto di interruzione e scegliere **Condizione**.  
  
3.  Nella finestra di dialogo **Condizione punto di interruzione** selezionare la casella di controllo **Condizione**.  Vedere [Punti di interruzione avanzati](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Nella casella di testo immettere un'espressione, ad esempio `Var==3`, in cui `Var` è il nome del parametro che contiene il valore errato e `3` il valore errato passato.  
  
5.  Selezionare il pulsante di opzione **è true**, quindi scegliere **OK**.  
  
6.  Eseguire nuovamente il programma.  Il punto di interruzione causa l'arresto del programma all'inizio della funzione, quando il parametro `Var` ha valore `3`.  
  
7.  Utilizzare la finestra Stack di chiamate per individuare la funzione chiamante e passare al relativo codice sorgente.  Per ulteriori informazioni, vedere [Procedura: utilizzare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).  
  
## Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Breakpoints](http://msdn.microsoft.com/it-it/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)