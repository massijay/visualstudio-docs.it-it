---
title: "Creazione di un motore di Debug personalizzato | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motori di debug, implementazione"
  - "motori di debug, personalizzato"
  - "debug [debug SDK], motori di debug personalizzati"
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Creazione di un motore di Debug personalizzato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il modulo \(DE\) di debug è un componente che consente di eseguire il debug di architetture di runtime particolari.  Esiste in genere un solo DE implementation per ambiente di runtime.  
  
> [!NOTE]
>  Mentre è DE implementations separato per Transact\-SQL e JScript, VBScript o JScript condividono un singolo DE.  
  
 Funzionamento Di un DE all'interprete o il sistema operativo per fornire a tali servizi di debug quali il controllo di esecuzione, i punti di interruzione e la valutazione delle espressioni.  Questi servizi sono distribuiti tra il DE interfaces e possono causare il debugger per la transizione tra le modalità operative diversi.  Per ulteriori informazioni, vedere [Modalità operative](../../extensibility/debugger/operational-modes.md).  
  
 Creare un DE effettuando le operazioni seguenti:  
  
1.  registrare un DE con Visual Studio  
  
2.  Impostazione di un programma da sottoporre a debug  
  
3.  Controllo dell'esecuzione e valutazione dello stato  
  
4.  L'invio di eventi  
  
5.  chiusura e rimuovere  
  
## In questa sezione  
 [Registrazione di un motore di Debug personalizzato](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Vengono illustrati i passaggi necessari per registrare il modulo di debug con Visual Studio in modo da poterlo utilizzare.  
  
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Viene fornita la prima che il DE possibile eseguire il debug di un programma, è innanzitutto necessario avviare il DE o associarlo a un programma esistente.  
  
 [Controllo dell'esecuzione e la valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Viene illustrato perché il debug di un'applicazione richiede implementare le funzionalità del controllo di esecuzione.  
  
 [L'invio di eventi](../../extensibility/debugger/sending-events.md)  
 Viene descritta la comunicazione tra il debugger e il DE come modello eventi basato su DCOM.  
  
 [Chiusura e disconnessione](../../extensibility/debugger/termination-and-detaching.md)  
 Viene illustrato come ottenere la terminazione normale, ovvero non sono presenti punti di interruzione, eccezioni, errori di runtime, o cicli infiniti nell'applicazione di cui eseguire il debug.  
  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)  
 Viene descritto l'ordine degli eventi che si verificano in una sessione di debug.  
  
 [Procedura: Eseguire il Debug di un motore di Debug personalizzato](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Viene descritto come eseguire il debug di un oggetto personalizzato DE.  
  
## Vedere anche  
 [Estensibilità del Debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)