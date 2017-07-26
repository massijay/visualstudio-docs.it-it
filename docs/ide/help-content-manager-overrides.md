---
title: Ovverride di Gestione contenuto della Guida | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: c4889d40e9ca53cccf7de384e609eb959d8981f5
ms.contentlocale: it-it
ms.lasthandoff: 05/13/2017

---
# <a name="help-content-manager-overrides"></a>Ovverride di Gestione contenuto della Guida
È possibile modificare il Registro di sistema per modificare il comportamento predefinito del visualizzatore della Guida e le funzionalità correlate alla Guida nell'IDE di Visual Studio.  
  
|Attività|Chiave del Registro di sistema|Valore e definizione|  
|----------|------------------|--------------------------|  
|Definire l'endpoint di servizio univoco|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*.|  
|Definire l'impostazione predefinita online/offline|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp--Immettere `0` per specificare la Guida locale e `1` per specificare la Guida online.|  
|Definire l'endpoint univoco F1|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|Eseguire l'override della priorità del processo BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (nei computer a 64 bit)\Microsoft\Help\v2.2|BITSPriority--Usare uno dei valori seguenti: **foreground**, **high**, **normal** o **low**.|  
|Disabilitare la guida online (e l'opzione online dell'IDE)|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (nei computer a 64 bit)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled--Impostare su 1 per disabilitare l'accesso al contenuto della Guida online.|  
|Disabilitare la gestione del contenuto|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (nei computer a 64 bit)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled--Impostare su 1 per disabilitare la scheda **Gestisci contenuto** in Help Viewer.|  
|Puntare all'archivio del contenuto locale nella condivisione di rete|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath="*ContentStoreNetworkShare*"|  
|Disabilitare l'installazione del contenuto al primo avvio della funzionalità di Visual Studio.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (nei computer a 64 bit)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection--Impostare su 1 per disabilitare le funzionalità della guida configurate la prima volta che si esegue Visual Studio.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida dell'amministratore di Help Viewer](../ide/help-viewer-administrator-guide.md)
