---
title: Stili di codice e azioni rapide | Microsoft Docs
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: BrianPeek
ms.author: brpeek
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
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
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: acc01617fffd7465cee01267482112aac5e352fc
ms.lasthandoff: 03/27/2017

---

# <a name="code-styles-and-quick-actions"></a>Stili di codice e azioni rapide
È possibile impostare le preferenze relative allo stile di codice per i progetti C# e Visual Basic nella finestra **Strumenti > Opzioni** selezionando **Editor di testo > C#/Base > Stile codice > Generale**.  Le opzioni impostate in questa finestra sono valide per il computer locale.  Quando viene selezionata, ogni voce dell'elenco visualizza un'anteprima delle preferenze corrispondenti, come illustrato di seguito.

![Opzioni di stile di codice](~/docs/ide/media/code-style-quick-actions-dialog.png)

Per ogni voce è possibile impostare **Preferenza** e **Gravità** dal menu a discesa disponibile per ogni riga.  La gravità può essere impostata su **Nessuna**, **Suggerimento**, **Avviso** o **Errore**. Visual Studio si comporterà nel modo opportuno.  Se si vogliono usare [azioni rapide](quick-actions.md) con gli stili di codice per riscrivere automaticamente il codice secondo lo stile preferito, assicurarsi che l'impostazione sia diversa da **Nessuna**, in modo che l'icona Lampadina ![Icona Lampadina piccola](~/docs/ide/media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") venga visualizzata quando vengono usati gli stili non preferiti.  È quindi possibile applicare queste preferenze scegliendo l'icona Lampadina o premendo **Ctrl +.** quando il cursore si trova sulla riga di codice appropriata.

Per .NET è possibile gestire le impostazioni relative agli stili di codice anche con un file [EditorConfig](editorconfig-code-style-settings-reference.md).  In questo caso, le impostazioni selezionate nella finestra Opzioni rappresentano le impostazioni di fallback, mentre il file EditorConfig ha la precedenza.  È possibile usare questo file per applicare e configurare lo stile di codifica per l'intero archivio o per tutto il team.

# <a name="see-also"></a>Vedere anche
* [Azioni rapide](quick-actions.md)
