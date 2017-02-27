---
title: "Procedura: valutare un&#39;espressione XPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura: valutare un&#39;espressione XPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile valutare le espressioni XPath tramite la finestra di dialogo **Controllo immediato**.L'espressione XPath deve essere valida in base alla raccomandazione W3C XPath 1.0 \(informazioni in lingua inglese\).Il contesto XSLT corrente, ovvero il nodo `self::node()` nella finestra **Variabili locali**, fornisce il contesto di valutazione per l'espressione XPath.  
  
 Nell'elenco seguente vengono descritte le funzioni supportate durante la valutazione di un'espressione XPath:  
  
-   Sono supportate le funzioni XPath incorporate.  
  
-   Non sono supportate le funzioni XSLT incorporate.  
  
-   Non sono supportate le funzioni definite dall'utente.  
  
> [!NOTE]
>  Nella procedura seguente vengono utilizzati i file belowAvg.xsl e books.xml dall'argomento [Procedura dettagliata: eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md).  
  
### Per valutare un'espressione XPath  
  
1.  Inserire un punto di interruzione in corrispondenza del tag di inizio `xsl:if`.  
  
2.  Fare clic sul pulsante **Debug XSLT** sulla barra degli strumenti dell'editor XML.  
  
     Il debugger viene avviato e interrotto sul tag `xsl:if`.  
  
3.  Fare clic con il pulsante destro del mouse su **Controllo immediato**.  
  
     Verrà visualizzata la finestra di dialogo **Controllo immediato**.  
  
4.  Immettere `./price/text()` nel campo **Espressione** della finestra di dialogo **Controllo immediato** e scegliere **Rivaluta**.  
  
     Il prezzo del nodo libro corrente viene visualizzato nella casella **Valore**.  
  
5.  Modificare l'espressione XPath in `./price/text() < $bookAverage` e fare clic su **Rivaluta**.  
  
     Nella casella **Valore** viene mostrato che l'espressione XPath restituisce `true`.  
  
## Vedere anche  
 [Debug di XSLT](../xml-tools/debugging-xslt.md)