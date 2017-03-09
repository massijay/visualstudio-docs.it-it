---
title: "&lt;param&gt; (JavaScript) | Microsoft Docs"
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
  - "<param> (tag XML JavaScript)"
  - "param (tag XML JavaScript)"
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica le informazioni della documentazione per un parametro di una funzione o di un metodo.  
  
## Sintassi  
  
```  
<param name="parameterName" type="ParameterType"  
    integer="true|false" domElement="true|false"  
    mayBeNull="true|false" elementType="ArrayElementType"  
    elementInteger="true|false" elementDomElement="true|false"  
    elementMayBeNull="true|false" locid="descriptionID"  
    parameterArray="true|false" optional="true|false"  
    value="code">description  
</param>  
```  
  
#### Parametri  
 `name`  
 Obbligatorio.  Nome del parametro.  
  
 `type`  
 Parametro facoltativo.  Tipo di dati del parametro.  Il tipo può essere uno dei seguenti:  
  
-   Un linguaggio ECMAScript nella specifica di ECMAScript 5, come `Number` e `Object`.  
  
-   Un oggetto DOM, come `HTMLElement`, `Window` e `Document`.  
  
-   Una funzione costruttore JavaScript.  
  
 `integer`  
 Parametro facoltativo.  Se `type` è `Number`, specifica se il parametro è un integer.  Impostare a `true` per indicare che il parametro è un integer; in caso contrario, impostare a `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `domElement`  
 Parametro facoltativo.  Questo attributo è deprecato; l'attributo `type` ha la precedenza su questo attributo.  Questo attributo specifica se il parametro documentato è un elemento DOM.  Impostare a `true` per specificare che il parametro è un elemento DOM; in caso contrario, impostare su `false`.  Se l'attributo `type` non è impostato e `domElement` è impostato a `true`, l'IntelliSense considera il parametro documentato come un `HTMLElement` quando esegue il completamento delle istruzioni.  
  
 `mayBeNull`  
 Parametro facoltativo.  Specifica se il parametro documentato può essere impostato a null.  Impostare a `true` per indicare che il parametro può essere impostato a null; in caso contrario, impostare a `false`.  Il valore predefinito è `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementType`  
 Parametro facoltativo.  Se `type` è `Array`, questo attributo specifica il tipo degli elementi nell'array.  
  
 `elementInteger`  
 Parametro facoltativo.  Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nell'array sono integer.  Impostare a `true` per indicare che gli elementi nell'array sono integer; in caso contrario, impostare a `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementDomElement`  
 Parametro facoltativo.  Questo attributo è deprecato; l'attributo `elementType` ha la precedenza su questo attributo.  Se `type` è `Array`, questo attributo consente di specificare se gli elementi nell'array sono elementi DOM.  Impostare a `true` per specificare che gli elementi sono elementi DOM; in caso contrario, impostare su `false`.  Se l'attributo `elementType` non è impostato e `elementDomElement` è impostato a `true`, l'IntelliSense considera ogni elemento dell'array come `HTMLElement` quando esegue il completamento delle istruzioni.  
  
 `elementMayBeNull`  
 Parametro facoltativo.  Se `type` è `Array`, specifica se gli elementi nell'array possono essere impostati a null.  Impostare a `true` per indicare che gli elementi dell'array possono essere impostati a null; in caso contrario, impostare a `false`.  Il valore predefinito è `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `locid`  
 Parametro facoltativo.  L'identificatore per le informazioni sulla localizzazione riguardo al parametro.  L'identificatore è un membro ID o corrisponde al valore dell'attributo `name` in un gruppo di messaggi definiti dai metadati di OpenAjax.  Il tipo dell'identificatore dipende dal formato specificato nell'elemento [\<loc\>](../ide/loc-javascript.md).  
  
 `parameterArray`  
 Parametro facoltativo.  Specifica se il parametro documentato può essere ripetuto nella chiamata di funzione, in modo simile alla ripetizione dei parametri di supporto nella funzione `String.format`.  Impostare a `true` per indicare che il parametro può essere ripetuto; in caso contrario, impostare a `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `optional`  
 Parametro facoltativo.  Specifica se il parametro documentato è facoltativo nella funzione chiamante.  Impostare a `true` per indicare che il parametro è facoltativo; in caso contrario, impostare a `false`.  
  
 `value`  
 Parametro facoltativo.  Specifica il codice che deve essere valutato per essere utilizzato da IntelliSense anziché dal codice stesso della funzione.  È possibile utilizzare questo attributo per fornire le informazioni sul tipo quando il tipo del parametro non è definito.  Ad esempio, è possibile utilizzare `value=’1’` per considerare il tipo del parametro come numero.  
  
 `description`  
 Parametro facoltativo.  Una descrizione del parametro.  
  
## Note  
 L'unico attributo obbligatorio è `name`.  Tutti gli altri attributi sono facoltativi.  
  
 Gli elementi utilizzati per annotare le funzioni, come [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md) e [\<returns\>](../ide/returns-javascript.md), devono essere inseriti nel corpo della funzione prima delle istruzioni.  
  
 Se sono presenti più elementi `<param>` con lo stesso nome, uno degli elementi `<param>` viene utilizzato ed elementi ridondanti vengono ignorati.  Il comportamento che determina quale elemento viene utilizzato non è definito.  Se `name` si riferisce a un parametro non esistente, l'elemento viene ignorato.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare l'elemento `<param>`.  
  
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
  
// Uses of <param> with the value attribute.  
  
function calculate(a) {  
    /// <param name='a' value='1'/>  
    a.    // Completion list for a Number.  
}  
  
function calculate(a) {  
    /// <param name='a' value='{x:0,y:0}'/>  
    a.    // x and y appear in the completion list.  
}  
  
```  
  
## Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)