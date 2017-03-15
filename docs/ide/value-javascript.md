---
title: "&lt;value&gt; (JavaScript) | Microsoft Docs"
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
  - "<value> (tag XML JavaScript)"
  - "value (tag XML JavaScript)"
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;value&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica le informazioni sulla documentazione per le funzioni `get` e `set` per le proprietà di ECMAScript 3.  
  
## Sintassi  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### Parametri  
 `type`  
 Parametro facoltativo.  Il tipo di dati della proprietà.  Il tipo può essere uno dei seguenti:  
  
-   Un linguaggio ECMAScript nella specifica di ECMAScript 5, come `Number` e `Object`.  
  
-   Un oggetto DOM, come `HTMLElement`, `Window` e `Document`.  
  
-   Una funzione costruttore JavaScript.  
  
 `integer`  
 Parametro facoltativo.  Se `type` è `Number`, specifica se la proprietà è un integer.  Impostare a `true` per indicare che la proprietà è un integer; in caso contrario, impostare a `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `domElement`  
 Parametro facoltativo.  Questo attributo è deprecato; l'attributo `type` ha la precedenza su questo attributo.  Questo attributo specifica se la proprietà documentata è un elemento DOM.  Impostare a `true` per specificare che la proprietà è un elemento DOM; in caso contrario, impostare su `false`.  Se l'attributo `type` non è impostato e `domElement` è impostato a `true`, l'IntelliSense considera la proprietà documentata come un `HTMLElement` quando esegue il completamento delle istruzioni.  
  
 `mayBeNull`  
 Parametro facoltativo.  Specifica se la proprietà documentata può essere impostata a null.  Impostare a `true` per indicare che la proprietà può essere impostata a null; in caso contrario, impostare a `false`.  Il valore predefinito è `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementType`  
 Parametro facoltativo.  Se `type` è `Array`, questo attributo specifica il tipo degli elementi nell'array.  
  
 `elementInteger`  
 Parametro facoltativo.  Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nell'array sono integer.  Impostare a `true` per indicare che gli elementi nell'array sono integer; in caintegertrario, impostare a `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementDomElement`  
 Parametro facoltativo.  Questo attributo è deprecato; l'attributo `elementType` ha la precedenza su questo attributo.  Se `type` è `Array`, questo attributo consente di specificare se gli elementi nell'array sono elementi DOM.  Impostare a `true` per specificare che gli elementi sono elementi DOM; in caso contrario, impostare su `false`.  Se l'attributo `elementType` non è impostato e `elementDomElement` è impostato a `true`, l'IntelliSense considera ogni elemento dell'array come `HTMLElement` quando esegue il completamento delle istruzioni.  
  
 `elementMayBeNull`  
 Parametro facoltativo.  Se `type` è `Array`, specifica se gli elementi nell'array possono essere impostati a null.  Impostare a `true` per indicare che gli elementi dell'array possono essere impostati a null; in caso contrario, impostare a `false`.  Il valore predefinito è `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `locid`  
 Parametro facoltativo.  L'identificatore per le informazioni sulla localizzazione riguardo alla proprietà.  L'identificatore è un membro ID o corrisponde al valore dell'attributo `name` in un gruppo di messaggi definiti dai metadati di OpenAjax.  Il tipo dell'identificatore dipende dal formato specificato nell'elemento [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Parametro facoltativo.  Una descrizione della proprietà.  
  
## Note  
 Le proprietà di ECMAScript 5 utilizzano l'elemento [\<summary\>](../ide/summary-javascript.md).  
  
 Utilizzare l'elemento `<value>` immediatamente prima della funzione `set` o `get`.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare l'elemento `<value>` in una funzione `get`.  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)