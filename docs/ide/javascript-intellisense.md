---
title: IntelliSense per JavaScript |Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 63
author: mikejo
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
ms.sourcegitcommit: d07820eda0d76163d99d7752789750eaf56182fd
ms.openlocfilehash: 1f8372fe201d6b23ee2c65e0f6d6a2fa28976654
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-intellisense"></a>IntelliSense per JavaScript
[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] offre funzionalità di modifica complete di JavaScript, implementabili all'istante. Visual Studio, gestito da un servizio di linguaggio basato su TypeScript, offre una modalità IntelliSense più completa, il supporto di funzionalità JavaScript aggiornate e funzioni di produttività migliorate quali Vai a definizione, il refactoring e altro ancora.

> [!NOTE]
>  Il servizio di linguaggio JavaScript in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] usa un nuovo motore ("Salsa"). I dettagli sono inclusi più avanti in questo argomento. Può anche essere utile leggere [questo post di blog](https://blogs.msdn.microsoft.com/visualstudio/2016/04/08/previewing-salsa-javascript-language-service-visual-studio-15/). Le nuove funzioni di modifica si applicano principalmente a Visual Studio Code. Per altre informazioni vedere la [documentazione di Visual Studio Code](https://code.visualstudio.com/docs/languages/javascript).

Per altre informazioni sulla funzionalità IntelliSense generale di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], vedere [Uso di IntelliSense](../ide/using-intellisense.md). 

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Novità del servizio di linguaggio JavaScript in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

- Funzionalità IntelliSense più completa

    JavaScript IntelliSense in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ora visualizza più informazioni relative agli elenchi di parametri e membri.
Le nuove informazioni sono specificate dal servizio di linguaggio TypeScript, che usa l'analisi statica in background per un'interpretazione più approfondita del codice.
Per ottenere le informazioni necessarie, TypeScript usa diverse fonti.
    - [IntelliSense basato sull'inferenza del tipo](#TypeInference)
    - [IntelliSense basato su JSDoc](#JsDoc)
    - [IntelliSense basato su file dichiarazione TypeScript](#TSDeclFiles)

- [Acquisizione automatica delle definizioni dei tipi](#Auto)
- [Supporto di ES6 e altro ancora](#ES6)
- [Supporto della sintassi JSX](#JSX)

## <a name="TypeInference"></a>IntelliSense basato sull'inferenza del tipo
In JavaScript nella maggior parte dei casi non sono disponibili informazioni esplicite relative ai tipi. In genere è abbastanza semplice dedurre un tipo usando come contesto il codice circostante.
Questo processo è detto inferenza del tipo.

Per una variabile o una proprietà, il tipo è in genere il tipo del valore usato per l'inizializzazione oppure l'assegnazione di un valore più recente. 

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Per una funzione, il tipo restituito può essere dedotto dalle istruzioni return. 

Per i parametri di funzione l'inferenza non è attualmente disponibile, ma è possibile risolvere il problema mediante i file `.d.ts` JSDoc o TypeScript (vedere le sezioni successive).

È anche disponibile una funzionalità di inferenza speciale per i seguenti elementi:
 - Classi "in stile ES3", specificate mediante una funzione costruttore e assegnazioni alla proprietà prototype.
 - Modelli di modulo in stile CommonJS, specificati come assegnazioni di proprietà nell'oggetto `exports` oppure assegnazioni alla proprietà `module.exports`.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

## <a name="JsDoc"></a> IntelliSense basato su JSDoc

Quando l'inferenza del tipo non specifica le informazioni sul tipo desiderate (o si vuole aggiungere supporto alla documentazione), è possibile includere informazioni sul tipo in modo esplicito tramite le annotazioni JSDoc.  Ad esempio, per assegnare un tipo specifico a un oggetto parzialmente dichiarato si può usare il tag `@type` come illustrato di seguito:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Come detto, l'inferenza non è mai valida per i parametri funzione. Tuttavia con il tag JSDoc `@param` è possibile aggiungere tipi anche ai parametri funzione. 

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```
 
Vedere in [questo documento](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) le annotazioni JsDoc attualmente supportate.

## <a name="TsDeclFiles"></a> IntelliSense basato su file dichiarazione TypeScript

Dato che ora JavaScript e TypeScript si basano sullo stesso servizio di linguaggio, sono in grado di interagire in modo più completo. Ad esempio è possibile aggiungere codice IntelliSense JavaScript per i valori dichiarati in un file `.d.ts` ([altre informazioni](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Writing%20Definition%20Files.md)), mentre i tipi quali interfacce e classi dichiarate in TypeScript sono disponibili per l'uso come tipi nei commenti JsDoc. 

Di seguito viene visualizzato un esempio semplice di file di definizione TypeScript che specifica questo tipo di informazioni (attraverso un'interfaccia) a un file JavaScript nello stesso progetto (mediante un tag JsDoc).

_**Dichiarazioni TypeScript usate in JavaScript**_

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

## <a name="Auto"></a> Acquisizione automatica delle definizioni dei tipi
Nell'ambito TypeScript, le API delle librerie JavaScript più diffuse sono descritte da file `.d.ts` e il repository più comune per tali definizioni si trova in [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Per impostazione predefinita il servizio di linguaggio Salsa prova a rilevare le librerie JavaScript in uso, quindi scarica e crea automaticamente un riferimento al file `.d.ts` corrispondente che descrive la libreria, al fine di fornire un'esecuzione IntelliSense più completa. I file vengono scaricati in una cache posta all'interno della cartella dell'utente in `%LOCALAPPDATA%\Microsoft\TypeScript`. 

> [!NOTE]
> Questa funzionalità è **disattivata** per impostazione predefinita se si usa un file di configurazione `tsconfig.json`, ma può essere impostata come attivata con le modalità descritte di seguito.

Attualmente il rilevamento automatico funziona per le dipendenze scaricate da npm (mediante la lettura del file `package.json`), Bower (mediante la lettura del file `bower.json`) e per singoli file del progetto corrispondenti a un elenco contenente circa 400 tra le librerie JavaScript più diffuse. Se ad esempio nel progetto è presente `jquery-1.10.min.js`, verrà recuperato e caricato il file `jquery.d.ts` per garantire una funzionalità di modifica più completa. Tale file `.d.ts` non avrà alcun impatto sul progetto. 

Se non si vuole usare l'acquisizione automatica, disattivarla mediante l'aggiunta di un file di configurazione, come descritto di seguito. È comunque possibile inserire manualmente file di definizione da usare direttamente nel progetto.

## <a name="ES6"></a> Supporto di ES6 e altro ancora

ES6 o ECMAScript 2015 è la versione successiva di JavaScript. Questa versione apporta nuovi elementi di sintassi al linguaggio, quali le classi, le funzioni freccia, `let`/`const` e altro ancora. Tutta la nuova sintassi è supportata in Visual Studio.

Una delle caratteristiche chiave fornite da TypeScript è la possibilità di usare funzionalità ES6 e generare codice eseguibile in runtime di JavaScript che non sono ancora in grado di interpretare queste funzionalità recenti. Questa caratteristica è nota come "transpiling". Dato che JavaScript usa lo stesso servizio di linguaggio, può a sua volta avvalersi del transpiling da ES6 e versioni successive a ES5.

Prima di configurare questa funzionalità è necessario un approfondimento relativo alle opzioni di configurazione.  TypeScript viene configurato tramite un file `tsconfig.json`. In assenza di tale file vengono usati alcuni valori predefiniti. Per motivi di compatibilità, tali valori predefiniti sono diversi in un contesto che include solo file JavaScript (e facoltativamente file `.d.ts`). Per la compilazione dei file JavaScript è necessario aggiungere un file `tsconfig.json` e quindi impostare in modo esplicito alcuni di questi valori predefiniti.

Le impostazioni necessarie per il file tsconfig sono descritte di seguito:

 - `allowJs`: per il riconoscimento dei file JavaScript, questo valore deve essere impostato su `true`.
L'impostazione predefinita è `false` perché TypeScript esegue la compilazione in JavaScript e tale impostazione è necessaria per evitare che il compilatore includa i file che ha appena compilato.
 - `outDir`: questa opzione deve essere impostata su un percorso non incluso nel progetto, in modo che i file JavaScript generati non vengano rilevati e quindi inclusi a loro volta nel progetto (vedere `exclude` di seguito).
 - `module`: se si usano i moduli, questa impostazione indica al compilatore il formato di modulo usato dal codice generato (ad esempio `commonjs` per Node o bundler come Browserify).
 - `exclude`: questa impostazione indica le cartelle da non includere nel progetto. 
 Aggiungere a questa impostazione il percorso di output e le cartelle non di progetto, quali `node_modules` o `temp`.
 - `enableAutoDiscovery`: questa impostazione consente il rilevamento e il download automatico dei file di definizione come descritto in precedenza.
 - `compileOnSave`: questa impostazione indica al compilatore se è necessario ricompilare quando un file di origine viene salvato in Visual Studio.

Per la conversione di file JavaScript in moduli CommonJS in una cartella `./out`, un file `tsconfig.json` può includere impostazioni come la seguente.

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typingOptions": {
    "enableAutoDiscovery": true
  }
}
```

Si supponga che le impostazioni precedenti siano attivate e che esista un file di origine (`./app.js`) contenente varie funzionalità del linguaggio ECMAScript 2015, come illustrato di seguito:

```js
import {Subscription} from 'rxjs/Subscription';

class Foo {
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;
    }
}

export let sqr = x => x * x;
export default Subscription;
```

Il risultato è la creazione in `./out/app.js` di un file ECMAScript 5 (impostazione predefinita) e con un aspetto simile al seguente:

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
//# sourceMappingURL=app.js.map
```

## <a name="JSX"></a> Supporto della sintassi JSX

JavaScript in Visual Studio 2017 offre un supporto dettagliato della sintassi JSX. JSX è un set di sintassi che consente la presenza di tag HTML nei file JavaScript. 

L'illustrazione che segue visualizza un componente React definito nel file TypeScript `comps.tsx`, quindi visualizza tale componente usato dal file `app.jsx` e provvisto di IntelliSense per il completamento e la documentazione all'interno delle espressioni JSX.
Qui non è necessario aggiungere codice TypeScript, perché casualmente l'esempio contiene già codice TypeScript.
<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/react.png" height="500" width="640"/>

> [!NOTE]
> Per convertire la sintassi JSX in chiamate React è necessario aggiungere l'impostazione `"jsx": "react"` a `compilerOptions` nel file `tsconfig.json` descritto in precedenza.

Il file JavaScript creato in `./out/app.js' in fase di compilazione conterrà il codice seguente:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

