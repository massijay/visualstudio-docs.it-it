---
title: Frammenti di codice con R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bf4f87-e276-40cd-bc17-3dfb47ef1870
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
ms.openlocfilehash: 033a06b276b8a31e6c69b0eff68ee3f76dda1042
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---

# <a name="code-snippets"></a>Frammenti di codice

I frammenti di codice in Visual Studio offrono collegamenti per inserire rapidamente blocchi di codice di lunghezza arbitraria. In questo modo non è necessario digitare più volte un codice simile. R Tools per Visual Studio (RTVS) aggiunge decine di frammenti R utili alla raccolta di Visual Studio.

Per inserire un frammento di codice, digitare il nome abbreviato del frammento (è disponibile IntelliSense) e premere TAB per inserire.

Di seguito alcuni semplici esempi:

- Digitare `=` e premere TAB. RTVS si espande fino all'operatore di assegnazione `<-`.
- Digitare `>` e premere TAB. RTVS si espande fino all'operatore pipe `%>%`.

I frammenti di codice sono molto più che un semplice completamento di caratteri. Ad esempio, non è più necessario dover ricordare i nomi dei parametri nella chiamata di funzioni complesse, come in questo frammento di codice per la lettura di un file CSV con la funzione `read.csv`:

![Animazione dell'uso di un frammento di codice per inserire una chiamata a read.csv](media/code-snippet-expansion.gif)

In questo caso, durante la digitazione di `readc`, IntelliSense visualizza un elenco di completamento. Selezionare il completamento nel menu a discesa e premere TAB per selezionare `readc`. Premere nuovamente TAB per espandere il frammento. Per questo motivo, l'espansione del frammento equivale spesso a "digitare il frammento e premere TAB due volte". Nella maggior parte dei casi, la prima volta che si preme TAB si completa la selezione di IntelliSense e la seconda volta si attiva l'espansione.

Per visualizzare tutti i frammenti disponibili, aprire la finestra di dialogo **Strumenti > Gestione frammenti di codice...**  (CTRL+K,B) e selezionare **R** per **Linguaggio**. Espandere i gruppi e selezionare singoli frammenti per visualizzare una descrizione e il testo del collegamento:

![Finestra di dialogo dei frammenti di codice per R](media/code-snippet-dialog.png)

Per creare frammenti di codice personalizzati, attenersi alle istruzioni in [Procedura dettagliata: creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md). Un frammento di codice è in definitiva semplicemente un file XML. Di seguito è ad esempio riportato il frammento per l'operazione di pipe (collegamento `>`)

Si noti che un frammento di codice è semplicemente un file XML. Di seguito è riportato il frammento di codice per l'operatore pipe:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

I file XML per tutti i frammenti di codice vengono installati con RTVS. Nel campo **Posizione** in **Gestione frammenti di codice** è specificato il percorso. È possibile individuarli anche nel codice sorgente di RTVS su GitHub in [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).

