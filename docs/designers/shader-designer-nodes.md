---
title: "Nodi della finestra di progettazione shader | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 6
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 6
---
# Nodi della finestra di progettazione shader
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Articoli in questa sezione della documentazione contengono informazioni sui vari nodi di Progettazione shader che è possibile utilizzare per creare effetti grafici.  
  
## Nodi e tipi di nodo  
 La finestra di Progettazione shader rappresenta gli effetti visivi in un grafico.  Questi grafici derivano da nodi che sono appositamente selezionati e connessi in modo tale da ottenere l'effetto desiderato.  Ogni nodo rappresenta un'informazione o una funzione matematica e le connessioni tra essi rappresentano il modo in cui le informazioni attraversano il grafico per generare il risultato.  Nella finestra di Progettazione shader sono disponibili sei i differenti tipi di nodi, i filtri, i nodi di trama, i parametri, le costanti, nodi di utilità e i nodi matematici, e molti nodi singoli appartengono a ciascun tipo.  Questi nodi e i tipi di nodi sono descritti negli altri articoli di questa sezione. Vedere i collegamenti alla fine del presente documento.  
  
## Struttura del nodo  
 Tutti i nodi sono costituiti da una combinazione di elementi comuni.  Ogni nodo contiene almeno un terminale di output dal lato destro \(eccetto il nodo colore finale che rappresenta l'output dello shader\).  I nodi che rappresentano i calcoli o campionatori di trama dispongono di terminali di input sul lato sinistro, mentre i nodi che rappresentano le informazioni non hanno terminali di input.  I terminal di output sono connessi ai terminal di input per spostare informazioni da un nodo a un altro.  
  
### Promozione di input  
 Poiché la finestra di Progettazione shader deve infine generare il codice sorgente HLSL in modo che l'effetto possa essere utilizzato in un gioco o in un'applicazione, i nodi della finestra di Progettazione shader soggetti alle regole di promozione del tipo utilizzate da HLSL.  Poiché l'hardware grafico opera principalmente sui valori a virgola mobile, la promozione del tipo tra tipi diversi \(ad esempio da `int` a `float` o da `float` a `double`\) è qualcosa di raro.  Al contrario, poiché l'hardware grafico utilizza immediatamente la stessa operazione su più informazioni, può verificarsi un tipo diverso di promozione in cui il più breve di un certo numero di input viene allungato in base alla dimensione dell'input più lungo.  Il modo in cui viene allungato dipende dal tipo di input e anche dall'operazione stessa:  
  
-   **Se il tipo più piccolo è un valore scalare:**  
  
     Il valore di scalare viene replicato in un vettore che corrisponde nella dimensione all'input più grande.  Ad esempio, l'input scalare 5,0 diventa il vettore \(5,0, 5,0, 5,0\) quando l'input maggiore dell'operazione è un vettore a tre elementi, indipendentemente dall'operazione.  
  
-   **Se il tipo più piccolo è un vettore e l'operazione è moltiplicativa \(\*, \/, % e così via\):**  
  
     Il valore del vettore viene copiato negli elementi iniziali di un vettore con dimensione uguale all'input maggiore e gli elementi finali vengono impostati su 1,0.  Ad esempio, l'input vettoriale \(5,0, 5,0\) diventa il vettore \(5,0, 5,0, 1,0, 1,0\) quando viene moltiplicato per un vettore a quattro elementi.  In questo modo vengono mantenuti il terzo e il quarto elemento dell'output utilizzando l'identità moltiplicativa, 1,0.  
  
-   **Se il tipo più piccolo è un vettore e l'operazione è aggiuntiva \(\+, \- e così via\):**  
  
     Il valore del vettore viene copiato negli elementi iniziali di un vettore con dimensione uguale all'input maggiore e gli elementi finali vengono impostati su 0,0.  Ad esempio, l'input vettoriale \(5,0, 5,0\) diventa il vettore \(5,0, 5,0, 0,0, 0,0\) quando viene aggiunto a un vettore a quattro elementi.  In questo modo vengono mantenuti il terzo e il quarto elemento dell'output utilizzando l'identità aggiuntiva, 0,0.  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Nodi costanti](../designers/constant-nodes.md)|Vengono descritti i nodi che è possibile utilizzare per rappresentare valori letterali e informazioni sullo stato del vertice interpolate nei calcoli dello shader.  Poiché lo stato del vertice è interpolato \(e pertanto è diverso per ogni pixel\) ogni istanza di pixel shader riceve una versione diversa della costante.|  
|[Nodi Parameter](../designers/parameter-nodes.md)|Vengono descritti i nodi che è possibile utilizzare per rappresentare la posizione della fotocamera, le proprietà dei materiali, i parametri di luce, l'ora e altre informazioni sullo stato delle applicazioni nei calcoli dello shader.|  
|[Nodi di trama](../designers/texture-nodes.md)|Vengono descritti i nodi da utilizzare per il campionamento dei vari tipi di trama e geometrie e per produrre o trasformare le coordinate trama in modi comuni.|  
|[Nodi di matematica](../designers/math-nodes.md)|Vengono descritti i nodi che è possibile utilizzare per eseguire operazioni algebriche, logiche, trigonometriche e altre operazioni matematiche mappate direttamente alle istruzioni HLSL.|  
|[Nodi utilità](../designers/utility-nodes.md)|Vengono descritti i nodi che è possibile utilizzare per eseguire calcoli comuni sull'illuminazione e altre operazioni comuni non mappate direttamente alle istruzioni HLSL.|  
|[Nodi del filtro](../designers/filter-nodes.md)|Vengono descritti i nodi che è possibile utilizzare per filtrare la trama e il colore.|