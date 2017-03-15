---
title: "Procedura: eseguire una trasformazione XSLT dall&#39;editor XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura: eseguire una trasformazione XSLT dall&#39;editor XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor XML consente di associare un foglio di stile XSLT a un documento XML, eseguire la trasformazione e visualizzare l'output.L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.  
  
 La proprietà **Output** specifica il nome del file per l'output.Se la proprietà **Output** è vuota, viene generato un nome di file nella directory temporanea.L'estensione del file è basata sull'elemento `xsl:output` del foglio di stile e può essere .xml, .txt o .htm.  
  
 Se la proprietà **Output** specifica un nome di file con estensione .htm o .html, viene visualizzata l'anteprima dell'output XSLT utilizzando [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer.Tutte le altre estensioni di file vengono aperte utilizzando l'editor predefinito scelto da [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio.Ad esempio, se l'estensione del file è .xml, Visual Studio utilizzerà l'editor XML.  
  
### Per eseguire una trasformazione XSLT da un documento XML  
  
1.  Aprire un documento XML nell'editor XML.  
  
2.  Associare un foglio di stile XSLT al documento XML.  
  
    -   Aggiungere un'istruzione di elaborazione `xml-stylesheet` al documento XML.Ad esempio, aggiungere la seguente riga `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` al prologo del documento.  
  
         In alternativa  
  
    -   Aggiungere il foglio di stile XSLT utilizzando la finestra **Proprietà**.Nella **Finestra Proprietà** del documento fare clic sul pulsante **Sfoglia** per il campo **Foglio di stile**, selezionare il foglio di stile XSLT e scegliere **Apri**.  
  
3.  Fare clic sul pulsante **Mostral'output XSL** sulla barra degli strumenti dell'**Editor XML**.  
  
    > [!NOTE]
    >  Se al documento XML non è associato alcun foglio di stile, viene visualizzata una finestra di dialogo con la richiesta di specificare il foglio di stile da utilizzare.  
    >   
    >  L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.  
  
### Per eseguire una trasformazione XSLT da un foglio di stile XSLT  
  
1.  Aprire il foglio di stile XSLT nell'editor XML.  
  
2.  Specificare un documento XML nel campo **Input** della finestra **Proprietà** del documento.  
  
    > [!NOTE]
    >  Il documento XML è il documento di input utilizzato per la trasformazione.Se non è stato specificato alcun documento quando la trasformazione XSLT è stata avviata, viene visualizzata la finestra di dialogo **Apri file** in cui è possibile specificare un documento.  
  
3.  Fare clic sul pulsante **Mostral'output XSLT** sulla barra degli strumenti dell'**Editor XML**.  
  
     L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.  
  
### Per fornire un nome di file di output diverso  
  
1.  Specificare un nome di file nel campo **Output** della finestra **Proprietà** del documento.  
  
2.  Fare clic sul pulsante **Mostral'output XSLT** sulla barra degli strumenti dell'**Editor XML**.  
  
     L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento e l'editor utilizzato nella finestra di output dipende dall'estensione del file della proprietà del documento di **Output**.  
  
## Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)