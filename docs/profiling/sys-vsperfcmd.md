---
title: "Sys (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Sys** di VSPerfCmd.exe consente di impostare l'evento di profilo campionato negli eventi chiamata di sistema \(chiamate di funzione dall'applicazione profilata al sistema operativo\) e facoltativamente di modificare il numero predefinito, 10, di chiamate di sistema in un intervallo di campionamento.  
  
 L'opzione **Sys** può essere utilizzata unicamente in una riga di comando che contiene anche l'opzione **Launch** o **Attach**.  
  
 Per impostazione predefinita, l'evento di campionamento del profiler è impostato sui cicli di clock del processore e l'intervallo di campionamento è impostato su 10.000.000.  Le opzioni **Timer**, **PF**, **Sys** e **Counter** consentono di impostare l'evento e l'intervallo di campionamento.  L'opzione **GC** consente di raccogliere i dati di memoria .NET a ogni evento di allocazione e Garbage Collection.  In una riga di comando è possibile specificare una sola di queste opzioni.  
  
 È possibile impostare l'evento e l'intervallo di campionamento solo nella prima riga di comando che contiene un'opzione **Launch** o **Attach**.  
  
## Sintassi  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### Parametri  
 `Events`  
 Integer che specifica il numero di eventi chiamata di sistema in un intervallo di campionamento.  Se `Events` non viene specificato, l'intervallo è impostato su 10.  
  
## Opzioni obbligatorie  
 **Sys** richiede una delle opzioni seguenti.  
  
 **Launch:** `AppName`  
 Avvia il profiler e l'applicazione specificata da `AppName`.  
  
 **Attach:** `PID`  
 Connette il profiler al processo specificato dal `PID`.  
  
## Opzioni non valide  
 Le opzioni seguenti non possono essere specificate nella stessa riga di comando di **Sys**.  
  
 **PF**\[**:**`Events`\]  
 Imposta l'evento di campionamento sugli errori di pagina e imposta facoltativamente l'intervallo di campionamento su `Events`.  L'intervallo PF predefinito è 10.  
  
 **Timer**\[**:**`Cycles`\]  
 Imposta l'evento di campionamento sui cicli di clock del processore e imposta facoltativamente l'intervallo di campionamento su `Cycles`.  L'intervallo Timer predefinito è 10.000.000.  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 Imposta l'evento di campionamento sul contatore delle prestazioni della CPU specificato da `Name` e l'intervallo di campionamento su `Reload`.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Raccoglie i dati di memoria .NET.  Per impostazione predefinita \(**Allocation**\), i dati vengono raccolti a ogni evento di allocazione della memoria.  Quando viene specificato il parametro **Lifetime**, i dati vengono raccolti anche a ogni evento di Garbage Collection.  
  
## Esempio  
 In questo esempio viene illustrato come impostare l'evento di campionamento del profiler sulle chiamate di sistema e l'intervallo di campionamento su 20 chiamate per campione.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)