---
title: "Procedura: creare i commenti della documentazione XLM in JavaScript | Microsoft Docs"
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
  - "commenti del codice, IntelliSense per JavaScript"
  - "commenti di documentazione [JavaScript]"
  - "IntelliSense [JavaScript], commenti di documentazione XML"
  - "commenti di documentazione XML, IntelliSense per JavaScript"
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: creare i commenti della documentazione XLM in JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*I commenti di documentazione XML* sono JavaScript commenti aggiungere uno script per fornire informazioni sugli elementi di codice, ad esempio funzioni, campi e variabili.  In Visual Studio, queste descrizioni di testo vengono visualizzate con IntelliSense quando si fa riferimento la funzione di script.  
  
 In questo argomento viene illustrata un'esercitazione base sull'utilizzo di commenti di documentazione XML.  Per informazioni sull'utilizzo di altri elementi, ad esempio [\<var\>](../ide/var-javascript.md) e [\<value\>](../ide/value-javascript.md)e per ulteriori esempi di codice, vedere [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md).  Per informazioni su come fornire informazioni IntelliSense per una richiamata asincrona, ad esempio un `Promise`, vedere [\<returns\>](../ide/returns-javascript.md).  
  
> [!NOTE]
>  I commenti di documentazione XML sono disponibili solo dai servizi, gli assembly e file di riferimento.  
  
### Per creare i commenti di documentazione XML per una funzione JavaScript  
  
-   Aggiungere nella funzione, [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md), e [\<returns\>](../ide/returns-javascript.md) gli elementi e precedere ogni elemento con tre barre \(\/ \/ \/\).  
  
    > [!NOTE]
    >  Ogni elemento deve essere su una sola riga.  
  
     Nell'esempio riportato di seguito viene illustrata una funzione JavaScript.  
  
    ```javascript  
    function getArea(radius)  
    {  
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>  
        /// <param name="radius" type="Number">The radius of the circle.</param>  
        /// <returns type="Number">The area.</returns>  
        var areaVal;  
        areaVal = Math.PI * radius * radius;  
        return areaVal;  
    }  
    ```  
  
-   Per visualizzare i commenti di documentazione XML, digitare il nome e la parentesi di apertura di una funzione contrassegnata con i commenti di documentazione XML, come illustrato nell'esempio riportato di seguito:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     Quando si digita la parentesi di apertura della funzione che contiene i commenti di documentazione XML, Editor di codice utilizza IntelliSense per visualizzare le informazioni che sono definite nei commenti di documentazione XML.  
  
### Per creare i commenti di documentazione XML per un campo di JavaScript  
  
-   In una definizione di funzione o un oggetto costruttore, aggiungere una [\<field\>](../ide/field-javascript.md) elemento preceduto da tre barre \(\/ \/ \/\).  
  
     Nell'esempio riportato di seguito viene illustrato come utilizzare il `<field>` elemento in una funzione di costruzione.  Per ulteriori esempi, vedere [\<field\>](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   Per visualizzare i commenti di documentazione XML, creare un oggetto utilizzando il costruttore di funzione contrassegnata con i commenti di documentazione XML, come illustrato nell'esempio riportato di seguito.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   Nella riga successiva, digitare il nome dell'oggetto e un periodo per visualizzare le informazioni di IntelliSense per il campo.  
  
    ```javascript  
    eng.  
    ```  
  
### Per creare i commenti di documentazione XML per una funzione in overload  
  
1.  Nella funzione, aggiungere una [\<signature\>](../ide/signature-javascript.md) \(elemento\) per ogni overload.  Questi elementi, aggiungere altri elementi, ad esempio `<summary>`, `<param>`, e `<returns>`, precede ogni elemento con tre barre \(\/ \/ \/\).  
  
     Nell'esempio riportato di seguito viene illustrata una funzione JavaScript in overload.  In questo esempio, gli overload differiscono dal tipo di parametro.  
  
    ```javascript  
    function calc(a) {  
        /// <signature>  
        /// <summary>Function summary 1.</summary>  
        /// <param name="a" type="Number">A number.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        /// <signature>  
        /// <summary>Function summary 2.</summary>  
        /// <param name="a" type="String">A string.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        return a;  
    }  
    ```  
  
2.  Per visualizzare i commenti di documentazione XML, digitare il nome e la parentesi di apertura della funzione contrassegnata con i commenti di documentazione XML, come illustrato nell'esempio riportato di seguito:  
  
    ```javascript  
    calc(  
    ```  
  
### Per creare localizzati IntelliSense  
  
1.  Creare un file XML che contiene i commenti di documentazione nel formato OpenAjax MessageBundle.  
  
    > [!IMPORTANT]
    >  MessageBundle è il formato consigliato.  Questo formato non è supportato in Microsoft Ajax o nei file .winmd.  Per informazioni sull'utilizzo dell'alternativa `VSDoc` di formato, vedere [\<loc\>](../ide/loc-javascript.md).  
  
     L'esempio seguente Mostra contenuto in un file collaterali che contiene le informazioni IntelliSense localizzate.  Si tratta di un file XML che si trova in una cartella di specifiche della lingua, ad esempio JA.  La cartella deve trovarsi nella stessa posizione del file con estensione js che contiene la `<loc>` elemento.  Il nome di file del file XML deve corrispondere il `filename` parametro specificato nel `<loc>` elemento.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  Nel file con estensione js, aggiungere il codice riportato di seguito.  Il `<loc>` elemento deve essere dichiarato prima tutti gli script e segue le stesse regole di utilizzo di `<reference>` elemento.  Per ulteriori informazioni, vedere [IntelliSense per JavaScript](../ide/javascript-intellisense.md) e [\<loc\>](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  Nel file con estensione js, aggiungere gli elementi di documentazione XML e le descrizioni di default.  Impostare il `locid` i valori in modo che corrisponda alla corrispondente dell'attributo `name` i valori degli attributi del file collaterale.  Le descrizioni di default verranno sostituite da informazioni IntelliSense localizzate, se è disponibile.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  Per visualizzare i commenti di documentazione XML, digitare il nome e la parentesi di apertura della funzione, come illustrato nell'esempio riportato di seguito:  
  
    ```javascript  
    add(  
    ```  
  
## Vedere anche  
 [IntelliSense per JavaScript](../ide/javascript-intellisense.md)   
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Walkthrough: JavaScript IntelliSense in ASP.NET](http://msdn.microsoft.com/it-it/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
