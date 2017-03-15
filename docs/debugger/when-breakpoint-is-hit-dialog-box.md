---
title: "Finestra di dialogo Quando il punto di interruzione viene raggiunto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.whenbreakpointishit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Finestra di dialogo Quando il punto di interruzione viene raggiunto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo consente di personalizzare l'azione che si verifica quando viene raggiunto un punto di interruzione.  
  
## Elenco UIElement  
 **Stampa un messaggio**  
 Stampa un messaggio utilizzando la sintassi DebuggerDisplay.  Per ulteriori informazioni, vedere [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 In questa casella di testo sono consentiti anche caratteri speciali, ad esempio $ADDRESS, che possono essere utilizzati da soli o tra le parentesi graffe di un'espressione DebuggerDisplay.  Nella finestra di dialogo sono elencate le parole chiave disponibili.  
  
 **Continua esecuzione**  
 Questo controllo è attivato solo quando è selezionata l'opzione **Stampa un messaggio**.  Con questo controllo attivato, è possibile utilizzare un punto di interruzione come punto di traccia per tracciare l'esecuzione del programma anziché interromperla quando viene raggiunto tale punto.  
  
## Vedere anche  
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)   
 [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)