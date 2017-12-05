---
title: "Gestione delle proprietà di progetti e soluzioni | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9242bf08b879e415af658696b2be75a55dc5075
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2017
---
# <a name="managing-project-and-solution-properties"></a>Gestione delle proprietà di progetti e soluzioni

Le proprietà dei progetti governano molti aspetti della compilazione, del debug, del test e della distribuzione. Alcune proprietà sono comuni tra tutti i tipi di progetto e altre sono univoche di piattaforme o linguaggi specifici. Per accedere alle proprietà di progetto, fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni e scegliere **Proprietà** oppure digitare le proprietà nella casella di ricerca **Avvio veloce** nella barra dei menu.

![Menu di scelta rapida Progetto](../ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")

I progetti .NET potrebbero anche avere un nodo di proprietà nell'albero del progetto.

![Nodo Proprietà nell'albero Esplora soluzioni](../ide/media/vs2015_props_se.png "VS2015_Props_SE")

> [!TIP]
> Le soluzioni, così come gli elementi del progetto, hanno alcune proprietà, che sono accessibili nella [Finestra Proprietà](../ide/reference/properties-window.md), non in **Progettazione progetti**.

## <a name="project-properties"></a>Proprietà progetto

Le proprietà del progetto sono organizzate in gruppi, ciascuno dei quali caratterizzato dalla relativa pagina delle proprietà; le pagine potrebbero differire per diverse lingue e tipi di progetto.

### <a name="c-visual-basic-and-f-projects"></a>Progetti C#, Visual Basic e F#

Nei progetti C#, Visual Basic e F# le proprietà sono esposte in **Progettazione progetti**. La figura seguente mostra la pagina della proprietà di compilazione per un progetto WPF in C#:

![Progettazione progetti di Visual Studio](../ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")

Per informazioni su ognuna delle pagine delle proprietà in Progettazione progetti, vedere [Riferimenti alle proprietà di progetto](../ide/reference/project-properties-reference.md).

### <a name="c-and-javascript-projects"></a>Progetti C++ e JavaScript

I progetti C++ e JavaScript hanno un'interfaccia utente differente per la gestione delle proprietà del progetto. Questa illustrazione mostra la pagina delle proprietà di un progetto C++ (le pagine JavaScript sono simili):

![Proprietà di progetto Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")

Per informazioni sulle proprietà di progetto C++, vedere [Utilizzo di proprietà di progetto (C++)](/cpp/ide/working-with-project-properties). Per altre informazioni sulle proprietà JavaScript, vedere [Pagine proprietà, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Proprietà soluzione

Per accedere alle proprietà della soluzione, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Proprietà**. Nella finestra di dialogo è possibile impostare le configurazioni di progetto per le compilazioni di debug o di rilascio, scegliere i progetti che devono essere il progetto di avvio quando viene premuto F5 e impostare le opzioni di analisi del codice.

## <a name="see-also"></a>Vedere anche

[Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
