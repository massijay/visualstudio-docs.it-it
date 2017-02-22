---
title: "/LCID (devenv.exe) | Microsoft Docs"
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
  - "/l (opzione devenv)"
  - "/lcid (opzione devenv)"
  - "devenv, /LCID (opzione)"
  - "impostazioni predefinite di linguaggio"
  - "LCID (opzione devenv)"
  - "ID impostazioni locali"
  - "ID impostazioni locali, impostazione per l'IDE"
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Imposta la lingua predefinita utilizzata per il testo, la valuta e altri valori all'interno dell'ambiente di sviluppo integrato \(IDE\).  
  
## Sintassi  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## Argomenti  
 `LocaleID`  
 Obbligatorio.  L'ID impostazioni locali, o LCID, della lingua specificata.  
  
## Note  
 Carica l'IDE e imposta la lingua predefinita per l'ambiente.  Questa modifica viene mantenuta tra una sessione e l'altra e visualizzata nel riquadro **Impostazioni internazionali** delle opzioni **Ambiente** nella finestra di dialogo **Opzioni** nell'IDE.  
  
 Se il linguaggio specificato non è disponibile nel sistema dell'utente, l'opzione \/LCID viene ignorata.  
  
 Nella tabella seguente vengono elencati gli identificatori locali \(LCID\) dei linguaggi supportati da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Linguaggio|LCID|  
|----------------|----------|  
|Cinese \(semplificato\)|2052|  
|Cinese \(tradizionale\)|1028|  
|Inglese|1033|  
|Francese|1036|  
|Tedesco|1031|  
|Italiano|1040|  
|Giapponese|1041|  
|Coreano|1042|  
|Spagnolo|3082|  
  
## Esempio  
 Questo esempio carica l'IDE con stringhe di risorse in lingua inglese.  
  
```  
devenv /LCID 1033  
```  
  
## Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Personalizzazione del layout della finestra](../../ide/customizing-window-layouts-in-visual-studio.md)