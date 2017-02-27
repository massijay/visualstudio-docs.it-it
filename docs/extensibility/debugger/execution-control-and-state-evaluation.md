---
title: "Controllo dell&#39;esecuzione e la valutazione dello stato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], il controllo dell'esecuzione"
  - "valutazione dell'espressione, controllo di esecuzione"
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Controllo dell&#39;esecuzione e la valutazione dello stato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Debug di un'applicazione, è necessario implementare tali funzionalità di controllo di esecuzione come l'esecuzione di funzioni, interruzione in corrispondenza di punti di interruzione e continuare l'esecuzione. Debug di base di Visual Studio relativo controllo di esecuzione per gli eventi inviati tra i componenti del debugger.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Controllo del programma](../../extensibility/debugger/program-control.md)  
 Elenca le routine seguenti che si verificano a livello di programma: impostazione dell'istruzione successiva, l'esecuzione, l'esecuzione di istruzioni, continuare, la sospensione e ripresa.  
  
 [Metodi correlati al punto di interruzione](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definisce il limite e in sospeso di tipi di punti di interruzione supportati da Visual Studio.  
  
 [Valutazione dello Stack di chiamate](../../extensibility/debugger/call-stack-evaluation.md)  
 Viene illustrata l'implementazione dei metodi che consentono la visualizzazione degli stack frame dello stack di chiamate durante la modalità di interruzione.  
  
 [Valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Viene illustrato il motore di debug (DE), valutazione (EE) e sessione di debug di gestione delle espressioni sono che riguardano l'analisi e valutazione di un'espressione immessi in una delle finestre dell'IDE.  
  
 [Eventi di controllo](../../extensibility/debugger/control-events.md)  
 Descrive l'interfaccia utilizzata per inviare eventi durante l'esecuzione del programma controllato.