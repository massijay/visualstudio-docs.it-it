---
title: "/ResetSettings (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/ResetSettings (opzione devenv)"
  - "devenv, /ResetSettings (opzione)"
  - "ResetSettings (opzione)"
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ripristina le impostazioni predefinite di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e avvia automaticamente l'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Eventualmente, consente di ripristinare le impostazioni in un file .vssettings specificato.  
  
 Le impostazioni predefinite sono determinate dal profilo selezionato quando è stato avviato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Sintassi  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## Argomenti  
 `SettingsFile`  
 Il percorso completo e il nome del file con estensione vssettings da applicare a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Per ripristinare il profilo Impostazioni generali per lo sviluppo, utilizzare `General`.  
  
## Note  
 Se non viene specificato `SettingsFile`, al successivo avvio di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verrà richiesto di selezionare una raccolta predefinita di impostazioni.  
  
## Esempio  
 La seguente linea di comando può essere applicata alle impostazioni memorizzate nel file `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## Vedere anche  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)