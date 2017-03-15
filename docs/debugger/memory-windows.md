---
title: "Finestra Memoria | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.memory"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Memoria (finestra)"
  - "stringhe [Visual Studio], visualizzazione"
  - "debugger [Visual Studio], finestra Memoria"
  - "memoria [Visual Studio], debug"
  - "debug [Visual Studio], finestra Memoria"
  - "buffer, visualizzazione"
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Finestra Memoria
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella finestra **Memoria** è possibile visualizzare lo spazio di memoria utilizzato dall'applicazione.  Nelle finestre **Espressioni di controllo**, **Controllo immediato**, **Auto** e **Variabili locali** viene visualizzato il contenuto di variabili archiviate in indirizzi specifici della memoria.  Nella finestra **Memoria** viene invece fornita un'immagine generale.  Questa visualizzazione può essere opportuna quando si intende esaminare grandi porzioni di dati, ad esempio buffer o stringhe di notevoli dimensioni, che non vengono visualizzate adeguatamente nella altre finestre.  La finestra **Memoria** non è limitata alla visualizzazione dei dati.  Nella finestra Memoria viene visualizzato ogni tipo di contenuto dello spazio di memoria, sia che si tratti di dati, di codice o di contenuto eliminato e collocato casualmente in spazio di memoria non assegnato.  
  
 La finestra **Memoria** è disponibile solo se il debug a livello di indirizzo è stato abilitato nel nodo **Debug** della finestra di dialogo **Opzioni**.  La finestra **Memoria** non è disponibile per i linguaggi script o SQL che non supportano il concetto di memoria.  
  
## Apertura di una finestra Memoria  
  
#### Per aprire una finestra Memoria  
  
1.  Avviare il debug, se la modalità di debug non è ancora attiva.  
  
2.  Scegliere **Finestre** dal menu **Debug**.  Puntare su **Memoria**, quindi fare clic su **Memoria 1**, **Memoria 2**, **Memoria 3** o **Memoria 4**. \(Le edizioni di livello inferiore di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dispongono unicamente di una singola finestra **Memoria**.  Se si utilizza una di queste edizioni, fare clic su **Memoria**\).  
  
## Paging nella finestra Memoria  
 La finestra **Memoria** dispone di una barra di scorrimento verticale caratterizzata da un funzionamento non standard.  Poiché lo spazio degli indirizzi di un moderno computer è molto ampio, trascinando il cursore su una posizione casuale sarebbe facile perderne la posizione.  Per questa ragione, la casella di scorrimento è fluttuante e rimane sempre al centro della barra di scorrimento.  Nelle applicazioni in codice nativo è possibile spostarsi verso l'alto o verso il basso dello spazio di memoria, ma non è consentito lo scorrimento casuale.  
  
 Gli indirizzi di memoria superiori vengono visualizzati nella parte inferiore della finestra.  Per visualizzare un indirizzo superiore, spostarsi verso il basso, non verso l'alto.  
  
#### Per spostarsi verso l'alto o verso il basso di una pagina di memoria  
  
1.  Per spostarsi verso il basso, ovvero verso un indirizzo di memoria superiore, fare clic sulla barra di scorrimento verticale sotto il cursore.  
  
2.  Per spostarsi verso l'alto, ovvero verso un indirizzo di memoria inferiore, fare clic sulla barra di scorrimento verticale sopra il cursore.  
  
## Selezione di un indirizzo di memoria  
 Per spostarsi immediatamente in una posizione selezionata in memoria, è possibile trascinare la selezione o modificare il valore nella casella **Indirizzo**.  La casella **Indirizzo** accetta non solo valori numerici, ma anche espressioni che restituiscono indirizzi.  Per impostazione predefinita, un'espressione **Indirizzo** viene trattata nella finestra **Memoria** come un'espressione attiva, rivalutata durante l'esecuzione del programma.  Le espressioni attive possono rivelarsi molto utili.  Ad esempio, possono essere utilizzate per visualizzare la memoria selezionata da un puntatore.  
  
#### Per selezionare un indirizzo di memoria mediante trascinamento della selezione  
  
1.  Da qualsiasi finestra selezionare un indirizzo di memoria o una variabile puntatore contenente un indirizzo di memoria.  
  
2.  Trascinare l'indirizzo o il puntatore sulla finestra **Memoria**.  
  
#### Per selezionare una posizione di memoria mediante modifica  
  
1.  Nella finestra **Memoria** selezionare la casella **Indirizzo**.  
  
2.  Digitare o incollare l'indirizzo che si desidera visualizzare, quindi premere **INVIO**.  
  
## Modifica della modalità di visualizzazione delle informazioni nella finestra Memoria  
 È inoltre possibile personalizzare il modo in cui il contenuto della memoria viene visualizzato nella finestra **Memoria**.  Per impostazione predefinita, il contenuto della memoria viene visualizzato come dati integer a 1 byte in formato esadecimale e con un numero di colonne determinato automaticamente dalla larghezza corrente della finestra.  
  
#### Per cambiare il formato del contenuto della memoria  
  
1.  Fare clic con il pulsante destro del mouse sulla finestra **Memoria**.  
  
2.  Scegliere il formato desiderato.  
  
#### Per modificare il numero di colonne nella finestra Memoria  
  
1.  Sulla barra degli strumenti nella parte superiore della finestra **Memoria** individuare l'elenco **Colonne**.  
  
2.  Nell'elenco **Colonne** selezionare il numero di colonne che si desidera visualizzare oppure selezionare **Automatico** per adattare automaticamente il numero di colonne alla larghezza della finestra.  
  
 Se non si desidera che il contenuto della finestra **Memoria** cambi seguendo l'esecuzione del programma, è possibile disattivare la valutazione diretta dell'espressione.  
  
#### Per attivare o disattivare la valutazione diretta  
  
1.  Fare clic con il pulsante destro del mouse sulla finestra **Memoria**.  
  
2.  Scegliere **Rivaluta automaticamente** dal menu di scelta rapida.  
  
     Se la valutazione diretta è attiva, l'opzione risulterà selezionata e facendo clic su di essa la valutazione diretta verrà disattivata.  Se la valutazione diretta non è attiva, l'opzione risulterà deselezionata e facendo clic su di essa verrà attivata.  
  
 È possibile nascondere o visualizzare la barra degli strumenti nella parte superiore della finestra **Memoria**.  Non è possibile accedere alla casella Indirizzo o ad altri strumenti quando la barra degli strumenti è nascosta.  
  
#### Per attivare o disattivare la barra degli strumenti  
  
1.  Fare clic con il pulsante destro del mouse sulla finestra **Memoria**.  
  
2.  Fare clic su **Barra degli strumenti** dal menu di scelta rapida.  
  
     La barra degli strumenti verrà visualizzata o nascosta, a seconda del precedente stato.  
  
## Come seguire il movimento di un puntatore in memoria  
 Nelle applicazioni in codice nativo è inoltre possibile utilizzare i nomi di registro come espressioni attive.  È possibile, ad esempio, utilizzare il puntatore dello stack per seguire lo stack.  
  
#### Per osservare il movimento di un puntatore in memoria  
  
1.  Nella casella **Indirizzo** della finestra **Memoria** digitare un'espressione puntatore.  La variabile puntatore deve trovarsi nell'ambito corrente.  A seconda del linguaggio, può essere necessario dereferenziarla.  
  
2.  Premere **INVIO**.  
  
     Quando si utilizza un comando di esecuzione quale **Esegui**, l'indirizzo di memoria visualizzato cambierà automaticamente seguendo lo spostamento del puntatore.  
  
## Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)