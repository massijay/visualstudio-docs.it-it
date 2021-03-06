---
title: 'Procedura: Creare e rimuovere dipendenze di progetto | Microsoft Docs'
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9762bf8905ad162bd6059fae9ed1b7be06ca7919
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Procedura: creare e rimuovere dipendenze di progetto
Quando si compila una soluzione che contiene più progetti, può essere necessario prima compilare alcuni progetti, per generare il codice usato da altri progetti. Quando un progetto usa codice eseguibile generato da un altro progetto, il progetto che genera il codice viene definito come dipendenza del progetto che usa il codice. Tali relazioni di dipendenza possono essere definite nella finestra di dialogo **Dipendenze progetto**.  

### <a name="to-assign-dependencies-to-projects"></a>Per assegnare le dipendenze ai progetti  

1.  Selezionare un progetto in Esplora soluzioni.  

2.  Nel menu **Proprietà** scegliere **Dipendenze progetto**.  

     Viene visualizzata la finestra di dialogo **Dipendenze progetto**.  

    > [!NOTE]
    >  L'opzione **Dipendenze progetto** è disponibile solo in una soluzione con più progetti.  

3.  Nella scheda **Dipendenze** selezionare un progetto dal menu a discesa **Progetto**.  

4.  Nel campo **Dipendente da** selezionare la casella di controllo di qualsiasi altro progetto da compilare prima del progetto specificato.  

 La soluzione deve contenere più di un progetto per poter creare dipendenze di progetto.  

### <a name="to-remove-dependencies-from-projects"></a>Per rimuovere dipendenze dai progetti  

1.  Selezionare un progetto in Esplora soluzioni.  

2.  Nel menu **Proprietà** scegliere **Dipendenze progetto**.  

     Viene visualizzata la finestra di dialogo **Dipendenze progetto**.  

    > [!NOTE]
    >  L'opzione **Dipendenze progetto** è disponibile solo in una soluzione con più progetti.  

3.  Nella scheda **Dipendenze** selezionare un progetto dal menu a discesa **Progetto**.  

4.  Nel campo **Dipendente da** deselezionare le caselle di controllo accanto agli altri progetti che non sono più dipendenze del progetto specificato.  

## <a name="see-also"></a>Vedere anche  
 [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md)  (Compilazione e creazione)  
 [Understanding Build Configurations](../ide/understanding-build-configurations.md)  (Informazioni sulle configurazioni delle compilazioni)  
 [Gestione delle proprietà di progetti e soluzioni](managing-project-and-solution-properties.md)

