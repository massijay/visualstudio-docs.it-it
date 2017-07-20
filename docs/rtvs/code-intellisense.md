---
title: IntelliSense per codice R per Visual Studio | Documenti di Microsoft
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3677-e5ec-4e11-82a8-d914a93b1aa9
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
ms.openlocfilehash: 359b9dc6bae84bb6d89e5f0f646c0b8fed5898ec
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---


# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense visualizza informazioni sulle funzioni che è possibile chiamare, sui membri di oggetti, sugli argomenti della funzione e sui [frammenti di codice](code-snippets.md) direttamente durante la scrittura del codice. Visualizza anche i possibili completamenti durante la digitazione e completa quando si preme TAB o INVIO (vedere le [opzioni dell'editor](code-editing.md#editor-options) nella scheda **Avanzate**). Intellisense è disponibile sia nell'editor che nella[ finestra interattiva](interactive-repl.md).

![Visualizzazione di una firma della funzione di IntelliSense](media/intellisense-function-signature.png) 

Durante la digitazione di una funzione o di un'altra istruzione, IntelliSense offre menu di completamento automatico (con distinzione tra maiuscole e minuscole) filtrato in base ai valori che sono già stati immessi:

![Menu di completamento automatico di IntelliSense](media/intellisense-auto-complete-menu.png)

Premendo TAB (o INVIO o BARRA SPAZIATRICE a seconda delle opzioni impostate) è possibile inserire l'elemento selezionato nell'elenco a discesa. È possibile modificare la selezione con i tasti di direzione. 

IntelliSense offre anche suggerimenti per i membri di oggetti R:
 
![Suggerimenti di IntelliSense per i membri di un oggetto](media/intellisense-auto-complete-r-objects.png)
 
Se si preme ESC, l'intero menu scompare. È possibile ripristinarlo premendo CTRL+BARRA SPAZIATRICE.

Se si digita il segno di `(` aperta per una chiamata di funzione viene inserito il segno di `)` chiusa e viene ripristinato il supporto per la firma come illustrato in precedenza:

![Supporto per la firma per una funzione di IntelliSense](media/intellisense-function-signature.png)

Premere nuovamente ESC per chiudere la finestra popup. È possibile ripristinarla per le firme della funzione premendo CTRL+MAIUSC+BARRA SPAZIATRICE.

> [!Tip]
> Se la guida dei parametri copre il testo sotto, come può succedere nell'editor del file, è possibile tenere premuto CTRL per rendere il testo della guida semitrasparente.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense per variabili e funzioni definite dall'utente

IntelliSense viene applicato anche per il completamento del parametro "name" di funzioni definite dall'utente nello stesso file:

![IntelliSense per funzioni definite dall'utente](media/intellisense-same-file-functions.png)

![Completamento parametri di IntelliSense per funzioni definite dall'utente](media/intellisense-parameter-completion.png)

IntelliSense viene applicato anche a variabili nello stesso file e nella sessione corrente:

![Completamento variabili di IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> Nella finestra interattiva IntelliSense prende in considerazione solo i nomi nella sessione corrente di R e ignora i file nel progetto.

## <a name="code-suggestions"></a>Suggerimenti di codice

Quando al margine viene visualizzata una lampadina, detta smart tag, significa che Visual Studio sta suggerendo un collegamento per una delle azioni più usate. Ad esempio, passare il puntatore su una riga che contiene un'istruzione `library` nell'editor. Verrà visualizzata una lampadina. Selezionando la lampadina, verranno visualizzate le opzioni disponibili:

![Smart tag per R nell'editor](media/intellisense-smart-tags.png)

