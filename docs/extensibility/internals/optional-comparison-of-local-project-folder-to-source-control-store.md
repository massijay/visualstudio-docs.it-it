---
title: Confrontare la cartella di progetto per l&quot;archivio del controllo origine | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: b2ed6955e5ba6fa334cc89a0c2ea8a3d4248f362
ms.lasthandoff: 02/22/2017

---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Confronto facoltativo della cartella di progetto locale all'archivio di controllo di origine
In origine 1.2 API Plug-nel confronto tra la cartella del progetto locale e controllo del codice sorgente viene eseguito utilizzando le funzioni di controllo [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 All'interno di **Esplora**, se si seleziona una cartella anziché un singolo file, il **confrontare versioni** richiama il nuovo menu di scelta rapida [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md) il plug-in del controllo del codice sorgente.  
  
## <a name="new-capability-flags"></a>Nuovo flag di capacità  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nuove funzioni  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 Il `SccDirQueryInfo` funzione viene chiamata prima `SccDirDiff` per determinare se la directory di lavoro è controllato dal codice sorgente. Il `SccDirDiff` funzione consente di visualizzare le differenze tra la directory corrente e la corrispondente cartella del codice sorgente. Questo comando richiede il controllo del codice sorgente del plug-in per visualizzare l'elenco delle modifiche alla directory. Un plug-in del controllo del codice sorgente fornisce la propria interfaccia utente per visualizzare le differenze.  
  
> [!NOTE]
>  Questa funzione utilizza gli stessi flag di comando come [SccDiff](../../extensibility/sccdiff-function.md). Come provider di plug-in controllo codice sorgente, è possibile scegliere di non supportare l'operazione "diff veloce" per le directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità di origine controllo plug-in API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
