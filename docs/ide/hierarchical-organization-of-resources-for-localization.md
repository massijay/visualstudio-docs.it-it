---
title: Organizzazione gerarchica di risorse per la localizzazione | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f52d57d45c0f78a5bd64b16f10c9bb7c2256cd7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Organizzazione gerarchica di risorse per la localizzazione
In Visual Studio, le risorse localizzate (dati come stringhe e immagini specifiche di ogni impostazione cultura) vengono archiviate in file separati e caricate in base alle impostazioni cultura dell'interfaccia utente. Per comprendere come vengono caricate le risorse localizzate, è utile pensarle come organizzate in modo gerarchico.  
  
## <a name="kinds-of-resources-in-the-hierarchy"></a>Tipi di risorse nella gerarchia  
  
-   Nella parte superiore della gerarchia si trovano le risorse di fallback per le impostazioni cultura predefinite, ad esempio inglese ("en"). Queste sono le uniche risorse che non dispongono di un proprio file. Vengono archiviate nell'assembly principale.  
  
-   Sotto le risorse di fallback si trovano le risorse per le impostazioni cultura non associate ad alcun paese. Alcune impostazioni cultura non associate ad alcun paese sono associate a una lingua, ma non a un paese/regione. Ad esempio, "fr" per il francese rappresenta impostazioni cultura non associate ad alcun paese. Si noi che le risorse di fallback sono disponibili anche per le impostazioni cultura non associate ad alcun paese e per uno in particolare.  
  
-   Sotto a queste risorse si trovano quelle per le impostazioni cultura specifiche. Un'impostazione cultura specifica è associata a una lingua e a un paese/regione. Ad esempio, il francese canadese ("fr-CA") è un'impostazione cultura specifica.  
  
 Se un'applicazione tenta di caricare una risorsa localizzata, ad esempio una stringa, e non la trova, dovrà risalire la gerarchia finché trova un file di risorse contenente la risorsa richiesta.  
  
 Il modo migliore per memorizzare le risorse consiste nel renderle il più generali possibile. Pertanto, quando possibile, è opportuno memorizzare stringhe, immagini e altre risorse localizzate nei file di risorse per le impostazioni cultura non associate ad alcun paese anziché in quelli per le impostazioni cultura specifiche. Ad esempio, se si dispone di risorse per le impostazioni cultura del francese belga ("fr-BE") e le risorse immediatamente sopra sono le risorse di fallback in inglese, può verificarsi un problema quando si tenta di usare l'applicazione su un sistema configurato per le impostazioni cultura del francese canadese. Il sistema cercherà un assembly satellite "fr-CA", non lo troverà e caricherà l'assembly principale che contiene la risorsa di fallback, ovvero l'inglese, invece di caricare le risorse per il francese. L'immagine seguente illustra questo spiacevole scenario.  
  
 ![Solo risorse specifiche](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")  
  
 Se si segue la procedura consigliata di inserimento di più risorse possibili in un file di risorse con impostazioni cultura non associate ad alcun paese per le impostazioni cultura "fr", l'utente francese canadese non visualizzerà le risorse contrassegnate per le impostazioni cultura "fr-BE", ma visualizzerà le stringhe in francese. L'immagine seguente illustra questo scenario più favorevole.  
  
 ![Elemento grafico NeutralSpecificResources](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")  
  
## <a name="see-also"></a>Vedere anche  
 [Linguaggi di risorse non associate ad alcun paese per la localizzazione](../ide/neutral-resources-languages-for-localization.md)   
 [Sicurezza e assembly satellite localizzati](../ide/security-and-localized-satellite-assemblies.md)   
 [Applicazioni localizzate](../ide/localizing-applications.md)   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)   
 [How to: Set the Culture and UI Culture for Windows Forms Globalization](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)  (Procedura: Impostare le impostazioni cultura e le impostazioni cultura dell'interfaccia utente per la globalizzazione di Windows Forms)  
 [Procedura: Impostare le impostazioni cultura e le impostazioni cultura dell'interfaccia utente per la globalizzazione della pagina Web ASP.NET](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0)