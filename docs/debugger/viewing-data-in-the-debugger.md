---
title: "Visualizzazione di dati nel debugger | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
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
  - "debugger, visualizzazione di dati"
  - "debug [Visual Studio], controllo di programmi"
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# Visualizzazione di dati nel debugger
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nel debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è disponibile una serie di strumenti che consentono di analizzare e modificare lo stato del programma. La maggior parte di questi strumenti è utilizzabile solo in modalità di interruzione.  
  
## DataTips  
 Suggerimenti dati è uno degli strumenti più utili per la visualizzazione di informazioni su variabili e oggetti nel programma durante il debug. Quando il debugger si trova in modalità di interruzione, è possibile visualizzare il valore di una variabile appartenente all'ambito corrente posizionando il puntatore del mouse sulla variabile all'interno di una finestra di origine. Per altre informazioni, vedere [Visualizzare i valori di dati nei suggerimenti dati](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).  
  
## Visualizzatori  
 I visualizzatori rappresentano un nuovo componente del debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che consentono di visualizzare in modo significativo il contenuto di un oggetto o di una variabile. È ad esempio possibile usare il visualizzatore HTML per visualizzare una stringa HTML come verrebbe interpretata e visualizzata in un browser. I visualizzatori sono accessibili dai suggerimenti dati, dalla finestra di dialogo **Controllo immediato** e dalle finestre **Espressioni di controllo**, **Auto** e **Variabili locali**. Per altre informazioni, vedere [Visualizzatori](../debugger/create-custom-visualizers-of-data.md).  
  
## Vedere anche  
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Finestra di comando](../ide/reference/command-window.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)