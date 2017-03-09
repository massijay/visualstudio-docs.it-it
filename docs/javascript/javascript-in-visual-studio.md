---
title: "JavaScript in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# JavaScript in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript è un ottimo linguaggio di Visual Studio.  È possibile usare la maggior parte o tutti gli strumenti di modifica standard \(frammenti di codice, IntelliSense e così via\) quando si scrive codice JavaScript nell'IDE di Visual Studio.  È possibile scrivere codice JavaScript per molti tipi di applicazioni e servizi.  
  
 Per la documentazione di riferimento del linguaggio JavaScript, vedere [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).  
  
 È possibile che vengano richieste versioni specifiche di Visual Studio o estensioni specifiche di Visual Studio per sviluppare determinati tipi di applicazioni e servizi con HTML e JavaScript.  L'elenco seguente include i collegamenti ad altre informazioni.  
  
-   Per creare app multipiattaforma con Apache Cordova, [scaricare Visual Studio Tools per Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).  
  
-   Per creare app di [Windows Store](http://dev.windows.com/develop), [Windows Phone](http://dev.windows.com/develop) e app universali \(che supportano entrambe le piattaforme\), [scaricare gli strumenti](http://dev.windows.com/en-us/develop/downloads).  
  
-   Per creare servizi basati su cloud, vedere il [sito di Microsoft Azure](http://azure.microsoft.com/documentation/).  
  
-   Per creare siti Web e app Web, [visitare il sito ASP.NET](http://www.asp.net/get-started/websites).  
  
    > [!NOTE]
    >  È possibile creare un sito Web ASP.NET vuoto e usarlo per la programmazione HTML, CSS e JavaScript.  Il file Webconfig fornito da ASP.NET consente il debug in Visual Studio \(o è possibile usare gli strumenti F12 quando si esegue l'app\).  
  
 L'editor JavaScript in Visual Studio fornisce il supporto IntelliSense.  Per altre informazioni, vedere [IntelliSense per JavaScript](../ide/javascript-intellisense.md).  
  
## Novità in JavaScript  
 Nuove funzionalità per JavaScript sono elencate nella tabella seguente.  
  
|Funzionalità|Descrizione|  
|------------------|-----------------|  
|Classi|La nuova sintassi supporta la dichiarazione delle [classi](../Topic/class%20Statement%20\(JavaScript\).md).|  
|Suggerimenti|I [suggerimenti](../Topic/Promise%20Object%20\(JavaScript\).md) consentono una codifica asincrona più semplice e chiara.  I costruttori di suggerimenti sono supportati, con i metodi di utilità `all` e `race`.|  
|Iteratori|Ora è possibile scorrere gli oggetti iterabili \(tra cui matrici, oggetti di tipo matrice e iteratori\), richiamando un hook di iterazione personalizzato con istruzioni da eseguire per il valore di ogni singola proprietà.  Per altre informazioni, vedere [Iteratori e generatori](../Topic/Iterators%20and%20Generators%20\(JavaScript\).md). **Note:**  I generatori non sono ancora supportati.|  
|Funzioni freccia|La funzione freccia \(\=\>\) fornisce una sintassi abbreviata per la parola chiave `function` che offre un'associazione `this` lessicale.|  
|Nuovi metodi per gli oggetti predefiniti|Gli oggetti predefiniti [Oggetto Array](../Topic/Array%20Object%20\(JavaScript\).md), [Oggetto Math](../Topic/Math%20Object%20\(JavaScript\).md), [Oggetto Number](../Topic/Number%20Object%20\(JavaScript\).md), [Oggetto Object](../Topic/Object%20Object%20\(JavaScript\).md) e [Oggetto String](../Topic/String%20Object%20\(JavaScript\).md) includono diverse nuove proprietà e funzioni di utilità per la modifica e il controllo dei dati.|  
|Miglioramenti dei valori letterali degli oggetti|Gli oggetti ora supportano proprietà calcolate, definizioni di metodo concise e sintassi abbreviata per le proprietà il cui valore viene inizializzato su una variabile con lo stesso nome.  Per altre informazioni, vedere [Creazione di oggetti](../Topic/Creating%20Objects%20\(JavaScript\).md).|  
|Proxy|I [proxy](../Topic/Proxy%20Object%20\(JavaScript\).md) consentono il comportamento personalizzato per gli oggetti.|  
|Parametri rest|I parametri rest consentono di convertire in una matrice gli argomenti consecutivi in una chiamata di funzione.  Per altre informazioni, vedere [Funzioni](../Topic/Functions%20\(JavaScript\).md).|  
|Operatore spread|L'[operatore spread](../Topic/Spread%20Operator%20\(...\)%20\(JavaScript\).md) \(`…`\) espande le espressioni iterabili in singoli argomenti.  Ad esempio, `a.b(…array)` è quasi come `a.b.apply(a, array)`.|  
|Simboli|Gli oggetti [Symbol](../Topic/Symbol%20Object%20\(JavaScript\).md) consentono di aggiungere proprietà agli oggetti esistenti senza possibilità di interferenza con le proprietà degli oggetti esistenti, senza alcuna visibilità imprevista e senza altre aggiunte non coordinate mediante un altro codice.|  
|Stringhe modello|Le [stringhe modello](../Topic/Template%20Strings%20\(JavaScript\).md) sono valori letterali stringa che consentono di valutare le espressioni e di concatenarle con il valore letterale stringa.|  
|Miglioramenti di Unicode|Sono stati apportati miglioramenti al supporto per Unicode.  Ad esempio, un nuovo formato di sequenza di escape supporta i punti di codice "astrali" \(punti di codice con più di quattro cifre esadecimali\).  Per altre informazioni, vedere [Caratteri speciali](../Topic/Special%20Characters%20\(JavaScript\).md).|  
|WeakSet|Un [WeakSet](../Topic/WeakSet%20Object%20\(JavaScript\).md) è una raccolta di oggetti che verranno sottoposti a Garbage Collection se non vi si fa riferimento in nessun altro punto.|