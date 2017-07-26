---
title: Opzioni, Editor di testo, C/C++, Sperimentale | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 77c4408fcd93a776468cf5fb23b3807a2b8d594d
ms.contentlocale: it-it
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-cc-experimental"></a>Opzioni, Editor di testo, C/C++, Sperimentale
Modificando queste opzioni è possibile modificare il comportamento correlato a IntelliSense e il database di esplorazione quando si programma in C o C++. Queste funzionalità sono davvero sperimentali. È possibile che vengano modificate o rimossa da Visuali Studio in una versione futura. In questo argomento vengono descritte le opzioni di Visual Studio 2017. Per Visual Studio 2015, vedere [Opzioni, Editor di testo, C/C++, Sperimentale](https://msdn.microsoft.com/library/mt591979.aspx) 
  
 Per accedere a questa pagina delle proprietà, premere **CTRL + Q** per attivare `Quick Launch` e quindi digitare "sperimentale". Avvio veloce troverà la pagina dopo le prime lettere. È anche possibile accedere scegliendo **Strumenti | Opzioni**, espandendo **Editor di testo** e **C/C++** e quindi scegliendo **Sperimentale**.  

 In un'installazione di Visual Studio 2017 sono disponibili queste funzionalità.  
  
> [!NOTE]
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="enable-predictive-intellisense"></a>Abilita IntelliSense predittivo
IntelliSense predittivo limita il numero di risultati visualizzati nell'elenco a discesa di IntelliSense, in modo che siano visualizzati solo i risultati pertinenti al contesto. Se ad esempio si digita <code> int x = </code> e si chiama l'elenco a discesa di IntelliSense, vengono visualizzati solo numeri interi o funzioni che restituiscono numeri interi. Per impostazione predefinita, IntelliSense predittivo è disattivato.

## <a name="enable-faster-project-load"></a>Abilita caricamento più rapido del progetto
Questa opzione consente a Visual Studio di memorizzare nella cache i dati di progetto in modo che alla successiva apertura del progetto sia possibile caricare i dati presenti nella cache anziché rielaborare i dati dai file di progetto. L'uso dei dati memorizzati nella cache può accelerare i tempi di caricamento del progetto in modo significativo.  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Altre funzionalità in Visual Studio Gallery
Per altre funzionalità dell'editor di testo in Visual Studio Gallery, vedere l'elenco disponibile [qui](http://go.microsoft.com/fwlink/?LinkId=692016). Un esempio è [Correzioni rapide per C++](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), che supporta quanto segue:  
  
-   **Aggiunta di #include mancante** : suggerisce gli #include rilevanti per i simboli sconosciuti nel codice  
  
-   **Aggiunta dell'uso dello spazio dei nomi/simbolo completo** : come l'elemento precedente, ma per gli spazi dei nomi  
  
-   **Aggiunta del punto e virgola mancante**  
  
-   **Guida di MSDN** : cercare i messaggi di errore in MSDN  
  
 È possibile passare il mouse su una sottolineatura ondulata per ottenere una lampadina oppure usare la combinazione di tasti predefinita Ctrl+punto (Ctrl+.). Per la combinazione di tasti, non è necessario che il punto di inserimento sia posizionato sull'errore specifico o token. È sufficiente trovarsi sulla stessa riga dell'errore per richiamare i suggerimenti per tutti gli elementi della riga.  
  
## <a name="see-also"></a>Vedere anche  
 [Setting Language-Specific Editor Options](../../ide/reference/setting-language-specific-editor-options.md)  (Impostazione delle opzioni dell'editor specifiche del linguaggio)  
 [Refactoring in C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)

