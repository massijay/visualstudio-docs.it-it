---
title: "Procedura: specificare una versione di .NET Framework per il debug | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - ".NET Framework, specifica della versione per il debug"
  - "debug [Visual Studio], specifica della versione di .NET Framework"
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: specificare una versione di .NET Framework per il debug
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debugger di [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] supporta il debug delle versioni precedenti di Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], oltre che della versione corrente.  Se un'applicazione viene avviata da Visual Studio, il debugger è sempre in grado di identificare la versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] corretta per l'applicazione di cui è in corso il debug.  Se l'applicazione è già in esecuzione e si utilizza **Connetti a**, il debugger potrebbe non essere sempre in grado di identificare una versione precedente di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  In questo caso, verrà visualizzato un messaggio di errore simile al seguente:  
  
 Il debugger ha interpretato erroneamente la versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] che verrà utilizzata dall'applicazione.  
  
 In questi rari casi, è possibile impostare una chiave del Registro di sistema per indicare al debugger quale versione utilizzare.  
  
### Per specificare una versione di .NET Framework per il debug  
  
1.  Cercare nella directory Windows\\Microsoft.NET\\Framework le versioni di .NET Framework installate nel computer.  I numeri di versione saranno simili al seguente:  
  
     `V1.1.4322`  
  
     Identificare il numero di versione corretto e annotarlo.  
  
2.  Avviare l'**Editor del Registro di sistema** \(regedit\).  
  
3.  Nell'**Editor del Registro di sistema** aprire la cartella HKEY\_LOCAL\_MACHINE.  
  
4.  Passare a: HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine\\{449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}  
  
     Se la chiave non esiste, fare clic con il pulsante destro del mouse su HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine e scegliere **Nuova chiave**.  Assegnare alla nuova chiave il nome `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Dalla chiave {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}, cercare la chiave CLRVersionForDebugging nella colonna **Nome**.  
  
    1.  Se la chiave non esiste, fare clic con il pulsante destro del mouse su {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B} e scegliere **Nuovo \- Valore stringa**.  Fare clic con il pulsante destro del mouse sul nuovo valore di stringa e scegliere **Rinomina**, quindi digitare `CLRVersionForDebugging`.  
  
6.  Fare doppio clic su **CLRVersionForDebugging**.  
  
7.  Digitare il numero di versione di .NET Framework nella casella **Valore** della casella **Modifica stringa**.  Ad esempio: V1.1.4322  
  
8.  Scegliere **OK**.  
  
9. Chiudere l'**Editor del Registro di sistema**.  
  
     Se all'avvio del debug viene di nuovo visualizzato un messaggio di errore, verificare di avere immesso il numero di versione corretto nel Registro di sistema.  Verificare inoltre che la versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in uso sia supportata da Visual Studio.  Il debugger è compatibile con la versione di .NET Framework corrente e le versioni precedenti, ma potrebbe non essere compatibile con le versioni future.  
  
## Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)