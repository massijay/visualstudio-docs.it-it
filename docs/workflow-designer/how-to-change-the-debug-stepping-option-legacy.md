---
title: 'Procedura: modificare l''opzione di esecuzione di istruzioni Debug (Legacy) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ff11186c82102230ec939c0c9b1c5aba69df7f3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Procedura: modificare l'opzione di avanzamento nell'esecuzione del debug (legacy)
In questo argomento viene descritto come modificare l'opzione di avanzamento nell'esecuzione del debug per le applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy aventi azioni simultanee. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando si esegue il debug di attività legacy esecuzione simultanea, ad esempio **ParallelActivity** o **ConditionedActivityGroup**, è possibile utilizzare una delle due opzioni per esaminare il codice.  
  
 Seguire questi passaggi per modificare l'opzione di avanzamento nell’esecuzione del debug nel progetto del flusso di lavoro legacy.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-change-the-debug-stepping-option"></a>Per modificare l'opzione di avanzamento nell'esecuzione del debug  
  
1.  Avviare Visual Studio.  
  
2.  Aprire un progetto flusso di lavoro legacy esistente o creare un nuovo progetto che usa attività simultanee e che viene destinato a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
3.  Nel **flusso di lavoro** menu legacy [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], scegliere **Debug**e quindi **opzioni di esecuzione di istruzioni**.  
  
4.  Selezionare l'opzione **istanza** o **ramo**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di flussi di lavoro Legacy](../workflow-designer/debugging-legacy-workflows.md)   
 [Opzioni di avanzamento nell’esecuzione del debug (legacy)](../workflow-designer/debug-stepping-options-legacy.md)