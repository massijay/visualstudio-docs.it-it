---
title: "Procedura: eseguire il debug del metodo OnStart | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "metodo OnStart"
  - "debug [Visual Studio], servizi Windows"
  - "debug del codice gestito, metodo OnStart"
  - "debug di applicazioni di servizi Windows, metodo OnStart"
  - "servizi Windows, debug di applicazioni"
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: eseguire il debug del metodo OnStart
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile eseguire il debug di un servizio Windows stesso avviando il servizio e connettendo il debugger al processo del servizio. Per altre informazioni, vedere [How to: Debug Windows Service Applications](../Topic/How%20to:%20Debug%20Windows%20Service%20Applications.md). Per eseguire il debug del metodo <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> di un servizio Windows, è tuttavia necessario avviare il debugger all'interno del metodo.  
  
1.  Aggiungere una chiamata a <xref:System.Diagnostics.Debugger.Launch%2A> all'inizio del metodo `OnStart()`.  
  
    ```c#  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Avviare il servizio. È possibile usare `net start` o avviarlo nella finestra **Servizi**.  
  
     Verrà visualizzata una finestra di dialogo analoga alla seguente:  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Selezionare **Sì, esegui il debug di \<nome servizio\>.**  
  
4.  Nella finestra Debugger JIT di Visual Studio selezionare la versione di Visual Studio da usare per il debug.  
  
     ![JustInTimeDebugger](~/debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Viene avviata una nuova istanza di Visual Studio e l'esecuzione viene arrestata in corrispondenza del metodo `Debugger.Launch()`.  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice gestito](../debugger/debugging-managed-code.md)