---
title: Applicazioni Server SDI | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 089eeada5f3d9d392aff7768ed3f5b813ef8f772
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="sdi-server-applications"></a>Applicazioni server SDI
Se si esegue il debug di un'applicazione server SDI, è necessario specificare `/Embedding` o `/Automation` nel **argomenti della riga di comando** proprietà il *progetto* la finestra di dialogo Pagine delle proprietà per C/C++, c#, o Progetti di Visual Basic.  
  
 Grazie a questi argomenti della riga di comando, il debugger è in grado di avviare l'applicazione server come se tale avvio venisse eseguito da un contenitore. In seguito all'avvio del contenitore da Program Manager o File Manager, il contenitore utilizzerà l'istanza del server già avviata dal debugger.  
  
## <a name="finding-the-command-line-arguments-property"></a>Ricerca della proprietà Argomenti della riga di comando  
 Per l'accesso di *progetto* mouse sul progetto in Esplora soluzioni, finestra di dialogo Pagine delle proprietà e quindi scegliere Proprietà dal menu di scelta rapida. Per individuare la proprietà Argomenti della riga di comando, espandere la categoria Proprietà di configurazione e fare clic sulla pagina Debug.  
  
## <a name="see-also"></a>Vedere anche  
 [COM e ActiveX di debug](../debugger/com-and-activex-debugging.md)   
 [Procedura: Eseguire il debug di server COM](../debugger/how-to-debug-com-servers.md)