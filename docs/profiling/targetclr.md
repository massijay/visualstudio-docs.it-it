---
title: "TargetCLR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# TargetCLR
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **TargetCLR** specifica la versione di Common Language Runtime \(CLR\) di cui eseguire il profilo quando in un'applicazione sono state caricate più versioni di CLR.  
  
 Per impostazione predefinita, gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizzano la prima versione di CLR caricata dall'applicazione.  
  
## Sintassi  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### Parametri  
 `ClrVersion`  
 Numero di versione di CLR.  Utilizzare il formato di versione **vN.N.NNNNN**.  
  
## Opzioni obbligatorie  
 L'opzione **TargetCLR** può essere utilizzata solo con le opzioni **Launch** o **Attach** .  
  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e l'esecuzione del profilo.  
  
 **Attach:** `PID`  
 Avvia l'esecuzione del profilo per il processo specificato.  
  
## Esempio  
 In questo esempio, l'opzione TargetCLR viene utilizzata per assicurarsi che venga eseguito il profilo della versione di CLR 4.0.11003.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```