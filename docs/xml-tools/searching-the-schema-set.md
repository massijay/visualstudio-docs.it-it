---
title: "Ricerche nel set di schemi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# Ricerche nel set di schemi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML Schema Explorer consente di eseguire ricerche nel set di schemi nei seguenti modi:  
  
-   Ricerca per parole chiave.  
  
-   Ricerca specifica dello schema.  
  
## Ricerca per parole chiave  
 Le ricerche per parole chiave vengono eseguite immettendo una sottostringa nella casella di testo **Cerca in set di schemi** della barra degli strumenti di XML Schema Explorer.  
  
 ![Ricerca di parole chiave in XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 XML Schema Explorer esegue ricerche dei seguenti elementi nel set di schemi:  
  
-   Attributi `name` o `ref` che corrispondono alla parola chiave specificata.In questo modo è possibile individuare elementi, attributi, tipi e così via in base al nome.  
  
-   Attributi `schemaLocation` delle istruzioni include.  
  
-   Attributi `namespace` delle istruzioni import.  
  
## Ricerca specifica dello schema  
 XML Schema Explorer comprende inoltre ricerche predefinite cui è possibile accedere utilizzando il menu di scelta rapida.Per ulteriori informazioni sui menu di scelta rapida disponibili, vedere [Menu di scelta rapida](../xml-tools/context-menus-xml-schema-explorer.md).È anche possibile eseguire una ricerca specifica dello schema dalla visualizzazione iniziale; per ulteriori informazioni, vedere la sezione "Dettagli set di schemi" nell'argomento [Visualizzazione iniziale](../xml-tools/start-view.md).  
  
## Visualizzazione e spostamento all'interno dei risultati di ricerca  
 Dopo aver terminato la ricerca, il riquadro dei risultati di riepilogo viene aggiunto alla barra degli strumenti con i risultati della ricerca.I risultati della ricerca sono anche evidenziati in XML Schema Explorer e contrassegnati con un segno di spunta sulla barra di scorrimento verticale.È possibile spostarsi tra i risultati della ricerca utilizzando i pulsanti **Risultato ricerca successivo** e **Risultato ricerca precedente** nel riquadro dei risultati di riepilogo della barra degli strumenti di XML Schema Explorer; utilizzando i tasti F3 e Maiusc\+F3 oppure facendo clic sui segni di graduazione nella barra di scorrimento.  
  
 È possibile aggiungere i risultati della ricerca all'area di lavoro facendo clic sul pulsante **Aggiungi nodi evidenziati all'area di lavoro** nel riquadro dei risultati di riepilogo.  
  
 ![Risultati della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## Eliminazione dei risultati di ricerca  
 Per eliminare i risultati di ricerca, fare clic sul pulsante **x** nel riquadro dei risultati di riepilogo della barra degli strumenti di XML Schema Explorer.  
  
## Vedere anche  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)