---
title: "Creare commenti JSDoc per IntelliSense per JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Creare commenti JSDoc per IntelliSense per JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense in Visual Studio visualizza le informazioni aggiunte a uno script tramite i commenti JSDoc standard.  È possibile usare i commenti JSDoc per fornire informazioni sugli elementi di codice, come funzioni, campi e variabili.  
  
## Tag di commento JSDoc  
 I tag di commento JSDoc standard elencati di seguito vengono usati da IntelliSense per visualizzare informazioni sul codice.  
  
|Tag JSDoc|Sintassi|Note|  
|---------------|--------------|----------|  
|@deprecated|@deprecated *descrizione*|Specifica una funzione o un metodo deprecato.|  
|@description|@description *descrizione*|Specifica la descrizione di una funzione o di un metodo.|  
|@param|@param {*tipo*} *nomeParametro**descrizione*|Specifica le informazioni relative a un parametro in una funzione o un metodo.<br /><br /> TypeScript supporta anche @paramTag.|  
|@property|@property {*tipo*} *nomeProprietà*|Specifica le informazioni, inclusa una descrizione, relative a un campo o a un membro definito per un oggetto.|  
|@returns|@returns {*tipo*}|Specifica un valore restituito.<br /><br /> Per TypeScript usare @returnType invece di @returns.|  
|@summary|@summary *descrizione*|Specifica la descrizione di una funzione o di un metodo \(uguale a @description\).|  
|@type|@type {*tipo*}|Specifica il tipo di una costante o di una variabile.|  
|@typedef|@typedef {*tipo*} *nomeTipoPersonalizzato*|Specifica un tipo personalizzato.|  
  
### Esempi  
 L'esempio seguente illustra l'uso dei tag @description, @param e @return di JSDoc per una funzione denominata `getArea`.  
  
```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  
  
 Nell'esempio precedente IntelliSense mostra le informazioni su descrizione, parametri e valori restituiti quando si digita la parentesi di apertura per `getArea`.  
  
 ![Informazioni di IntelliSense per una funzione](../ide/media/js_intellisense_jsdoc_comments.png "JS\_IntelliSense\_JSDoc\_Comments")  
  
 L'esempio seguente illustra come usare il tag @typedef con il tag @property.  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 L'esempio seguente illustra come usare i tag @type di JSDoc.  Come illustrato nell'esempio, gli asterischi singoli \(\*\) che seguono la coppia di asterischi iniziale \(\*\*\) non sono obbligatori.  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 L'esempio seguente illustra come usare il tag @deprecated di JSDoc.  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```