---
title: "/Upgrade (devenv.exe) | Microsoft Docs"
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
  - "/upgrade (opzione devenv)"
  - "devenv, /upgrade (opzione)"
  - "upgrade (opzione devenv)"
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Consente di aggiornare il file della soluzione e tutti i relativi file di progetto, oppure solo quello specificato, ai formati di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] correnti.  
  
## Sintassi  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## Argomenti  
 `SolutionFile`  
 Obbligatorio se si aggiorna un'intera soluzione e i relativi progetti.  Il percorso e il nome di un file della soluzione.  È possibile immettere solo il nome del file della soluzione oppure il percorso completo e il nome del file della soluzione.  Se non esistono, la cartella o il file specificati verranno creati.  
  
 `ProjectFile`  
 Obbligatorio se si aggiorna un progetto singolo.  Il percorso e il nome del file di progetto nella soluzione.  È possibile immettere solo il nome del file del progetto oppure il percorso completo e il nome del file del progetto.  Se non esistono, la cartella o il file specificati verranno creati.  
  
## Note  
 I backup vengono creati e copiati automaticamente in una directory denominata Backup, creata nella directory corrente.  
  
 Per consentire l'aggiornamento di soluzioni o progetti inclusi nel controllo del codice sorgente è necessario estrarli.  
  
 Se si utilizza l’opzione `/upgrade`, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non viene avviato.  È possibile visualizzare i risultati dell'aggiornamento nel report di aggiornamento relativo al linguaggio di sviluppo della soluzione o del progetto.  Non vengono restituiti messaggi di errore o informazioni sull'utilizzo.  Per ulteriori informazioni sull'aggiornamento di progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vedere [Procedura: Risolvere i problemi relativi agli aggiornamenti di progetti Visual Studio con esito negativo](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## Esempio  
 In questo esempio viene aggiornato un file della soluzione denominato "MyProject.sln" nella cartella predefinita per le soluzioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## Vedere anche  
 [Procedura: Risolvere i problemi relativi agli aggiornamenti di progetti Visual Studio con esito negativo](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)