---
title: "&lt;loc&gt; (JavaScript) | Microsoft Docs"
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
  - "<loc> (tag XML JavaScript)"
  - "loc (tag XML JavaScript)"
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica la posizione e il tipo del file collaterale che fornisce informazioni IntelliSense localizzate.  
  
## Sintassi  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### Parametri  
 `filename`  
 Parametro facoltativo.  Il nome radice del file collaterale contenente le informazioni di localizzazione per le impostazioni cultura non associate ad alcun paese.  Quando Visual Studio cerca informazioni di localizzazione, tenta di trovare una versione specifica delle impostazioni cultura di questo file.  Ad esempio, se `filename` è jquery.xml, Visual Studio cerca la cartella specifica delle impostazioni cultura corretta \(come JA\) nella stessa posizione del file .js che contiene l'elemento `<loc>`.  Se individua la cartella specifica delle impostazioni cultura, controlla se al suo interno esiste un file jquery.xml.  Se non è possibile individuare il file corretto, utilizzare invece le regole di locazione della risorsa gestita.  Il valore predefinito per `filename` è il nome del file corrente, ma con estensione .xml anziché .js.  
  
 `format`  
 Parametro facoltativo.  Il tipo di file collaterale utilizzato per la localizzazione.  Utilizzare `messagebundle` per specificare l'utilizzo di gruppi di messaggio definiti dai metadati Open AJAX.  `messagebundle` è il formato consigliato.  Tuttavia, questo formato non è supportato in Microsoft AJAX o in file .winmd.  Utilizzare `vsdoc` per specificare il formato di localizzazione standard di .NET Framework utilizzato da Microsoft Ajax e Windows Runtime.  L'attributo è facoltativo.  `vsdoc` è il formato predefinito.  
  
## Note  
 L'elemento `<loc>` deve trovarsi all'inizio del file nella stessa sezione dell'elemento `<reference>`.  Le regole di utilizzo per l'elemento `<loc>` sono le stesse dell'elemento `<reference>`.  Per ulteriori informazioni, vedere la sezione "Direttive References" in [IntelliSense per JavaScript](../ide/javascript-intellisense.md).  
  
 Visual Studio processa un singolo elemento `<loc>` per ogni file .js.  Se più elementi `<loc>` sono presenti, solo un singolo elemento `<loc>` viene utilizzato.  Il comportamento per determinare quale elemento `<loc>` utilizzare non è definito.  
  
 Quando si utilizza il formato del gruppo di messaggi, utilizzare l'attributo `locid` nei commenti della documentazione XML per specificare il valore dell'attributo `name`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare l'elemento `<loc>` con il formato messagebundle.  Aggiungere il seguente codice XML in un file denominato messageFilename.xml e posizionarlo nella corretta cartella specifica delle impostazioni cultura, come specificato nella descrizione del parametro `filename`.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Per l'esempio di messagebundle, aggiungere il seguente codice ad un file JavaScript nel progetto.  L'elemento `<loc>` deve apparire come prima riga nel file JavaScript.  Le descrizioni in questo codice vengono sostituite dalle descrizioni localizzate, se disponibili.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 Nell'esempio seguente viene utilizzato il formato VSDoc.  Aggiungere il seguente codice XML in un file denominato scriptFilename.xml e posizionarlo nella corretta cartella specifica delle impostazioni cultura.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<doc>  
  <assembly>  
    <name>Lights</name>  
  </assembly>  
  <members>  
    <member name="M:illuminate">  
      <summary>Activates a light. </summary>  
      <param name='a'>The light to activate. </param>  
    </member>  
  </members>  
</doc>  
  
```  
  
 Per l'esempio VSDoc, aggiungere il seguente codice ad un file JavaScript nel progetto.  Le descrizioni in questo codice vengono sostituite dalle descrizioni localizzate, se disponibili.  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)