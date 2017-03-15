---
title: "Procedura: utilizzare il visualizzatore della struttura ad albero di WPF | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug, WPF"
  - "WPF, debug"
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: utilizzare il visualizzatore della struttura ad albero di WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare il visualizzatore della struttura ad albero di WPF per esplorare la struttura ad albero visuale di un oggetto WPF e visualizzare le proprietà di dipendenza WPF per gli oggetti contenuti in quella struttura ad albero.  Per ulteriori informazioni sulle strutture ad albero visuali, vedere [Strutture ad albero in WPF](../Topic/Trees%20in%20WPF.md).  Per ulteriori informazioni sulle proprietà di dipendenza, vedere [Cenni preliminari sulle proprietà di dipendenza](../Topic/Dependency%20Properties%20Overview.md).  
  
 Quando si apre il visualizzatore della struttura ad albero di WPF, vengono visualizzati due riquadri: la **struttura ad albero visuale** sulla sinistra e il riquadro **Proprietà di** *Name***:***Type* sulla destra.  Selezionare un oggetto qualsiasi nel riquadro **Struttura ad albero visuale** e il riquadro delle **proprietà di** *Name***:***Type* verrà aggiornato automaticamente per mostrare le proprietà di quell'oggetto.  
  
### Per aprire il visualizzatore della struttura ad albero di WPF  
  
1.  In un suggerimento dati, in una finestra **Espressioni di controllo**, **Auto** o **Variabili locali** fare clic sulla freccia della lente d'ingrandimento accanto al nome di un oggetto WPF.  
  
     Verrà visualizzato un elenco di visualizzatori.  
  
2.  Fare clic su **Visualizzatore della struttura ad albero di WPF**.  
  
### Per eseguire ricerche nella struttura ad albero visuale  
  
-   Nel riquadro **Struttura ad albero visuale**, digitare la stringa da cercare nella casella **Cerca**.  
  
     Il visualizzatore della struttura ad albero di WPF troverà immediatamente il primo oggetto nella struttura ad albero visuale che corrisponde alla stringa digitata.  Digitare più caratteri per trovare una corrispondenza più accurata.  
  
    -   Per passare alla corrispondenza successiva all'interno della struttura ad albero visuale, fare clic su **Successiva**.  
  
    -   Per ritornare alla corrispondenza precedente, fare clic su **Prec**.  
  
    -   Per cancellare i criteri di ricerca, fare clic su **Cancella**.  
  
### Per eseguire ricerche nell'elenco di proprietà  
  
-   Nel riquadro **Proprietà di** *Name***:***Type* digitare la stringa che si desidera cercare nella casella **Filtro**.  
  
     Il visualizzatore della struttura ad albero di WPF troverà immediatamente le proprietà che corrispondono alla stringa digitata; nell'elenco sono visualizzate soltanto le proprietà corrispondenti alla stringa digitata.  Digitare più caratteri per trovare una corrispondenza più accurata.  
  
    -   Per cancellare i criteri di ricerca, fare clic su **Cancella**.  
  
### Per chiudere il visualizzatore  
  
-   Fare clic sull'icona **Chiudi** nell'angolo in alto a destra della finestra di dialogo.  
  
## Vedere anche  
 [Procedura: utilizzare un visualizzatore](../Topic/How%20to:%20Use%20a%20Visualizer.md)   
 [Visualizzatori](../debugger/create-custom-visualizers-of-data.md)   
 [Strutture ad albero in WPF](../Topic/Trees%20in%20WPF.md)   
 [Cenni preliminari sulle proprietà di dipendenza](../Topic/Dependency%20Properties%20Overview.md)