---
title: "&lt;deprecated&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica una funzione o un metodo deprecato.  
  
## Sintassi  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### Parametri  
 `type`  
 Parametro facoltativo.  Specifica se la funzione o il metodo sarà rimosso nelle versioni future, o se la funzione o il metodo è già stato rimosso e che il relativo utilizzo può provocare un errore.  Impostare a `deprecate` per specificare che la funzione o il metodo sarà rimosso nelle versioni future.  Impostare a `remove` per specificare che la funzione o il metodo è già stato rimosso.  
  
 `locid`  
 Parametro facoltativo.  L'identificatore per informazioni sulla localizzazione della funzione o del metodo.  L'identificatore è un membro ID o corrisponde al valore dell'attributo `name` in un gruppo di messaggi definiti dai metadati di OpenAjax.  Il tipo dell'identificatore dipende dal formato specificato nell'elemento [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Parametro facoltativo.  Una descrizione della funzione o del metodo che è stato deprecato.  
  
## Note  
 Gli elementi utilizzati per annotare le funzioni, compresi `<deprecated>`, devono essere inseriti nel corpo della funzione prima delle istruzioni.  Quando si contrassegna una funzione come deprecata, è consigliabile sostituire il relativo elemento [\<summary\>](../ide/summary-javascript.md) con l'elemento `<deprecated>`.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare l'elemento `<deprecated>`.  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)