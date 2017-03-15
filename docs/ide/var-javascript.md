---
title: "&lt;var&gt; (JavaScript) | Microsoft Docs"
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
  - "<var> (tag XML JavaScript)"
  - "var (tag XML JavaScript)"
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica le informazioni della documentazione relative a una variabile.  
  
## Sintassi  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>  
  
```  
  
#### Parametri  
 `type`  
 Parametro facoltativo.  Tipo di dati della variabile.  Il tipo può essere uno dei seguenti:  
  
-   Un linguaggio ECMAScript nella specifica di ECMAScript 5, come `Number` e `Object`.  
  
-   Un oggetto DOM, come `HTMLElement`, `Window` e `Document`.  
  
-   Una funzione costruttore JavaScript.  
  
 `integer`  
 Parametro facoltativo.  Se `type` è `Number`, specifica se la variabile è un integer.  Impostare a `true` per indicare che la variabile è un integer; in caso contrario, impostare a `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `domElement`  
 Parametro facoltativo.  Questo attributo è deprecato; l'attributo `type` ha la precedenza su questo attributo.  Questo attributo specifica se la variabile documentata è un elemento DOM.  Impostare a `true` per specificare che la variabile è un elemento DOM; in caso contrario, impostare su `false`.  Se l'attributo `type` non è impostato e `domElement` è impostato a `true`, l'IntelliSense considera la variabile documentata come un `HTMLElement` quando esegue il completamento delle istruzioni.  
  
 `mayBeNull`  
 Parametro facoltativo.  Specifica se la variabile documentata può essere impostata a null.  Impostare a `true` per indicare che la variabile può essere impostata a null; in caso contrario, impostare a `false`.  Il valore predefinito è `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementType`  
 Parametro facoltativo.  Se `type` è `Array`, questo attributo specifica il tipo degli elementi nell'array.  
  
 `elementInteger`  
 Parametro facoltativo.  Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nell'array sono integer.  Impostare a `true` per indicare che gli elementi nell'array sono integer; in caso contrario, impostare a `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementDomElement`  
 Parametro facoltativo.  Questo attributo è deprecato; l'attributo `elementType` ha la precedenza su questo attributo.  Se `type` è `Array`, questo attributo consente di specificare se gli elementi nell'array sono elementi DOM.  Impostare a `true` per specificare che gli elementi sono elementi DOM; in caso contrario, impostare su `false`.  Se l'attributo `elementType` non è impostato e `elementDomElement` è impostato a `true`, l'IntelliSense considera ogni elemento dell'array come `HTMLElement` quando esegue il completamento delle istruzioni.  
  
 `elementMayBeNull`  
 Parametro facoltativo.  Se `type` è `Array`, specifica se gli elementi nell'array possono essere impostati a null.  Impostare a `true` per indicare che gli elementi dell'array possono essere impostati a null; in caso contrario, impostare a `false`.  Il valore predefinito è `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `helpKeyword`  
 Parametro facoltativo.  La parola chiave per la guida richiamata tramite F1.  
  
 `locid`  
 Parametro facoltativo.  L'identificatore per le informazioni sulla localizzazione riguardo alla variabile.  L'identificatore è un membro ID o corrisponde al valore dell'attributo `name` in un gruppo di messaggi definiti dai metadati di OpenAjax.  Il tipo dell'identificatore dipende dal formato specificato nel tag [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Parametro facoltativo.  Una descrizione della variabile.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare l'elemento `<var>`.  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)