---
title: "PF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# PF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **PF** di VSPerfCmd.exe imposta l'evento di profilo campionato sugli errori di pagina e facoltativamente modifica il numero predefinito di errori di pagina in un intervallo di campionamento pari a 10.  
  
> [!NOTE]
>  Non è possibile utilizzare PF in sistemi a 64 bit.  
  
 **Nota**  
 **PF** non è supportato in computer a 64 bit.**PF** può essere utilizzato solo in una riga di comando che contiene anche l'opzione **Launch** o **Attach**.  
  
 Per impostazione predefinita, l'evento di campionamento è impostato sui cicli di clock del processore non interrotti e l'intervallo di campionamento è impostato su 10.000.000.  Le opzioni **Timer**, **PF**, **Sys** e **Counter** consentono di impostare l'evento e l'intervallo di campionamento.  L'opzione **GC** consente di raccogliere i dati di memoria .NET a ogni evento di allocazione e Garbage Collection.  In una riga di comando è possibile specificare una sola di queste opzioni.  
  
 È possibile impostare l'evento e l'intervallo di campionamento solo nella prima riga di comando che contiene un'opzione **Launch** o **Attach**.  
  
## Sintassi  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### Parametri  
 `Events`  
 Valore intero che specifica il numero di eventi errore di pagina in un intervallo di campionamento.  Se `Events` non viene specificato, l'intervallo è impostato su 10.  
  
## Opzioni obbligatorie  
 È possibile specificare l'opzione **PF** solo in una riga di comando che contiene una delle opzioni seguenti.  
  
 **Launch:** `AppName`  
 Avvia il profiler e l'applicazione specificata da AppName.  
  
 **Attach:** `PID`  
 Connette il profiler al processo specificato da AppName.  
  
## Opzioni non valide  
 Le opzioni seguenti non possono essere specificate nella stessa riga di comando di **PF**.  
  
 **Timer**\[**:**`Cycles`\]  
 Imposta l'evento di campionamento sui cicli di clock del processore e imposta facoltativamente l'intervallo di campionamento su `Cycles`.  L'intervallo Timer predefinito è 10.000.000.  
  
 **Sys**\[**:**`Events`\]  
 Imposta l'evento di campionamento sulle chiamate dall'applicazione profilata al kernel del sistema operativo \(syscall\) e facoltativamente imposta l'intervallo di campionamento su `Events`.  L'intervallo Sys predefinito è 10.  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 Imposta l'evento di campionamento sul contatore delle prestazioni della CPU specificato da `Name` e l'intervallo di campionamento su `Reload`.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Raccoglie i dati di memoria .NET.  Per impostazione predefinita \(**Allocation**\), i dati vengono raccolti a ogni evento di allocazione della memoria.  Quando viene specificato il parametro **Lifetime**, i dati vengono raccolti anche a ogni evento di Garbage Collection.  
  
## Esempio  
 In questo esempio viene illustrato come impostare l'evento di campionamento del profilo sugli errori di pagina e l'intervallo di campionamento su 20 errori di pagina.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)