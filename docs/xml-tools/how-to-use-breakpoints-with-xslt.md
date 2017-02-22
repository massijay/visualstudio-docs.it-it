---
title: "Procedura: utilizzare i punti di interruzione con XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: utilizzare i punti di interruzione con XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile impostare punti di interruzione in un foglio di stile XSLT o nel documento di origine XML.Se si imposta un punto di interruzione su un tag, all'avvio dell'esecuzione il punto di interruzione si sposterà all'istruzione successiva che dispone di informazioni sulla riga del codice sorgente.  
  
 Per ulteriori informazioni, vedere [Debugging Basics: Breakpoints](http://msdn.microsoft.com/it-it/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## Impostazione di un punto di interruzione in un foglio di stile  
 È possibile impostare punti di interruzione su tag di inizio e di fine e nodi di tipo text di un foglio di stile XSLT.È inoltre possibile impostare punti di interruzione in un blocco di script del codice.  
  
#### Per impostare un punto di interruzione in un foglio di stile  
  
1.  Aprire un foglio di stile nell'editor XML.  
  
2.  Collocare il cursore sulla posizione del punto di interruzione, fare clic con il pulsante destro del mouse, scegliere **Punto di interruzione**, quindi fare clic su **Inserisci punto di interruzione**.  
  
3.  Fare clic sul pulsante Sfoglia \(**...**\) nel campo di **Input** della finestra Proprietà del documento.  
  
4.  Individuare il documento di origine XML e fare clic su **Apri**.  
  
     In questo modo viene impostato il file del documento di origine utilizzato per la trasformazione XSLT.  
  
5.  Fare clic sul pulsante **Debug XSLT** sulla barra degli strumenti dell'editor XML.  
  
## Impostazione di un punto di interruzione nel documento di origine XML  
 È possibile impostare punti di interruzione su elementi, attributi, nodo dello spazio dei nomi, commenti, istruzioni di elaborazione e nodi di tipo text di un documento di origine XML.Non è possibile impostare un punto di interruzione sul nodo del documento o su un nodo di spazio dei nomi ereditato dall'elemento padre.  
  
#### Per impostare un punto di interruzione nel documento di origine XML  
  
1.  Aprire il documento XML nell'editor XML.  
  
2.  Collocare il cursore sulla posizione del punto di interruzione, fare clic con il pulsante destro del mouse, scegliere **Punto di interruzione**, quindi fare clic su **Inserisci punto di interruzione**.  
  
3.  Fare clic sul pulsante Sfoglia \(**...**\) nel campo di **Foglio di stile** della finestra Proprietà del documento.  
  
4.  Individuare il documento di origine XML e fare clic su **Apri**.  
  
     In questo modo viene impostato il file del documento di origine utilizzato per la trasformazione XSLT.  
  
5.  Fare clic sul pulsante **Debug XSLT** sulla barra degli strumenti dell'editor XML.  
  
## Vedere anche  
 [Procedura dettagliata: eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)