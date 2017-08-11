---
title: R Markdown con R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: b29ae0240a29616edcdf2ae0dced7a9fca0f9584
ms.contentlocale: it-it
ms.lasthandoff: 07/12/2017

---

# <a name="creating-r-markdown-documents"></a>Creazione di documenti R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) è un formato di documento che trasforma l'analisi in R in documenti, report, presentazioni e dashboard di alta qualità.

Per R Markdown R Tools per Visual Studio offre un modello di elemento, il supporto dell'editor (tra cui IntelliSense per il codice R all'interno dell'editor) e funzionalità di generazione di file.

Per usare R Markdown:

1. Chiudere Visual Studio.
1. (Una sola volta) Installare `pandoc` da [pandoc.org](http://pandoc.org/installing.html).
1. Riavviare Visual Studio, che deve rilevare l'installazione di pandoc.
1. Installare i pacchetti `knitr` e `rmarkdown`. È possibile eseguire questa operazione dalla [finestra interattiva](interactive-repl.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Creare un nuovo file R Markdown usando il comando di menu **File > Nuovo** e selezionando **R Markdown** dall'elenco. In alternativa, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e selezionare **Aggiungi R Markdown**. Oppure usare **Aggiungi > Nuovo elemento...**  e selezionare **R Markdown** dall'elenco.

1. Il contenuto predefinito del nuovo file è il seguente:

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---
    
    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.
    
    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:
    
    ```{r}
    summary(cars)
    ```
    
    You can also embed plots, for example:
    
    ```{r, echo=FALSE}
    plot(cars)
    ```
    
    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
    
    ~~~

1. In qualsiasi momento durante la modifica, fare clic con il pulsante destro del mouse nell'editor e selezionare **Anteprima**, in cui sono disponibili le opzioni relative ad HTML, PDF e Microsoft Word. Da tale anteprima è possibile salvare il file nel modo più appropriato per il formato scelto.

