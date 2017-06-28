---
title: "Nodi di matematica | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adc225cc-1cf5-4f7c-9b00-e7ac8450b6b9
caps.latest.revision: 10
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 10
---
# Nodi di matematica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella finestra Progettazione shader i nodi matematici eseguono operazioni algebriche, logiche, trigonometriche e altre matematiche.  
  
> [!NOTE]
>  Quando si utilizzano i nodi matematici nella finestra di Progettazione shader, la promozione del tipo è particolarmente evidente.  Per informazioni su come la promozione del tipo influisce sui parametri di input, vedere la sezione "Promozione di input" in [Nodi della finestra di progettazione shader](../designers/shader-designer-nodes.md).  
  
## Riferimento del nodo Math  
  
|Nodo|Dettagli|Proprietà|  
|----------|--------------|---------------|  
|**Abs**|Calcola il valore assoluto dell'input specificato, per componente.<br /><br /> Per ciascun componente dell'input `X`, i valori negativi sono resi positivi in modo che ogni componente del risultato abbia un valore positivo.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori per i quali determinare il valore assoluto.<br /><br /> `Output:`<br /><br /> `Output`: uguale all'input `X`<br /> Valore assoluto, per componente.|None|  
|**Add**|Calcola la somma per componente degli input specificati per componente.<br /><br /> Per ciascun componente del risultato, i componenti corrispondenti dell'input `X` e dell'input `Y` vengono aggiunti insieme.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei valori da aggiungere insieme.<br /><br /> `Y`: uguale all'input `X`<br /> Uno dei valori da aggiungere insieme.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> La somma, per componente.|None|  
|**Ceil**|Calcola il limite massimo dell'input specificato, per componente.<br /><br /> La parte intera superiore di un valore è l'Integer più piccolo maggiore o uguale a tale valore.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori per i quali calcolare il tetto massimo.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Parte intera superiore, per componente.|None|  
|**Morsa**|Fissa ogni componente dell'input specificato in un intervallo predefinito.<br /><br /> Per ciascun componente del risultato, i valori al di sotto dell'intervallo definito sono resi uguali al valore minimo dell'intervallo, i valori al di sopra dell'intervallo definito sono resi uguali al valore massimo dell'intervallo e i valori compresi nell'intervallo non vengono modificati.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori da fissare.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Valore impostato, per componente.|**Max**<br /> Valore massimo dell'intervallo.<br /><br /> **Min**<br /> Valore minimo dell'intervallo.|  
|**Cos**|Calcola il coseno dell'input specificato, in radianti, per componente.<br /><br /> Per ciascun componente del risultato, viene calcolato il coseno del componente corrispondente, fornito in radianti.  Il risultato ha componenti con valori compresi nell'intervallo \[\-1, 1\].<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori di cui calcolare il coseno, in radianti.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Il coseno, per componente.|None|  
|**Cross**|Calcola il prodotto incrociato dei vettori a tre componenti specificati.<br /><br /> È possibile utilizzare il prodotto incrociato per calcolare la normale a una superficie definita da due vettori.<br /><br /> **Input:**<br /><br /> `X`: `float3`<br /> Vettore di sinistra del prodotto incrociato.<br /><br /> `Y`: `float3`<br /> Vettore di destra del prodotto incrociato.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Prodotto incrociato.|None|  
|**Distanza**|Calcola la distanza tra i punti specificati.<br /><br /> Il risultato è un valore scalare positivo.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei punti per determinare la distanza.<br /><br /> `Y`: uguale all'input `X`<br /> Uno dei punti per determinare la distanza.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> La distanza.|None|  
|**Divisione**|Calcola il quoziente per componente degli input specificati.<br /><br /> Per ciascun componente del risultato, il componente corrispondente del primo input `X` viene diviso per il componente corrispondente dell'input `Y`.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori dividendi.<br /><br /> `Y`: uguale all'input `X`<br /> Valori divisori.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Quoziente, per componente.|None|  
|**Punto**|Calcola il prodotto scalare dei vettori specificati.<br /><br /> Il risultato è un valore scalare.  È possibile utilizzare il prodotto scalare per determinare l'angolo tra due vettori.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei termini.<br /><br /> `Y`: uguale all'input `X`<br /> Uno dei termini.<br /><br /> **Output:**<br /><br /> `Output`: `float`<br /> Prodotto scalare.|None|  
|**Floor**|Calcola il limite minimo dell'input specificato, per componente.<br /><br /> Per ciascun componente del risultato, il valore è l'Integer intero più grande che sia minore o uguale al componente corrispondente dell'input.  Ogni componente del risultato è un Integer intero.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori per i quali calcolare il tetto minimo.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Tetto minimo, per componente.|None|  
|**Fmod**|Calcola i moduli \(resto\) per componente degli input specificati.<br /><br /> Per ciascun componente del risultato, un multiplo integrale \(numero intero\), m, del componente corrispondente dell'input `Y` viene sottratto dal componente corrispondente dell'input `X`, lasciando un resto.  Il multiplo, m, viene scelto in modo che il resto sia minore del componente corrispondente dell'input `Y` e abbia lo stesso segno del componente corrispondente dell'input `X`.  Ad esempio, fmod\(\-3.14, 1.5\) è \-0.14.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori dividendi.<br /><br /> `Y`: uguale all'input `X`<br /> Valori divisori.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Modulo, per componente.|None|  
|**Frac**|Rimuove la parte integrale \(numero intero\) dell'input specificato per componente.<br /><br /> Per ciascun componente del risultato, la parte integrale del componente corrispondente dell'input viene rimossa, ma la parte frazionaria e il segno vengono mantenuti.  Questo valore frazionario rientra nell'intervallo \[0, 1\].  Ad esempio, il valore \-3.14 diventa il valore \-0.14.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori per i quali calcolare la parte frazionaria.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Parte frazionaria, per componente.|None|  
|**Lerp**|Interpolazione lineare.  Calcola la media soppesata per componente degli input specificati.<br /><br /> Per ciascun componente del risultato, la media soppesata dei componenti corrispondenti degli input `X` e `Y`.  Il peso viene fornito dell'input `Percent`, scalare applicato in modo uniforme a tutti i componenti.  È possibile utilizzare questo valore per interpolare tra punti, colori, attributi e altri valori.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valore originario.  Quando `Percent` è uguale a zero, il risultato è uguale all'input.<br /><br /> `Y`: uguale all'input `X`<br /> Valore terminale.  Quando `Percent` è uguale a uno, il risultato è uguale all'input.<br /><br /> `Percent`: `float`<br /> Un peso scalare espresso come percentuale della distanza dalla `X` di input verso la `Y` di input.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Un valore che è collineare con gli input specificati.|None|  
|**Aggiunta multipla**|Calcola la moltiplicazione\-addizione per componente degli input specificati.<br /><br /> Per ciascun componente del risultato, il prodotto dei componenti corrispondenti degli input `M` e `A` viene aggiunto al componente corrispondente dell'input `B`.  Questa sequenza di operazioni è presente in formule comuni, ad esempio nella formula punto\-inclinazione di una linea e nella formula per scalare e quindi compensare un input.<br /><br /> **Input:**<br /><br /> `M`: `float`, `float2`, `float3` o `float4`<br /> Uno dei valori da moltiplicare insieme.<br /><br /> `A`: uguale all'input `M`<br /> Uno dei valori da moltiplicare insieme.<br /><br /> `B`: uguale all'input `M`<br /> Valori da aggiungere al prodotto degli altri due input.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `M`<br /> Risultato dell'operazione di moltiplicazione e addizione, per componente.|None|  
|**Max**|Calcola il massimo per componente degli input specificati.<br /><br /> Per ciascun componente del risultato, viene preso il maggiore dei componenti corrispondenti degli input.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei valori per i quali calcolare il massimo.<br /><br /> `Y`: uguale all'input `X`<br /> Uno dei valori per i quali calcolare il massimo.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Valore massimo, per componente.|None|  
|**Min**|Calcola il minimo per componente degli input specificati.<br /><br /> Per ciascun componente del risultato, viene preso il minore dei componenti corrispondenti degli input.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei valori per i quali calcolare il minimo.<br /><br /> `Y`: uguale all'input `X`<br /> Uno dei valori per i quali calcolare il minimo.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Valore minimo, per componente.|None|  
|**Moltiplica**|Calcola il prodotto per componente degli input specificati.<br /><br /> Per ciascun componente del risultato, i componenti corrispondenti degli input `X` e `Y` vengono moltiplicati insieme.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei valori da moltiplicare insieme.<br /><br /> `Y`: uguale all'input `X`<br /> Uno dei valori da moltiplicare insieme.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Prodotto, per componente.|None|  
|**Normalizza**|Normalizza il vettore specificato.<br /><br /> Un vettore normalizzato mantiene la direzione del vettore originale, ma non l'ampiezza.  È possibile utilizzare i vettori normalizzati per semplificare i calcoli in cui è importante l'ampiezza di un vettore.<br /><br /> **Input:**<br /><br /> `X`: `float2`, `float3` o `float4`<br /> Vettore da normalizzare.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Vettore normalizzato.|None|  
|**Uno meno**|Calcola la differenza tra 1 e l'input specificato per componente.<br /><br /> Per ciascun componente del risultato, il componente corrispondente dell'input viene sottratto da 1.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori da sottrarre da 1.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Differenza tra 1 e l'input specificato, per componente.|None|  
|**Potenza**|Calcola l'esponente per componente degli input specificati.<br /><br /> Per ciascun componente del risultato, il componente corrispondente dell'input `X` viene elevato alla potenza del componente corrispondente dell'input `Y`.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori di base<br /><br /> `Y`: uguale all'input `X`<br /> Valori dell'esponente.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Elevamento a potenza, per componente.|None|  
|**Saturazione**|Fissa ogni componente dell'input specificato nell'intervallo \[0, 1\].<br /><br /> È possibile utilizzare questo intervallo per rappresentare le percentuali e altre misurazioni relative nei calcoli.  Per ciascun componente del risultato, i valori dei componenti corrispondenti dell'input minori di 0 sono resi uguali a 0, i valori maggiori di 1 sono resi uguali a 1 e i valori compresi nell'intervallo non vengono modificati.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori da saturare.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Valore saturato, per componente.|None|  
|**Seno**|Calcola il seno dell'input specificato, in radianti, per componente.<br /><br /> Per ciascun componente del risultato, viene calcolato il seno del componente corrispondente, fornito in radianti.  Il risultato ha componenti con valori compresi nell'intervallo \[\-1, 1\].<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori di cui calcolare il seno, in radianti.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Il seno, per componente.|None|  
|**Sqrt**|Calcola la radice quadrata dell'input specificato, per componente.<br /><br /> Per ciascun componente del risultato, viene calcolata la radice quadrata del componente corrispondente.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori per i quali calcolare la radice quadrata.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Radice quadrata, per componente.|None|  
|**Sottrai**|Calcola la differenza per componente degli input specificati.<br /><br /> Per ciascun componente del risultato, il componente corrispondente dell'input `Y` viene sottratto dal componente corrispondente dell'input `X`.  È possibile utilizzare questo valore per calcolare il vettore che si estende dal primo input al secondo.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori da sottrarre.<br /><br /> `Y`: uguale all'input `X`<br /> Valori da sottrarre all'input `X`.<br /><br /> **Output:**<br /><br /> `Output`: uguale all'input `X`<br /> Differenza, per componente.|None|  
|**Trasforma vettore 3D**|Trasforma il vettore 3D specificato in uno spazio differente.<br /><br /> È possibile utilizzare questo valore per portare punti o vettori in uno spazio comune per poterli utilizzare per eseguire calcoli significativi.<br /><br /> **Input:**<br /><br /> `Vector`: `float3`<br /> Vettore da trasformare.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Vettore trasformato.|**Da sistema**<br /> Spazio nativo del vettore.<br /><br /> **A sistema**<br /> Spazio in cui trasformare il vettore.|