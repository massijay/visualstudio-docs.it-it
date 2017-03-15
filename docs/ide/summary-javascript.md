---
title: "&lt;summary&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "summary (tag XML JavaScript)"
  - "<summary> (tag XML JavaScript)"
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica la descrizione per una funzione o un metodo.  
  
## Sintassi  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### Parametri  
 `locid`  
 Parametro facoltativo.  L'identificatore per informazioni sulla localizzazione della funzione o del metodo.  L'identificatore è un membro ID o corrisponde al valore dell'attributo `name` in un gruppo di messaggi definiti dai metadati di OpenAjax.  Il tipo dell'identificatore dipende dal formato specificato nell'elemento [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Parametro facoltativo.  Una descrizione della funzione o del metodo.  
  
## Note  
 Gli elementi utilizzati per annotare le funzioni, compresi [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md) e [\<returns\>](../ide/returns-javascript.md), devono essere inseriti nel corpo della funzione prima delle istruzioni.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare l'elemento `<summary>`.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)