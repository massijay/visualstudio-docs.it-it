---
title: "Use code maps to debug your applications | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "Visual Studio Ultimate, visualizing code"
  - "Visual Studio Ultimate, navigating code visually"
  - "Visual Studio Ultimate, understanding code"
  - "Visual Studio Ultimate, mapping code relationships"
  - "Visual Studio Ultimate, code maps"
  - "mapping code relationships"
  - "code maps"
  - "mapping relationships in code"
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: 49
caps.handback.revision: 49
author: "alexhomer1"
ms.author: "ahomer"
manager: "douge"
---
# Use code maps to debug your applications
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mappe codice consentono di evitare di perdersi nelle codebase di grandi dimensioni, nel codice con cui si ha poca familiarità o nel codice legacy.  Quando si esegue il debug, ad esempio, potrebbe essere necessario esaminare il codice in file e progetti diversi.  Usare le mappe codice per esplorare queste parti di codice e comprendere le relazioni tra loro.  In questo modo, non è necessario tenere traccia di questo codice a mente o creare un diagramma separato.  Se il lavoro viene interrotto, le mappe codice consentono di aggiornare la memoria relativa al codice usato.  
  
 ![Mappa codici &#45; Mappare le relazioni nel codice](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  
  
 **Una freccia verde indica la posizione del cursore nell'editor**  
  
 Per informazioni dettagliate sui comandi e sulle azioni che è possibile usare quando si usano le mappe codice, vedere [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md).  
  
## Informazioni sul problema  
 Si supponga che sia presente un bug in un programma di disegno su cui si sta lavorando.  Per riprodurre il bug, aprire la soluzione in Visual Studio Ultimate e premere **F5** per avviare il debug.  
  
 Quando si disegna una linea e si sceglie l'opzione **Annulla ultimo tratto** non succede niente finché non si disegna la riga successiva.  
  
 ![Mappa codici &#45; Ripetizione bug](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  
  
 Di conseguenza, iniziare l'analisi cercando il metodo `Undo`.  Il metodo si trova nella classe `PaintCanvas`.  
  
 ![Mappa codici &#45; Trovare codice](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  
  
## Avviare il mapping del codice  
 A questo punto è possibile avviare il mapping del metodo `undo` e le relative relazioni.  Nell'editor di codice aggiungere il metodo `undo` e i campi a cui viene fatto riferimento a una nuova mappa codice.  Quando si crea una nuova mappa, l'indicizzazione del codice potrebbe richiedere del tempo.  Ciò consente alle operazioni successive di essere eseguite più velocemente.  
  
 ![Mappa codici &#45; Visualizzare il metodo e i campi correlati](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  
  
> [!TIP]
>  L'evidenziazione verde indica gli ultimi elementi aggiunti alla mappa.  La freccia verde indica la posizione del cursore nel codice.  Le frecce tra gli elementi rappresentano relazioni diverse.  È possibile ottenere altre informazioni sugli elementi nella mappa spostandovi sopra il mouse ed esaminando le relative descrizioni comandi.  
  
 ![Mappa codici &#45; Visualizzare le descrizioni comandi](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  
  
## Passare al codice ed esaminarlo dal mapping  
 Per visualizzare la definizione di codice per ogni campo, fare doppio clic sul campo nella mappa o selezionare il campo e premere **F12**.  La freccia verde si sposta tra gli elementi nella mappa.  Il cursore nell'editor di codice viene spostato automaticamente.  
  
 ![Mappa codici &#45; Esaminare la definizione di campo](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  
  
 ![Mappa codici &#45; Esaminare la definizione di campo](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  
  
> [!TIP]
>  È inoltre possibile spostare la freccia verde sulla mappa spostando il cursore nell'editor di codice.  
  
## Informazioni sulle relazioni tra parti di codice  
 A questo punto si desidera sapere quale altro codice interagisce con i campi `history` e `paintObjects`.  È possibile aggiungere tutti i metodi che fanno riferimento a questi campi alla mappa.  Questa operazione può essere eseguita dalla mappa o dall'editor di codice.  
  
 ![Mappa codici &#45; Trovare tutti i riferimenti](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  
  
 ![Aprire una mappa codici nell'editor del codice](../modeling/media/codemapstoryboardpaint6a.png "CodeMapStoryboardPaint6A")  
  
> [!NOTE]
>  Se si aggiungono elementi da un progetto condiviso in più applicazioni, ad esempio Windows Phone o Windows Store, tali elementi vengono sempre visualizzati nella mappa insieme al progetto di app attualmente attivo.  Se pertanto si modifica il contesto in un altro progetto di app, il contesto nella mappa viene modificato anche per tutti gli elementi appena aggiunti dal progetto condiviso.  Le operazioni eseguite con un elemento nella mappa si applicano solo agli elementi che condividono lo stesso contesto.  
  
 Modificare il layout per ridisporre il flusso di relazioni e rendere la mappa più facile da leggere.  È inoltre possibile spostare elementi nella mappa trascinandoli.  
  
 ![Mappa codici &#45; Modificare il layout](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  
  
> [!TIP]
>  Per impostazione predefinita, l'opzione **Layout incrementale** è attivata.  Ciò consente di ridisporre la mappa il meno possibile quando vengono aggiunti nuovi elementi.  Per ridisporre l'intera mappa ogni volta che si aggiungono nuovi elementi, disabilitare **Layout incrementale**.  
  
 ![Mappa codici &#45; Modificare il layout](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  
  
 Esaminiamo questi metodi.  Nella mappa fare doppio clic sul metodo **PaintCanvas** oppure selezionarlo e premere **F12**.  Questo metodo crea `history` e `paintObjects` come elenchi vuoti.  
  
 ![Mappa codici &#45; Esaminare la definizione del metodo](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  
  
 A questo punto, ripetere gli stessi passaggi per esaminare la definizione del metodo `clear`.  Il metodo `clear` esegue alcune attività con `paintObjects` e `history` e quindi chiama il metodo `Repaint`.  
  
 ![Mappa codici &#45; Esaminare la definizione del metodo](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  
  
 A questo punto, esaminare la definizione del metodo `addPaintObject`.  Tale metodo esegue alcune attività con `history` e `paintObjects`.  e chiama inoltre `Repaint`.  
  
 ![Mappa codici &#45; Esaminare la definizione del metodo](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  
  
## Individuare il problema esaminando il mapping  
 Sembra che tutti i metodi che modificano `history` e `paintObjects` chiamino `Repaint`.  Tuttavia il metodo `undo` non chiama `Repaint`, anche se `undo` modifica gli stessi campi.  Pertanto, è possibile risolvere il problema chiamando `Repaint` da `undo`.  
  
 ![Mappa codici &#45; Individuare la chiamata al metodo mancante](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  
  
 Se non fosse stata disponibile una mappa che mostrava questa chiamata mancante, sarebbe stato più difficile individuare il problema, specialmente in caso di codice più complesso.  
  
## Condividere l'individuazione e passaggi successivi  
 Prima che l'utente o un altro sviluppatore corregga il bug, è possibile inserire note nella mappa sul problema e su come correggerlo.  
  
 ![Mappa codici &#45; Commentare e contrassegnare elementi per il completamento](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  
  
 Ad esempio, è possibile aggiungere commenti alla mappa e contrassegnare gli elementi usando i colori.  
  
 ![Mappa codici &#45; Elementi commentati e contrassegnati](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  
  
 Se Microsoft Outlook è installato, è possibile inviare la mappa ad altre persone tramite posta elettronica.  È inoltre possibile esportare la mappa come un'immagine o in un altro formato.  
  
 ![Mappa codici &#45; Condividere, esportare, inviare](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  
  
## Correggere il problema e visualizzare le operazioni effettuate  
 Per correggere il bug, aggiungere la chiamata per `Repaint` a `undo`.  
  
 ![Mappa codici &#45; Aggiungere la chiamata al metodo mancante](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  
  
 Per confermare la correzione, riavviare la sessione di debug e tentare di riprodurre il bug.  A questo punto l'opzione **Annulla ultimo tratto** funziona come previsto e consente di verificare che le correzioni apportate siano corrette.  
  
 ![Mappa codici &#45; Confermare la correzione del codice](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  
  
 È possibile aggiornare la mappa per mostrare la correzione apportata.  
  
 ![Mappa codici &#45; Aggiornare la mappa con la chiamata al metodo mancante](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  
  
 La mappa mostrerà un collegamento tra **undo** e **Repaint**.  
  
 ![Mappa codici &#45; Mappa aggiornata con la chiamata al metodo](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  
  
> [!NOTE]
>  Quando si aggiorna la mappa, è possibile che venga visualizzato un messaggio che indica che l'indice di codice usato per creare la mappa è stato aggiornato.  Ciò significa che un utente ha modificato il codice e di conseguenza la mappa non corrisponde al codice corrente.  L'aggiornamento della mappa non verrà arrestato, ma potrebbe essere necessario ricreare la mappa per confermare che corrisponde al codice.  
  
 A questo punto l'analisi è terminata.  Il problema è stato individuato e corretto eseguendo il mapping del codice.  Si dispone inoltre di una mappa che consente di spostarsi nel codice e di ricordare quanto indicato e che mostra i passaggi eseguiti per correggere il problema.  
  
## Vedere anche  
 [Mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [Visualize code](../modeling/visualize-code.md)