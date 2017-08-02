---
title: Guida di R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef9c04d4-0d5e-405a-842e-8d47fa0e8781
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 6644ea68ae691e8467828ff699245fef4e485971
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---


# <a name="help-in-r-tools-for-visual-studio"></a>Guida di R Tools per Visual Studio

La Guida di R è integrata direttamente nella finestra interattiva in Visual Studio. Quando si usa il comando `?`, ad esempio `?mtcars`, viene visualizzata la Guida dalla documentazione di R in una finestra di Visual Studio:

![Finestra della Guida in Visual Studio](~/rtvs/media/help-window.png)

> [!Tip]
> La finestra della Guida, come tutte le finestre di Visual Studio, può essere disposta e ancorata a seconda delle proprie preferenze. Vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> È anche possibile aprire i risultati della Guida in un browser selezionando il menu **R Tools > Opzioni** e impostando la proprietà **Browser della Guida di R** su `External`. Vedere [R Tools for Visual Studio options](options.md) (Opzioni di R Tools per Visual Studio).

Per eseguire la ricerca nella Guida, usare il comando `??` con il termine di ricerca tra virgolette se include spazi:

```R
??"Motor Trend"
```

![Risultati della ricerca nella Guida](~/rtvs/media/help-search1.png)

La finestra della Guida ha anche un campo di immissione per la ricerca tramite il quale è possibile eseguire altre ricerche direttamente nella documentazione di R:

![Risultati della ricerca nella Guida tramite il campo di immissione](~/rtvs/media/help-search2.png)

## <a name="integrated-help-lookup"></a>Ricerca nella Guida integrata

Poiché spesso gli sviluppatori eseguono ricerche nella documentazione di R per informazioni su nomi di funzione, set di dati e altri elementi, R Tools per Visual Studio semplifica il processo integrando le ricerche della Guida direttamente nell'editor e nella finestra interattiva.

- Se si preme F1 durante un'operazione di completamento automatico, viene visualizzato un elenco di risultati della ricerca nella Guida corrispondenti alla sottostringa.
- Fare clic con il pulsante destro del mouse su un termine di ricerca, ad esempio una funzione, e selezionare il comando **Help on** (Guida su) o premere F1 per aprire la Guida per tale funzione. È anche possibile richiamare **Help on** (Guida su) per qualsiasi selezione.

    ![Richiamare la Guida mediante il menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse](~/rtvs/media/help-right-click.png)

> [!Tip]
> Per aprire la Guida integrata in un browser, selezionare **R Tools > Opzioni** e impostare **Web browser F1** su `External`. Vedere [R Tools for Visual Studio options](options.md) (Opzioni di R Tools per Visual Studio).

## <a name="integrated-stackoverflow-search"></a>Ricerca di StackOverflow integrata

Oltre a eseguire ricerche nella documentazione di R, gli sviluppatori spesso cercano anche in StackOverflow durante la scrittura del codice. RTVS semplifica anche tale processo. Quando si fa clic con il pulsante destro del mouse su un termine o una selezione e si seleziona il comando **Search web for** (Cerca nel Web), oppure si preme CTRL + F1, si apre una finestra di Visual Studio (o un browser, se è stata modificata l'opzione **Web browser F1**) che contiene i risultati della ricerca per tale termine che ha come ambito StackOverflow per impostazione predefinita:

![Risultati della ricerca nel Web in Visual Studio](~/rtvs/media/help-web-search-results.png)

È possibile modificare la stringa aggiunta, `R site:stackoverflow`, tramite l'opzione **R Tools > Opzioni > Stringa di ricerca sul Web F1**:

![Modifica dell'opzione Stringa di ricerca sul Web F1](~/rtvs/media/options-dialog.png)
