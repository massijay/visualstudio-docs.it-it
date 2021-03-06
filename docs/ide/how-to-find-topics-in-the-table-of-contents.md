---
title: "Procedura: trovare argomenti nel sommario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hv_contents"
helpviewer_keywords: 
  - "Scheda contenuti [Visualizzatore della Guida 2.0]"
  - "Visualizzatore della Guida 2.0, Scheda contenuti"
  - "Visualizzatore della Guida 2.0, applicazione di filtri alla tavola dei contenuti"
  - "applicazione di filtri alla tavola dei contenuti [Visualizzatore della Guida 2.0]"
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Procedura: trovare argomenti nel sommario
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella scheda **Sommario** è possibile usare il sommario per trovare le informazioni.  Il sommario è un elenco espandibile che contiene tutti argomenti dei libri installati.  Per informazioni sull'accessibilità relative a come spostarsi nel sommario, vedere [Tasti di scelta rapida \(visualizzatore della Guida\)](../ide/shortcut-keys-help-viewer.md).  
  
> [!IMPORTANT]
>  L'ambito degli argomenti disponibili nel sommario dipende dal filtro selezionato.  
  
## Filtrare il sommario  
 È possibile filtrare il sommario per limitare l'ambito degli argomenti visualizzati nella scheda **Sommario**.  I titoli vengono visualizzati nell'elenco solo se contengono la radice del termine specificato.  Ad esempio, se si specifica la parola "risoluzione" come filtro, verranno visualizzati solo i titoli contenenti la parola "risolvere" o "risoluzione".  I nodi i cui titoli non contengono il termine verranno compressi in un unico nodo con i puntini di sospensione \(...\).  
  
#### Per filtrare il sommario  
  
1.  Scegliere la scheda **Sommario**.  
  
2.  Nella casella di testo **Filtra contenuti** immettere un termine.  
  
> [!NOTE]
>  Se l'esecuzione del filtro richiede molto tempo, è possibile visualizzare i risultati più rapidamente usando l'operatore di ricerca avanzata `title:`.  
  
## Sincronizzare un argomento con il sommario  
 Se un argomento è stato aperto tramite l'indice o le funzionalità di ricerca full\-text, è possibile determinarne la posizione all'interno del sommario sincronizzando quest'ultimo con la finestra dell'argomento.  
  
#### Per sincronizzare il sommario con la finestra dell'argomento  
  
1.  Visualizzare un argomento.  
  
2.  Fare clic sul pulsante **Mostra argomento nel contenuto** nella barra degli strumenti oppure premere                                                            CTRL\+S                                                           .  
  
     Viene aperta la scheda **Sommario** in cui viene visualizzata la posizione dell'argomento nel sommario.  
  
## Vedere anche  
 [Individuare informazioni](../ide/locate-information.md)   
 [Visualizzatore della Guida Microsoft](../ide/microsoft-help-viewer.md)