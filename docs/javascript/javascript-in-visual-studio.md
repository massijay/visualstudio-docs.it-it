---
title: JavaScript in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 77e7ce26df70e41e2328442454fe78c7a663f1f3
ms.openlocfilehash: de00ef86413571739446b61427c3a8e6c4680c06
ms.lasthandoff: 03/08/2017

---
# <a name="javascript-in-visual-studio"></a>JavaScript in Visual Studio
JavaScript è un ottimo linguaggio di Visual Studio. È possibile usare la maggior parte o tutti gli strumenti di modifica standard (frammenti di codice, IntelliSense e così via) quando si scrive codice JavaScript nell'IDE di Visual Studio. È possibile scrivere codice JavaScript per molti tipi di applicazioni e servizi.  
  
 Per la documentazione di riferimento del linguaggio JavaScript, vedere [JavaScript](https://docs.microsoft.com/scripting/javascript/javascript-language-reference).
  
 È possibile che vengano richieste versioni specifiche di Visual Studio o estensioni specifiche di Visual Studio per sviluppare determinati tipi di applicazioni e servizi con HTML e JavaScript. L'elenco seguente include i collegamenti ad altre informazioni.  
  
-   Per creare app multipiattaforma con Apache Cordova, vedere [Visual Studio Tools per Apache Cordova](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/).  
  
-   Per i collegamenti alle tecnologie di JavaScript che è possibile usare in Visual Studio, vedere le pagine [JavaScript](https://docs.microsoft.com/scripting/javascript/) e [Tecnologie di script](https://docs.microsoft.com/scripting/).
  
 L'editor JavaScript in Visual Studio fornisce il supporto IntelliSense. Per altre informazioni, vedere [IntelliSense per JavaScript](../ide/javascript-intellisense.md).  
  
## <a name="whats-new-in-javascript"></a>Novità in JavaScript  
 Nuove funzionalità per JavaScript sono elencate nella tabella seguente.  
  
|Funzionalità|Descrizione|  
|-------------|-----------------|  
|Classi|La nuova sintassi supporta la dichiarazione delle [classi](http://msdn.microsoft.com/Library/bf45ebad-4678-4062-88df-55d32b603c69).|  
|Suggerimenti|I [suggerimenti](http://msdn.microsoft.com/Library/358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6) consentono una codifica asincrona più semplice e chiara. I costruttori di suggerimenti sono supportati, con i metodi di utilità `all` e `race`.|  
|Iteratori|Ora è possibile scorrere gli oggetti iterabili (tra cui matrici, oggetti di tipo matrice e iteratori), richiamando un hook di iterazione personalizzato con istruzioni da eseguire per il valore di ogni singola proprietà. Per altre informazioni, vedere [Iteratori e Generatori](http://msdn.microsoft.com/Library/68ef5b2f-0349-492b-b557-73ff2a2f90cf). **Nota:** i generatori non sono ancora supportati.|  
|Funzioni freccia|La funzione freccia (=>) fornisce una sintassi abbreviata per la parola chiave `function` che offre un'associazione `this` lessicale.|  
|Nuovi metodi per gli oggetti predefiniti|Gli oggetti predefiniti [Array](http://msdn.microsoft.com/Library/08e5f552-0797-4b48-8164-609582fc18c9), [Math](http://msdn.microsoft.com/Library/607b94cb-921c-43cd-b514-fdbc13aeced6), [Number](http://msdn.microsoft.com/Library/76e87c37-cf6c-46cc-bafa-04be1fe3d78d), [Object](http://msdn.microsoft.com/Library/d24ef8fc-217b-4828-94e1-19f72780bae0) e [String](http://msdn.microsoft.com/Library/8063ecd5-5778-4e87-b985-b21420171914) includono diverse nuove proprietà e funzioni di utilità per la modifica e il controllo dei dati.|  
|Miglioramenti dei valori letterali di oggetto|Gli oggetti ora supportano proprietà calcolate, definizioni di metodo concise e sintassi abbreviata per le proprietà il cui valore viene inizializzato su una variabile con lo stesso nome. Per altre informazioni, vedere [Creazione di oggetti](http://msdn.microsoft.com/Library/58d1baa5-4fe8-4a56-a926-5b11765df704).|  
|Proxy|I [proxy](http://msdn.microsoft.com/Library/2b89abee-04fa-47e6-9676-980016cff5f8) abilitano il comportamento personalizzato per gli oggetti.|  
|Parametri rest|I parametri rest consentono di convertire in una matrice gli argomenti consecutivi in una chiamata di funzione. Per altre informazioni, vedere [Funzioni](http://msdn.microsoft.com/Library/e2a72b5a-3edd-43d8-95e8-91721b38c1c1).|  
|Operatore spread|L'[operatore spread](http://msdn.microsoft.com/Library/10263a4c-bd27-4d87-9917-fb4b6bf373db) (`…`) espande le espressioni iterabili in singoli argomenti. Ad esempio, `a.b(…array)` è quasi come `a.b.apply(a, array)`.|  
|Simboli|Gli oggetti [Symbol](http://msdn.microsoft.com/Library/2ad059f1-4b7f-4758-882a-c74ce1283ab0) consentono di aggiungere proprietà agli oggetti esistenti senza possibilità di interferenza con le proprietà di questi ultimi, senza alcuna visibilità imprevista e senza altre aggiunte non coordinate mediante altro codice.|  
|Stringhe modello|Le [stringhe modello](http://msdn.microsoft.com/Library/f2e525a5-b0fc-49c3-95a0-641788e5c12a) sono valori letterali stringa che consentono di valutare le espressioni e di concatenarle con il valore letterale stringa.|  
|Miglioramenti di Unicode|Sono stati apportati miglioramenti al supporto per Unicode. Ad esempio, un nuovo formato di sequenza di escape supporta i punti di codice "astrali" (punti di codice con più di quattro cifre esadecimali). Per altre informazioni, vedere [Caratteri speciali](http://msdn.microsoft.com/Library/3b38b1bd-1f0f-4748-b13e-55cab36fd126).|  
|WeakSet|Un [WeakSet](http://msdn.microsoft.com/Library/f97e6e7c-d678-4e32-978e-d949a7cafa3a) è una raccolta di oggetti che vengono sottoposti a Garbage Collection se non vi si fa riferimento in nessun altro punto.|
