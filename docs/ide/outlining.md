---
title: "Struttura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "struttura"
  - "Visual Studio, espansione/compressione del codice"
  - "Visual Studio, struttura"
  - "codice di espansione/compressione"
  - "codice [Visual Studio], struttura"
  - "codice [Visual Studio], nascondere"
  - "strutturazione di codice"
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Struttura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile scegliere di nascondere parte del codice dalla visualizzazione comprimendo un'area del codice in modo che venga visualizzata sotto un segno più \(\+\).  Espandere un'area compressa facendo clic sul segno più. \(O premere CTRL \+ M \+ M per comprimere un'area quindi un CTRL\+ M \+ M per ampliarla nuovamente.\) È inoltre possibile comprimere una regione delineata facendo doppio clic su qualsiasi riga nell'area nel margine della struttura, visualizzato a sinistra del codice.  È possibile visualizzare il contenuto di un'area compressa come tooltip quando si posiziona il puntatore sull'area compressa.  
  
 Le aree nel margine della struttura vengono evidenziate quando si posiziona il puntatore sul bordo con il mouse.  Il colore predefinito di evidenziazione può essere piuttosto leggero in alcune configurazioni di colore.  È possibile modificarlo in **Strumenti\/Opzioni\/Ambiente\/Carattere e colori\/Regione comprimibile**.  
  
 Quando si lavora in codice strutturato, è possibile espandere le sezioni su cui si desidera operare, comprimerle al termine del lavoro, quindi spostarsi ad altre sezioni.  Quando non si desidera più la visualizzazione strutturata, è possibile utilizzare il comando **Rimuovi struttura** per rimuovere le informazioni relative alla struttura senza alterare il codice.  
  
 I comandi **Annulla** e **Ripristina** del menu **Modifica** hanno effetto su queste operazioni.  I comandi **Copia**, **Taglia**, **Incolla** e le operazioni di trascinamento mantengono le informazioni di struttura, ma non lo stato dell'area comprimibile.  Quando, ad esempio, si copia un'area compressa, mediante il comando **Incolla** il testo copiato verrà incollato come area espansa.  
  
> [!CAUTION]
>  Quando si modifica una determinata area delimitata, la delimitazione potrebbe venir persa.  Ad esempio, l'eliminazione o l'operazione Trova e sostituisci possono determinare la cancellazione della fine dell'area.  
  
 I seguenti comandi sono disponibili nel sottomenu **Modifica\/Struttura**.  
  
|||  
|-|-|  
|Nascondi selezione|\(CTRL \+ M, CTRL \+ H\) \- Comprime un blocco di codice selezionato che in genere non sarà disponibile per la struttura, ad esempio un blocco `if`.  Per rimuovere l'area personalizzata, utilizzare **Visualizza selezione nascosta** \(o CTRL \+ M, CTRL \+ U\).  Non disponibile in Visual Basic.|  
|Espandi\/Comprimi struttura|\- Consente di invertire lo stato corrente \(nascosto o espanso\) della sezione più interna della struttura il cursore passa all'interno di una sezione annidata compressa.|  
|Attiva\/Disattiva tutte le strutture|\(CTRL \+ M, CTRL \+ L\) \- setta tutte le aree allo stesso stato \(espanso o compresso\).  Se alcune aree sono espanse e altre nascoste, tutte le aree nascoste verranno espanse.|  
|Rimuovi struttura|\(CTRL \+ M, CTRL \+ P\) \- Rimuove tutte le informazioni relative alla struttura per l'intero documento.|  
|Visualizza selezione nascosta|\(CTRL \+ M, CTRL \+ U\)  \- Rimuove le informazioni sulla struttura relative all'area definita dall'utente attualmente selezionata.  Non disponibile in Visual Basic.|  
|Comprimi alle definizioni|\(CTRL \+ M, CTRL \+ O\) \- Comprime i membri di tutti i tipi.|  
|Comprimi blocco:\<blocco logico\>|\(Visual C\+\+\) Comprime un'area nella funzione che contiene il punto di inserimento.  Ad esempio, se il punto di inserimento si trova in un ciclo, il ciclo è nascosto.|  
|Comprime tutto in: \<strutture logiche\>|\(Visual C\+\+\) Comprime tutte le strutture all'interno della funzione.|  
  
 È inoltre possibile utilizzare Visual Studio SDK per definire le aree del testo che si desidera espandere o comprimere.  Vedere [Procedura dettagliata: struttura](../extensibility/walkthrough-outlining.md).