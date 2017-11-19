---
title: 'Errore: ASP.NET non installato | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec590a018e102e6ab3dd8d2607d9720991e9f90
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="error-aspnet-not-installed"></a>Errore: ASP.NET non è installato
Questo errore si verifica quando [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è installato correttamente nel computer di cui si sta tentando di eseguire il debug. Questo errore potrebbe essere dovuto al fatto che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è mai stato installato o che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è stato installato prima di IIS.  
  
### <a name="to-reinstall-aspnet"></a>Per reinstallare ASP.NET  
  
1.  Da una finestra del prompt dei comandi eseguire il comando seguente:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     dove *versione* rappresenta il numero di versione di .NET Framework installata nel computer in uso, ad esempio v 1.0.370. È possibile determinare la versione di framework esaminando il `\WINDOWS\Microsoft.NET\Framework` directory.  
  
    > [!NOTE]
    >  Con Windows Server 2003, è possibile installare [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] utilizzando **Aggiungi / Rimuovi programmi** nel Pannello di controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)