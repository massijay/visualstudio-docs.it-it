---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c4f65035e1030406ced4c5f0c98ebd1d1e66c5d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
Ripristina le impostazioni predefinite di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e avvia automaticamente l'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Facoltativamente, reimposta le impostazioni in un file con estensione vssettings specificato.  
  
 Le impostazioni predefinite sono determinate dal profilo selezionato quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è stato avviato per la prima volta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Argomenti  
 `SettingsFile`  
 Il percorso completo e il nome del file con estensione vssettings da applicare a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Per ripristinare il profilo Impostazioni generali per lo sviluppo, usare `General`.  
  
## <a name="remarks"></a>Note  
 Se non viene specificato `SettingsFile`, al successivo avvio di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verrà richiesto di selezionare una raccolta predefinita di impostazioni.  
  
## <a name="example"></a>Esempio  
 La riga di comando seguente applica le impostazioni memorizzate nel file `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)