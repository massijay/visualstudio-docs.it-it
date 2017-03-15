---
title: "Nodi costanti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
caps.latest.revision: 11
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 11
---
# Nodi costanti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella finestra Progettazione shader i nodi costanti rappresentano valori letterali e gli attributi di vertice interpolati dei calcoli di pixel shader.  Poiché gli attributi di vertice sono interpolati \(e pertanto sono diversi per ogni pixel\) ogni istanza di pixel shader riceve una versione diversa della costante.  Ogni pixel ha così un aspetto unico.  
  
## Interpolazione dell'attributo di vertice  
 L'immagine di una scena tridimensionale in un gioco o in un'app viene eseguita matematicamente trasformando una serie di oggetti, che sono definiti attraverso i vertici, gli attributi di vertice e le definizioni dei primitivi, in pixel sullo schermo.  Tutte le informazioni necessarie per dare a un pixel il suo aspetto unico vengono fornite tramite gli attributi del vertice, che sono fusi insieme in base alla vicinanza del pixel ai diversi vertici che costituiscono la *primitiva*.  Una primitiva è un elemento di rendering di base; ovvero una forma semplice come un punto, una riga, o un triangolo.  Un pixel molto vicino solo a uno dei vertici riceve le costanti che sono quasi identiche a quel vertice, ma un pixel che è spaziato uniformemente tra tutti i vertici della primitiva riceve le costanti che costituiscono la media dei vertici.  Nella programmazione grafica, che costanti ricevute dai pixel sono dette *interpolate*.  Fornisce dati costanti ai pixel in questo modo è la qualità visiva molto buona e contemporaneamente riduce i requisiti di larghezza di banda di footprint di memoria.  
  
 Sebbene ogni istanza di pixel shader riceva solo un set di valori costanti e non può modificarli, istanze diverse di pixel shader ricevono set di dati costanti diversi.  Questa progettazione consente a un programma di shader di produrre un output di colore diverso per ogni pixel della primitiva.  
  
## Riferimento nodo della costante  
  
|Nodo|Dettagli|Proprietà|  
|----------|--------------|---------------|  
|**Vettore fotocamera**|Vettore che si estende dal pixel corrente alla camera nello spazio globale.<br /><br /> È possibile utilizzare questo valore per calcolare i riflessi nello spazio globale.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Vettore dal pixel corrente alla fotocamera.|Nessuno|  
|**Costante colore**|Valore colore costante.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Valore di colore.|**Output**<br /> Valore di colore.|  
|**Costante**|Valore scalare costante.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Valore scalare.|**Output**<br /> Valore scalare.|  
|**Costante 2D**|Una costante di vettore a due componenti.<br /><br /> **Output**<br /><br /> `Output`: `float2`<br /> Valore di vettore.|**Output**<br /> Valore di vettore.|  
|**Costante 3D**|Una costante di vettore a tre componenti.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Valore di vettore.|**Output**<br /> Valore di vettore.|  
|**Costante 4D**|Una costante di vettore a quattro componenti.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Valore di colore.|**Output**<br /> Valore di vettore.|  
|**Posizione normalizzata**|Posizione del pixel corrente, espressa in coordinate dispositivo normalizzate.<br /><br /> Le coordinate x e y hanno valori compresi nell'intervallo di \[\(\-1, 1\], la coordinata z ha un valore compreso tra \[0, 1\] e il componente w contiene il valore di profondità del punto nello spazio di visualizzazione; w non è normalizzato.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Posizione del pixel corrente.|Nessuno|  
|**Colore punto**|Colore diffuso del pixel corrente, che è una combinazione degli attributi del colore diffuso del materiale e del colore dei vertici.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Colore diffuso del pixel corrente.|Nessuno|  
|**Profondità del punto**|Profondità del pixel corrente nello spazio di visualizzazione.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Posizione del pixel corrente.|Nessuno|  
|**Profondità punto normalizzato**|Profondità del pixel corrente, espressa in coordinate dispositivo normalizzate.<br /><br /> Il risultato ha un valore nell'intervallo \[0, 1\].<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Posizione del pixel corrente.|Nessuno|  
|**Percorso dello schermo**|Posizione del pixel corrente, espressa in coordinate schermo.<br /><br /> Le coordinate sullo schermo sono basate sul riquadro di visualizzazione corrente.  I componenti x e y contengono le coordinate dello schermo, il componente z contiene la profondità normalizzata a un intervallo di \[0, 1\] e il componente w contiene il valore di profondità nello spazio di visualizzazione.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Posizione del pixel corrente.|Nessuno|  
|**Superficie normale**|Normale alla superficie del pixel corrente nello spazio dell'oggetto.<br /><br /> È possibile utilizzare questo valore per calcolare i contributi dell'illuminazione e i riflessi nello spazio dell'oggetto.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Normale alla superficie del pixel corrente.|Nessuno|  
|**Vettore fotocamera spazio tangente**|Vettore che si estende dal pixel corrente alla camera nello spazio tangente.<br /><br /> È possibile utilizzare questo valore per calcolare i riflessi nello spazio tangente.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Vettore dal pixel corrente alla fotocamera.|Nessuno|  
|**Direzione luce spazio tangente**|Vettore che definisce la direzione in cui la luce è diffusa da una sorgente di luce nello spazio tangente del pixel corrente.<br /><br /> È possibile utilizzare questo valore per calcolare l'illuminazione e i contributi speculari nello spazio tangente.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Vettore dal pixel corrente a una sorgente di luce.|Nessuno|  
|**Normale globale**|Normale alla superficie del pixel corrente nello spazio globale.<br /><br /> È possibile utilizzare questo valore per calcolare i contributi dell'illuminazione e i riflessi nello spazio globale.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Normale alla superficie del pixel corrente.|Nessuno|  
|**Posizione globale**|Posizione del pixel corrente nello spazio globale.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Posizione del pixel corrente.|Nessuno|