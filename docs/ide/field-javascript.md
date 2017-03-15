---
title: "&lt;field&gt; (JavaScript) | Microsoft Docs"
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
  - "<field> (tag XML JavaScript)"
  - "field (tag XML JavaScript)"
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica le informazioni della documentazione, inclusa una descrizione, per un campo o un membro definito in un oggetto.  
  
## Sintassi  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### Parametri  
 `name`  
 Il nome del campo o del membro.  Quando l'elemento `<field>` viene utilizzato in una funzione costruttore, `name` è obbligatorio e definisce il membro a cui il tag viene applicato.  Quando l'elemento `<field>` sta direttamente annotando un campo, questo attributo viene ignorato e il nome utilizzato da Visual Studio è il nome del campo nel codice sorgente.  
  
 `static`  
 Parametro facoltativo.  Specifica se il campo è un membro della funzione costruttore o un membro dell'oggetto restituito dalla funzione costruttore.  Impostato a `true`, considera il campo come membro della funzione costruttore.  Impostato a `false`, considera il campo come membro dell'oggetto restituito dalla funzione costruttore.  
  
 `type`  
 Parametro facoltativo.  Tipo di dati del campo.  Il tipo può essere uno dei seguenti:  
  
-   Un linguaggio ECMAScript nella specifica di ECMAScript 5, come `Number` e `Object`.  
  
-   Un oggetto DOM, come `HTMLElement`, `Window` e `Document`.  
  
-   Una funzione costruttore JavaScript.  
  
 `integer`  
 Parametro facoltativo.  Se `type` è `Number`, specifica se il campo è un integer.  Impostare a `true` per indicare che il campo è un integer; in caso contrario, impostare a `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `domElement`  
 Parametro facoltativo.  Questo attributo è deprecato; l'attributo `type` ha la precedenza su questo attributo.  Questo attributo specifica se il campo documentato è un elemento DOM.  Impostare a `true` per specificare che il campo è un elemento DOM; in caso contrario, impostare su `false`.  Se l'attributo `type` non è impostato e `domElement` è impostato a `true`, l'IntelliSense considera il campo documentato come un `HTMLElement` quando esegue il completamento delle istruzioni.  
  
 `mayBeNull`  
 Parametro facoltativo.  Specifica se il campo documentato può essere impostato a null.  Impostare a `true` per indicare che il campo può essere impostato a null; in caso contrario, impostare a `false`.  Il valore predefinito è `false`.  Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
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
 Parametro facoltativo.  L'identificatore per le informazioni sulla localizzazione riguardo al campo.  L'identificatore è un membro ID o corrisponde al valore dell'attributo `name` in un gruppo di messaggi definiti dai metadati di OpenAjax.  Il tipo dell'identificatore dipende dal formato specificato nel tag [\<loc\>](../ide/loc-javascript.md).  
  
 `value`  
 Parametro facoltativo.  Specifica il codice che deve essere valutato per essere utilizzato da IntelliSense anziché dal codice stesso della funzione.  Per `<field>`, questo attributo è supportato per le funzioni costruttore, ma non è supportato per i valori letterali di oggetto.  È possibile utilizzare questo attributo per fornire le informazioni sul tipo quando il tipo del campo non è definito.  Ad esempio, è possibile utilizzare `value=’1’` per considerare il tipo del campo come numero.  
  
 `description`  
 Parametro facoltativo.  Descrizione del campo.  
  
## Note  
 L'attributo `name` è obbligatorio quando si sta effettuando la documentazione di un campo di una funzione costruttore.  Per tutti gli altri scenari, tutti gli attributi per l'elemento `<field>` sono facoltativi.  
  
 Quando si sta effettuando la documentazione di una funzione costruttore, l'elemento `<field>` deve trovarsi subito prima della dichiarazione del campo.  L'attributo `name` deve corrispondere al nome del campo utilizzato nel codice sorgente.  Per i membri dell'oggetto, l'attributo `name` può essere omesso se l'elemento `<field>` appare immediatamente prima della dichiarazione del membro dell'oggetto.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare l'elemento `<field>`.  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare l'attributo `<field>`, con l'attributo `static` impostato a `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare l'attributo `<field>`, con l'attributo `static` impostato a `false`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare l'elemento `<field>` con l'attributo `value`.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)