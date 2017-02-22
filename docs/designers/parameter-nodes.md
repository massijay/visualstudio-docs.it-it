---
title: "Nodi Parameter | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
caps.latest.revision: 10
caps.handback.revision: 10
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Nodi Parameter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella finestra Progettazione shader i nodi parametro rappresentano gli input dello shader controllati dall'app in base al disegno, ad esempio proprietà materiali, luci direzionali, posizione della fotocamera e ora.  Poiché è possibile modificare questi parametri a ogni chiamata di disegno, è possibile utilizzare lo stesso shader per fornire a un oggetto aspetti diversi.  
  
## Riferimento nodo del parametro  
  
|Nodo|Dettagli|Proprietà|  
|----------|--------------|---------------|  
|**Posizione globale fotocamera**|Posizione della camera nello spazio globale.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Posizione della fotocamera.|Nessuno|  
|**Direzione luce**|Vettore che definisce la direzione in cui la luce è diffusa da una sorgente di luce nello spazio globale.<br /><br /> È possibile utilizzare questo valore per calcolare l'illuminazione e i contributi speculari nello spazio globale.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Vettore dal pixel corrente a una sorgente di luce.|Nessuno|  
|**Ambiente materiale**|Contributo di colore diffuso del pixel corrente attribuito all'illuminazione indiretta.<br /><br /> Il colore diffuso di un pixel simula il modo in cui l'illuminazione interagisce con le superfici ruvide.  È possibile utilizzare il parametro Ambiente materiale per approssimare il modo in cui l'illuminazione indiretta contribuisce all'aspetto di un oggetto nel mondo reale.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Colore diffuso del pixel corrente che è dovuto all'illuminazione indiretta, ovvero la luce ambientale.|**Accesso**<br /> **Pubblico** per consentire che questa proprietà venga impostata dall'editor modello; in caso contrario **Privato**.<br /><br /> **Valore**<br /> Colore diffuso del pixel corrente che è dovuto all'illuminazione indiretta, ovvero l'ambiente.|  
|**Materiale diffuso**|Colore che descrive in che modo l'illuminazione diretta viene diffusa dal materiale del pixel corrente.<br /><br /> Il colore diffuso di un pixel simula il modo in cui l'illuminazione interagisce con le superfici ruvide.  È possibile utilizzare il parametro Materiale diffuso per modificare il modo in cui il pixel corrente diffonde l'illuminazione diretta, vale a dire le luci direzionale, puntiforme e spot.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Colore che descrive in che modo l'illuminazione diretta viene diffusa dal materiale del pixel corrente.|**Accesso**<br /> **Pubblico** per consentire che questa proprietà venga impostata dall'editor modello; in caso contrario **Privato**.<br /><br /> **Valore**<br /> Colore che descrive in che modo l'illuminazione diretta viene diffusa dal materiale del pixel corrente.|  
|**Materiale emissivo**|Contributo di colore diffuso del pixel corrente attribuito all'illuminazione fornita a se stesso.<br /><br /> È possibile utilizzare questo valore per simulare un oggetto brillante, ovvero un oggetto che ha una luce propria.  Questa luce non influisce su altri oggetti.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Contributo di colore del pixel corrente, in base all'illuminazione autofornita.|**Accesso**<br /> **Pubblico** per consentire che questa proprietà venga impostata dall'editor modello; in caso contrario **Privato**.<br /><br /> **Valore**<br /> Contributo di colore del pixel corrente, in base all'illuminazione autofornita.|  
|**Materiale speculare**|Colore che descrive in che modo l'illuminazione diretta viene riflessa dal pixel corrente.<br /><br /> Il colore speculare di un pixel simula il modo in cui l'illuminazione interagisce con le superfici lisce simili agli specchi.  È possibile utilizzare il parametro Materiale speculare per modificare il modo in cui il pixel corrente riflette l'illuminazione diretta, vale a dire le luci direzionale, puntiforme e spot.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Colore che descrive in che modo l'illuminazione diretta viene riflessa dal pixel corrente.|**Accesso**<br /> **Pubblico** per poter impostare questa proprietà dall'editor modello; in caso contrario **Privato**.<br /><br /> **Valore**<br /> Colore che descrive in che modo l'illuminazione diretta viene riflessa dal pixel corrente.|  
|**Materiale potenza speculare**|Valore scalare che descrive l'intensità delle evidenziazioni speculari.<br /><br /> Maggiore è la potenza speculare, più intense e lunghe diventano le evidenziazioni speculari.<br /><br /> **Output:**<br /><br /> `Output`: `float`<br /> Termine esponenziale che descrive l'intensità delle evidenziazioni speculari nel pixel corrente.|**Accesso**<br /> **Pubblico** per consentire che questa proprietà venga impostata dall'editor modello; in caso contrario **Privato**.<br /><br /> **Valore**<br /> Esponente che definisce l'intensità delle evidenziazioni speculari nel pixel corrente.|  
|**Tempo normalizzato**|Tempo in secondi, normalizzato all'intervallo \[0, 1\], in modo tale che quando il tempo raggiunge 1, si reimposta su 0.<br /><br /> È possibile utilizzare questo valore come parametro nei calcoli dello shader, ad esempio per animare coordinate di trama, valori di colore o altri attributi.<br /><br /> **Output:**<br /><br /> `Output`: `float`<br /> Tempo normalizzato, in secondi.|Nessuno|  
|**Ora**|Tempo in secondi.<br /><br /> È possibile utilizzare questo valore come parametro nei calcoli dello shader, ad esempio per animare coordinate di trama, valori di colore o altri attributi.<br /><br /> **Output:**<br /><br /> `Output`: `float`<br /> Tempo in secondi.|Nessuno|