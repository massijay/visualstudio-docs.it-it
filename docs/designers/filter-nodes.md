---
title: "Nodi del filtro | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 12
caps.handback.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Nodi del filtro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella finestra Progettazione shader il filtro dei nodi trasforma un valore di input, come un esempio di colore o di trama, in un valore di colore figurativo.  Questi valori di colore figurati vengono comunemente utilizzati nel rendering non fotorealistico o come componenti in altri effetti visivi.  
  
## Riferimento nodo del filtro  
  
|Nodo|Dettagli|Proprietà|  
|----------|--------------|---------------|  
|**Sfocatura**|Offusca i pixel di una trama utilizzando una funzione gaussiana.<br /><br /> È possibile utilizzare questo metodo per ridurre il livello di dettaglio o il rumore di una trama.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate del texel da testare.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Il valore del colore sfocato.|**Trama**<br /> Registro di trama associato al campionatore utilizzato durante lo sfocamento.|  
|**Desatura**|Riduce la quantità di colore nel colore specificato.<br /><br /> Man mano che il colore viene rimosso, il valore di colore si avvicina all'equivalente nelle gradazioni di grigio.<br /><br /> **Input:**<br /><br /> `RGB`: `float3`<br /> Colore da desaturare.<br /><br /> `Percent`: `float`<br /> Percentuale di colore da rimuovere, espressa come un valore normalizzato nell'intervallo \[0, 1\].<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Colore da desaturare.|**Luminanza**<br /> I pesi assegnati ai componenti di colore rosso, verde e blu.|  
|**Rilevamento dei bordi**|Rileva i bordi in una trama utilizzando un rilevatore di bordi Canny.  I pixel del bordo vengono restituiti come bianco, i pixel non del bordo vengono restituiti come nero.<br /><br /> È possibile utilizzare questo valore per identificare i bordi in una trama in modo da poter utilizzare effetti aggiuntivi per trattare i pixel dei bordi.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate del texel da testare.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Bianco se il texel è su un bordo; in caso contrario, nero.|**Trama**<br /> Registro di trama associato al campionatore utilizzato durante il rilevamento dei bordi.|  
|**Nitidezza**|Regolare nitidezza di una trama.<br /><br /> È possibile utilizzare questo metodo per evidenziare i dettagli in una trama.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate del texel da testare.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Il valore del colore sfocato.|**Trama**<br /> Registro di trama associato al campionatore utilizzato durante la regolazione della nitidezza.|