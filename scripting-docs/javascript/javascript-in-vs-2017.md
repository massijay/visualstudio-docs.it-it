---
title: JavaScript in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 04/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: "1"
author: bowdenk7
ms.author: wilkelly
manager: ghogen
ms.openlocfilehash: d217443ed0231d71f861ed54b27f3f8d1e8d49ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-in-includevsdev15docsmiscincludesvsdev15mdmd"></a>JavaScript in[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)]

JavaScript è un ottimo linguaggio di Visual Studio. È possibile usare la maggior parte o tutti gli strumenti di modifica standard (frammenti di codice, IntelliSense e così via) quando si scrive codice JavaScript nell'IDE di Visual Studio. È possibile scrivere codice JavaScript per molti tipi di applicazioni e servizi.

## <a name="ES6"></a>Supporto per ECMAScript 2015 (ES6) e versioni successive
Visual Studio ora supporta la sintassi per gli aggiornamenti del linguaggio ECMAScript, ad esempio ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>Che cos'è ECMAScript 2015?

JavaScript è in continua evoluzione come linguaggio di programmazione e [TC39](http://www.ecma-international.org/memento/TC39.htm) è il comitato responsabile dell'esecuzione di aggiornamenti.  
ECMAScript 2015 è un aggiornamento del linguaggio JavaScript che porta una grande quantità di sintassi utile e di funzionalità.
Per approfondimenti sulle funzionalità di ES6, consultare [questo](http://es6-features.org) sito di riferimento.

Oltre a supportare ECMAScript 2015, Visual Studio supporta anche ECMAScript 2016 e supporterà le future versioni di ECMAScript non appena verranno rilasciate. Per mantenere TC39 e le modifiche più recenti in ECMAScript, seguire il lavoro [github](https://github.com/tc39).

### <a name="transpiling-javascript"></a>Transpiling di JavaScript

Un problema comune con JavaScript è che si desidera usare le più recenti funzionalità di linguaggio ES6+ perché consentono di essere più produttivi, ma gli ambienti di runtime (spesso i browser) ancora non supportano queste nuove funzionalità.
Ciò significa che è che necessario o tenere traccia di quali browser supportano quali funzionalità (ciò può rivelarsi noioso) o trovare un modo per convertire il codice ES6+ in una versione comprensibile per i runtime di destinazione (in genere ES5).
Questo è ciò che noto come "transpiling".

Una delle funzionalità chiave di TypeScript è la capacità di eseguire il transpiling del codice ES6+ a ES3 e ES5, in modo che è possibile scrivere il codice che rende più produttivi, ma comunque eseguire il codice in qualsiasi piattaforma.  
Dato che JavaScript in [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] usa lo stesso servizio di linguaggio di TypeScript, può a sua volta avvalersi del transpiling da ES6 e versioni successive a ES5.

Prima di configurare questa funzionalità è necessario un approfondimento relativo alle opzioni di configurazione. TypeScript viene configurato tramite un file `tsconfig.json`. In assenza di tale file vengono usati alcuni valori predefiniti. Per motivi di compatibilità, tali valori predefiniti sono diversi in un contesto che include solo file JavaScript (e facoltativamente file `.d.ts`). Per la compilazione dei file JavaScript è necessario aggiungere un file `tsconfig.json` e impostare in modo esplicito alcune di queste opzioni.

Le impostazioni necessarie per il file tsconfig sono descritte di seguito:

 - `allowJs`: per il riconoscimento dei file JavaScript, questo valore deve essere impostato su `true`.
L'impostazione predefinita è `false` perché TypeScript esegue la compilazione in JavaScript e tale impostazione è necessaria per evitare che il compilatore includa i file che ha appena compilato.
 - `outDir`: questa opzione deve essere impostata su un percorso non incluso nel progetto, in modo che i file JavaScript generati non vengano rilevati e quindi inclusi a loro volta nel progetto (vedere `exclude` di seguito).
 - `module`: se si usano i moduli, questa impostazione indica al compilatore il formato di modulo usato dal codice generato (ad esempio `commonjs` per Node o bundler come Browserify).
 - `exclude`: questa impostazione indica le cartelle da non includere nel progetto. 
 Aggiungere a questa impostazione il percorso di output e le cartelle non di progetto, quali `node_modules` o `temp`.
 - `enableAutoDiscovery`: questa impostazione consente il rilevamento e il download automatico dei file di definizione come descritto in precedenza.
 - `compileOnSave`: questa impostazione indica al compilatore se è necessario ricompilare quando un file di origine viene salvato in Visual Studio.
 - `typeAcquisition`: Questo set di impostazioni controlla il comportamento dell'acquisto di tipo automatica (altre spiegazioni in [questa sezione](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense#Auto))

Per convertire i file JavaScript in moduli CommonJS e inserirli in una cartella `./out`, è possibile usare il file `tsconfig.json` seguente.

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
  "typeAcquisition": {
    "enable": true
  }
}
```

Si supponga che le impostazioni precedenti siano attivate e che esista un file di origine (`./app.js`) e contenga varie funzionalità del linguaggio ECMAScript 2015, come illustrato di seguito:

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
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
```

## <a name="better-intellisense"></a>Funzionalità IntelliSense migliore

JavaScript IntelliSense in [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] ora visualizza più informazioni relative agli elenchi di parametri e membri. Le nuove informazioni sono specificate dal servizio di linguaggio TypeScript, che usa l'analisi statica in background per un'interpretazione più approfondita del codice. Per ottenere altre informazioni sulla nuova esperienza IntelliSense e il relativo funzionamento vedere [qui](/visualstudio/ide/javascript-intellisense/).

## <a name="JSX"></a> Supporto della sintassi JSX

JavaScript in [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] offre un supporto dettagliato della sintassi JSX. JSX è un set di sintassi che consente la presenza di tag HTML nei file JavaScript. 

L'illustrazione che segue visualizza un componente React definito nel file TypeScript `comps.tsx`, quindi visualizza tale componente usato dal file `app.jsx` e provvisto di IntelliSense per il completamento e la documentazione all'interno delle espressioni JSX.
Qui non è necessario aggiungere codice TypeScript, perché casualmente l'esempio contiene già codice TypeScript.

<img src="./media/react.png" height="500" width="640"/>

> [!NOTE]
> Per convertire la sintassi JSX in chiamate React è necessario aggiungere l'impostazione `"jsx": "react"` a `compilerOptions` nel file `tsconfig.json` descritto in precedenza.

Il file JavaScript creato in `./out/app.js' in fase di compilazione conterrà il codice seguente:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

# <a name="configuring-your-javascript-project"></a>Configurazione del progetto JavaScript
Il servizio di linguaggio è alimentato dall'analisi statica, il che significa che analizza il codice sorgente senza realmente eseguirlo per restituire i risultati di IntelliSense e offrire altre funzionalità di modifica.
Pertanto, maggiore sarà la quantità e le dimensioni dei file che sono inclusi nel contesto del progetto, maggiore sarà la quantità di memoria e CPU usata durante l'analisi.
Per questo motivo, esistono alcuni presupposti predefiniti creati sulla forma del progetto:

- `package.json`e `bower.json` elencano le dipendenze usate dal progetto e per impostazione predefinita sono inclusi nell'Acquisizione di tipo automatico (ATA) < TODO: aggiungere collegamento >
- Una cartella di livello superiore `node_modules` contiene il codice sorgente della libreria e il relativo contenuto viene escluso dal contesto del progetto per impostazione predefinita
- Qualsiasi altro file `.js`, `.jsx`, `.ts`, e `.tsx` è probabilmente uno dei *propri* file di origine e deve essere incluso nel contesto del progetto

Nella maggior parte dei casi, sarà possibile solo aprire il progetto e avere un'esperienza ottimale tramite la configurazione di progetto predefinita in precedenza.
Tuttavia, nei progetti con diverse strutture della cartella o in progetti di dimensioni particolarmente grandi, può risultare utile configurare ulteriormente il servizio di linguaggio per concentrarsi meglio solo sui propri file di origine.

## <a name="overriding-defaults"></a>Override dei valori predefiniti
È possibile eseguire l'override della configurazione predefinita in precedenza aggiungendo un file `tsconfig.json` alla radice del progetto.
Un oggetto `tsconfig.json` ha diverse opzioni che possono modificare il contesto del progetto.
Alcune di esse sono elencati di seguito, ma per un set completo di tutte le opzioni disponibili, [vedere l'archivio degli schemi](http://json.schemastore.org/tsconfig). 

## <a name="important-tsconfigjson-options"></a>Opzioni `tsconfig.json` importanti

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA 
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

## <a name="example-project-configuration"></a>Configurazione del progetto di esempio

Dato un progetto con la seguente configurazione:
- i file di origine del progetto si trovano in`wwwroot/js`
- i file lib del progetto si trovano in`wwwrrot/lib`
- `bootstrap`, `jquery`, `jquery-validation`, e `jquery-validation-unobtrusive` sono elencati in `bower.json`
- `kendo-ui` è stato aggiunto manualmente alla cartella lib

![Struttura di cartelle](./media/folderStructure.png)

È possibile usare la seguente `tsconfig.json` per assicurarsi che il servizio di linguaggio analizzi solo i file di origine nella cartella `js`, ma recupera e usa i file `.d.ts` per le librerie nella cartella `lib`.

```json
{
  "compilerOptions": {
    "allowJs": true,          
    "noEmit": true            
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,            
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```

# <a name="notable-changes-from-vs-2015"></a>Modifiche di rilievo da VS 2015 
Poiché [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] è dotato di un servizio di linguaggio completamente nuovo, esistono alcuni comportamenti che saranno diversi o assenti rispetto all'esperienza precedente.
Le modifiche più importanti sono la sostituzione di VSDoc con JSDoc, la rimozione delle estensioni personalizzate `.intellisense.js` e IntelliSense limitato per i modelli di codice specifici.

## <a name="no-more-references-or-referencesjs"></a>`///<references/>` o `_references.js` non più disponibile
In precedenza era piuttosto complicato capire in qualsiasi momento quali file si trovassero nel proprio ambito di IntelliSense.
In alcuni casi era preferibile disporre di tutti i file nell'ambito, in altri casi non lo era, ma ciò ha comportato delle configurazioni complesse che comprendevano una gestione di riferimento manuale.
In futuro, non sarà più necessario preoccuparsi della gestione dei riferimenti e pertanto non sono necessari i commenti ai riferimenti con tripla barra o i file `_references.js`.

Vedere la pagina [JavaScript IntelliSense](/visualstudio/ide/javascript-intellisense/) per altre informazioni sul funzionamento di IntelliSense.

## <a name="vsdoc"></a>VSDoc
I commenti in formato documentazione XML, talvolta denominati VSDocs, potevano essere usati in precedenza per decorare il codice sorgente con dati aggiuntivi che potevano essere usati per respingere i risultati di IntelliSense.
VSDoc non è più supportato in favore di [JSDoc](http://usejsdoc.org/about-getting-started.html) che è più facile da scrivere ed è lo standard comunemente accettato per JavaScript.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` estensioni
In precedenza, era possibile creare [estensioni IntelliSense](https://msdn.microsoft.com/en-us/library/hh874692.aspx) che consentivano di aggiungere dei risultati di completamento personalizzato per le librerie di terze parti.
Queste estensioni erano piuttosto difficili da scrivere e installarle e farvi riferimento era un'operazione complessa, pertanto in futuro il nuovo servizio di linguaggio non supporterà tali file.
Come alternativa più semplice, è possibile scrivere un file di definizione TypeScript per fornire gli stessi vantaggi di IntelliSense delle vecchie estensioni `.intellisense.js`.
Altre informazioni sulla dichiarazione (`.d.ts`) di creazione di file [qui](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Modelli non supportati
Poiché il nuovo servizio di linguaggio è alimentato dalle analisi statiche piuttosto che da un motore di esecuzione (leggere [questo problema](https://github.com/Microsoft/TypeScript/issues/4789) per informazioni riguardanti le differenze), esistono alcuni modelli di JavaScript che non possono essere rilevati.
Il modello più comune è il modello "expando". Attualmente il servizio di linguaggio non può fornire IntelliSense ad oggetti che hanno proprietà aggiunte dopo la dichiarazione.
Ad esempio:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

È possibile aggirare il problema dichiarando le proprietà durante la creazione dell'oggetto:
```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

È anche possibile aggiungere un commento JSDoc come illustrato in precedenza:
```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```