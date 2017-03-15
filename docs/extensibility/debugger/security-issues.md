---
title: Problemi di sicurezza | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 12
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
ms.sourcegitcommit: 98a4c85118fc836e1f8922a24700036c9d4837cb
ms.openlocfilehash: fcc65d94f8348674110db6cc0a87e0e3020a4683
ms.lasthandoff: 02/22/2017

---
# <a name="security-issues"></a>Problemi relativi alla sicurezza
Per eseguire il debug di un programma in Visual Studio, solo le autorizzazioni necessite sono gli stessi necessari per eseguire il programma. Ciò include il debug remoto per la maggior parte delle situazioni (alcune situazioni che coinvolgono altri servizi, ad esempio Internet Information Service, potrebbe essere necessario un livello superiore di autorizzazioni).  
  
 Mentre è in esecuzione Visual Studio, il gestore di debug di processi (PDM) tiene traccia dei processi di debug nel computer locale. In modalità remota, viene avviato un programma denominato msvsmon.exe dallo sviluppatore per gestire il debug remoto e rendere disponibile il PDM. Si noti che msvsmon.exe non è un servizio e deve essere avviato manualmente per abilitare il debug remoto sul computer. Quando Visual Studio (o msvsmon.exe) non è in esecuzione, nessun processo viene tenuta traccia per il debug.  
  
 Ciò significa che uno sviluppatore può eseguire il debug di programmi che egli avviato senza autorizzazioni speciali. Lo sviluppatore può anche eseguire il debug di processi avviati da un altro utente se tale utente è un membro dello stesso gruppo di sicurezza. E per abilitare il debug remoto, è necessario solo per copiare i necessari file al sito remoto del computer e avviare msvsmon.exe (vedere [il debug remoto](../../debugger/remote-debugging.md) per ulteriori dettagli).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [Gestione di Debug di processi](../../extensibility/debugger/process-debug-manager.md)   
 [Debug remoto](../../debugger/remote-debugging.md)
