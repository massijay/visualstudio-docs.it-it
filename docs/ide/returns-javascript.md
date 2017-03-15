---
title: "&lt;returns&gt; (JavaScript) | Microsoft Docs"
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
  - "returns (tag XML JavaScript)"
  - "<returns> (tag XML JavaScript)"
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica le informazioni della documentazione relative al risultato di una chiamata ad una funzione o metodo.  
  
## Sintassi  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### Parametri  
 `type`  
 Parametro facoltativo.  Tipo di dati del valore restituito.  Il tipo può essere uno dei seguenti:  
  
-   Un linguaggio ECMAScript nella specifica di ECMAScript 5, come `Number` e `Object`.  
  
-   Un oggetto DOM, come `HTMLElement`, `Window` e `Document`.  
  
-   Una funzione costruttore JavaScript.  
  
 `integer`  
 Parametro facoltativo.  Se `type` è `Number`, specifica se il valore restituito è un integer.  Impostare a `true` per indicare che il valore restituito è un intero; in caso contrario, impostare su `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `domElement`  
 Parametro facoltativo.  Questo attributo è deprecato; l'attributo `type` ha la precedenza su questo attributo.  Questo attributo specifica se il valore restituito documentato è un elemento DOM.  Impostare a `true` per specificare che il valore restituito è un elemento DOM; in caso contrario, impostare su `false`.  Se l'attributo `type` non è impostato e `domElement` è impostato su `true`, l'IntelliSense considera il valore restituito documentato come un `HTMLElement` quando esegue il completamento delle istruzioni.  
  
 `mayBeNull`  
 Parametro facoltativo.  Specifica se il valore restituito documentato può essere impostato a null.  Impostare a `true` per indicare che il valore restituito può essere impostato a null; in caso contrario, impostare su `false`.  Il valore predefinito è `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementType`  
 Parametro facoltativo.  Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.  
  
 `elementInteger`  
 Parametro facoltativo.  Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono interi.  Impostare a `true` per indicare che gli elementi nella matrice sono numeri interi; in caso contrario, impostare su `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementDomElement`  
 Parametro facoltativo.  Questo attributo è deprecato; l'attributo `elementType` ha la precedenza su questo attributo.  Se `type` è `Array`, questo attributo consente di specificare se gli elementi nella matrice sono elementi DOM.  Impostare a `true` per specificare che gli elementi sono elementi DOM; in caso contrario, impostare su `false`.  Se l'attributo `elementType` non è impostato e `elementDomElement` su `true`, l'IntelliSense considera ogni elemento della matrice come `HTMLElement` quando esegue il completamento delle istruzioni.  
  
 `elementMayBeNull`  
 Parametro facoltativo.  Se `type` è `Array`, specifica se gli elementi nella matrice possono essere impostati a null.  Impostare a `true` per indicare che gli elementi della matrice possono essere impostati a null; in caso contrario, impostare su `false`.  Il valore predefinito è `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `locid`  
 Parametro facoltativo.  L'identificatore per informazioni di localizzazione sul valore restituito.  L'identificatore è un membro ID o corrisponde al valore dell'attributo `name` in un gruppo di messaggi definiti dai metadati di OpenAjax.  Il tipo dell'identificatore dipende dal formato specificato nel tag [\<loc\>](../ide/loc-javascript.md).  
  
 `value`  
 Parametro facoltativo.  Specifica il codice che deve essere valutato per essere utilizzato da IntelliSense anziché dal codice stesso della funzione.  Ad esempio, è possibile utilizzare questo attributo per fornire IntelliSense per le callbacks asincrone, come `Promise`.  Mediante l'attributo `value` con l'elemento `<returns>` può migliorare le prestazioni di IntelliSense ignorando la lunga esecuzione di codice.  
  
 `description`  
 Parametro facoltativo.  Descrizione del valore restituito.  
  
## Note  
 L'elemento `<returns>` deve essere inserito nel corpo della funzione prima delle istruzioni.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare l'elemento `<returns>`.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
// The following examples use the <remarks> element with a value attribute.  
  
function getJson(complete) {   
    /// <returns value='complete("")' ></returns>  
    var r = new XMLHttpRequest();   
    // . . .   
}   
  
getJson(function (json) {   
    json.  // IntelliSense for a String object is   
           // available here.  
});  
  
function calculate(x) {  
    /// <returns value='1'/>  
}  
calculate().  // Completion list for a Number.  
  
```  
  
## Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)