---
title: "Nodi di trama | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
caps.latest.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 12
---
# Nodi di trama
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Progettazione shader i nodi della trama effettuano il campionamento dei vari tipi di trama e geometrie e producono o trasformano le coordinate trama.  Le trame forniscono il livello di dettaglio di illuminazione e di colore degli oggetti.  
  
## Riferimento nodo della trama  
  
|Nodo|Dettagli|Proprietà|  
|----------|--------------|---------------|  
|**Campione mappa cubi**|Preleva un campione di colore da una mappa di cubo alle coordinate specificate.<br /><br /> È possibile utilizzare una mappa cubi per fornire dettagli di colore per gli effetti di riflesso o per applicare una trama a un oggetto sferico con meno distorsione rispetto a una trama 2D.<br /><br /> **Input:**<br /><br /> `UVW`: `float3`<br /> Un vettore che specifica la posizione nel cubo di trama dove viene preso l'esempio.  L'esempio indica il punto in cui il vettore interseca il cubo.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Esempio di colore.|**Trama**<br /> Registro di trama associato al campionatore.|  
|**Campione mappa normale**|Preleva un campione normale da una normale mappa 2D alle coordinate specificate<br /><br /> È possibile utilizzare una mappa normale per simulare l'aspetto di dettagli geometrici aggiuntivi sulla superficie di un oggetto.  Le mappe normali contengono dati compressi che rappresentano un vettore unitario anziché dati di colore.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate in cui è prelevato il campione.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Esempio normale.|**Regolazione asse**<br /> Fattore utilizzato per regolare la mano utilizzata per scrivere del campione di mappa normale.<br /><br /> **Trama**<br /> Registro di trama associato al campionatore.|  
|**Panoramica UV**|Effettua una panoramica delle coordinate di trama specificate in funzione di tempo.<br /><br /> È possibile utilizzare questo valore per spostare una mappa di trama o normale sulla superficie di un oggetto.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate di cui eseguire la panoramica.<br /><br /> `Time`: `float`<br /> Il tempo di spostamento, in secondi.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> Coordinate in panoramica.|**Velocità X**<br /> Numero di texel visualizzati in panoramica lungo l'asse x, al secondo.<br /><br /> **Velocità Y**<br /> Numero di texel visualizzati in panoramica lungo l'asse y, al secondo.|  
|**Parallasse UV**|Modifica le coordinate di trama specificate come funzione dell'altezza e dell'angolo di visualizzazione.<br /><br /> L'effetto creato è noto come *mapping del parallasse* o mapping di spostamento virtuale.  È possibile utilizzare questo valore per creare un'illusione di profondità su una superficie piana.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate da spostare.<br /><br /> `Height`: `float`<br /> Il valore di heightmap associato alle coordinate `UV`.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> Coordinate spostate.|**Piano profondità**<br /> Profondità di riferimento per l'effetto di parallasse.  Per impostazione predefinita, il valore è 0,5.  I valori minori sollevano la trama, mentre quelli maggiori la sprofondano nella superficie.<br /><br /> **Scala profondità**<br /> Scala dell'effetto di parallasse.  La profondità apparente diventa più o meno pronunciata.  I valori tipici sono compresi tra 0,02 e 0,1.|  
|**Rotazione UV**|Ruota le coordinate di trama specificate intorno a un punto centrale come una funzione di tempo.<br /><br /> È possibile utilizzare questo valore per ruotare una mappa di trama o normale sulla superficie di un oggetto.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate da ruotare.<br /><br /> `Time`: `float`<br /> Il tempo di spostamento, in secondi.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> Coordinate ruotate.|**Centra X**<br /> Coordinata x che definisce il centro della rotazione.<br /><br /> **Centra Y**<br /> Coordinata y che definisce il centro della rotazione.<br /><br /> **Velocità**<br /> Angolo, in radianti, in base a cui viene ruotata la trama al secondo.|  
|**Coordinata trama**|Le coordinate di trama del pixel corrente.<br /><br /> Le coordinate di trama sono determinate dall'interpolazione tra gli attributi delle coordinate di trama dei vertici vicini.  È possibile considerare questo valore come la posizione del pixel corrente nello spazio di trama.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> Coordinate di trama.|None|  
|**Dimensioni trama**|Restituisce la larghezza e l'altezza di una mappa di trama 2D.<br /><br /> È possibile utilizzare le dimensioni della trama per prendere in considerazione la larghezza e l'altezza della trama nello shader.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> La larghezza e l'altezza della trama, espresse come vettori.  La larghezza viene memorizzata nel primo elemento del vettore.  L'altezza viene memorizzata nel secondo elemento.|**Trama**<br /> Registro di trama associato alla dimensione della trama.|  
|**Differenza texel**|Restituisce il delta \(distanza\) tra i texels di una mappa di trama 2D.<br /><br /> È possibile utilizzare il delta di texel per campionare i valori di texel adiacenti nello shader.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> Il delta \(distanza\) da un texel al texel seguente \(spostandosi in diagonale nella direzione positiva\), espresso come un vettore nello spazio di trama normalizzato.  È possibile derivare le posizioni di tutti i texels adiacenti in modo selettivo ignorando o negando le coordinate V o U del delta.|**Trama**<br /> Registro di trama associato al delta di texel.|  
|**Campione trama**|Preleva un campione di colore da un mapping di trama 2D alle coordinate specificate.<br /><br /> È possibile utilizzare una mappa di trama per fornire dettagli di colore sulla superficie di un oggetto.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate in cui è prelevato il campione.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Esempio di colore.|**Trama**<br /> Registro di trama associato al campionatore.|