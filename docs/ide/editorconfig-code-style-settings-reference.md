---
title: Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig | Microsoft Docs
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 1
author: kaseyu
ms.author: kaseyu
manager: davidcsa
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
ms.translationtype: HT
ms.sourcegitcommit: 223750aef8d997c6ae017f49ea0a9522bdba72bc
ms.openlocfilehash: c5687a3971d4b670e73e55294e6dfd0c7c3f91d0
ms.contentlocale: it-it
ms.lasthandoff: 08/10/2017

---

# <a name="net-coding-convention-settings-for-editorconfig"></a>Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig
Le convenzioni per la scrittura del codice .NET vengono configurate mediante un file [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options). I file EditorConfig consentono di **abilitare/disabilitare le singole convenzioni per la scrittura del codice .NET** e di **configurare il livello in base a cui si vuole applicare la convenzione** (tramite un livello di gravità). Per altre informazioni su come usare EditorConfig per applicare la coerenza nella codebase, leggere [questo articolo](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options).

Esistono tre categorie di convenzioni per la scrittura del codice .NET supportate:
- Le **[convenzioni del linguaggio](#language)** sono regole che riguardano il linguaggio C# o Visual Basic, ad esempio il tipo `var`/explicit o l'uso di membri con corpo di espressione.
- Le **[regole di formattazione](#formatting)** sono regole che riguardano il layout e la struttura del codice in modo da renderlo più facile da leggere, ad esempio le parentesi graffe Allman o la spaziatura nei blocchi di controllo.
- Le **[convenzioni di denominazione](#naming)** sono regole che rispettano il modo in cui gli oggetti vengono denominati, ad esempio i metodi `async` devono terminare con "Async". 

# <a name="language"> Convenzioni del linguaggio </a>
## <a name="overview"></a>Panoramica
**Formato della regola:**
`options_name = false|true : none|suggestion|warning|error`

Per l'opzione di stile di codice è necessario specificare **true** (opzione consigliata) o **false** (opzione non consigliata), i due punti (`:`) e un livello di gravità (`none`, `silent`, `suggestion`, `warning` o `error`). La gravità indica il livello di applicazione dello stile nella base di codice.

`none` e `silent` sono sinonimi e indicano che non devono essere visualizzate all'utente indicazioni di nessun tipo disabilitando di conseguenza questa regola.

Gravità | Effetto
------------ | -------------
none/silent | Non viene visualizzato alcun avviso all'utente quando lo stile non viene rispettato, ma le funzionalità di generazione del codice generano comunque lo stile. 
suggestion | Quando lo stile non viene rispettato, viene visualizzato un suggerimento all'utente: i primi due caratteri vengono sottolineati con dei puntini.
avviso | Quando lo stile non è rispettato, viene visualizzato un avviso del compilatore.
errore | Quando lo stile non è rispettato, viene visualizzato un errore del compilatore.

## <a name="net-language-convention-options"></a>Opzioni di convenzione del linguaggio .NET

- **[Impostazioni di stile di codice .NET](#this_and_me)**
    - ["This." e "Me." - Qualificazione](#this_and_me)
        - [Campi](#this_and_me_fields)
        - [Proprietà](#this_and_me_properties)
        - [Metodi](#this_and_me_methods)
        - [Eventi](#this_and_me_events)
    - [Parole chiave (int, string e così via) piuttosto che nomi tipi framework per i riferimenti di tipo](#language_keywords)
        - [Variabili locali, parametri e membri](#language_keywords_variables)
        - [Espressioni di accesso ai membri](#language_keywords_member_access)
    - [Preferenze a livello di espressione](#expression_level)
        - [Inizializzatori di oggetti](#expression_level_object_initializers)
        - [Inizializzatori di insieme](#expression_level_collection_initializers)
        - [Nomi di tupla espliciti](#expression_level_tuple_names)
        - [Espressioni di unione nel controllo "Null"](#expression_level_null_checking)
        - [Propagazione Null nel controllo "Null"](#expression_level_null_propogation)
- **[Impostazioni di stile di codice CSharp](#csharp_codestyle)**
    - ["var"](#var)
        - ["var" per tipi incorporati](#var_built_in)
        - ["var" quando il tipo è evidente](#var_apparent)
        - ["var" altrove](#var_elsewhere)
    - [Membri con corpo di espressione](#expression_body)
        - [Metodi](#expression_bodied_members_methods)
        - [Costruttori](#expression_bodied_members_constructors)
        - [Operatori](#expression_bodied_members_operators)
        - [Proprietà](#expression_bodied_members_properties)
        - [Indicizzatori](#expression_bodied_members_indexers)
        - [Funzioni di accesso](#expression_bodied_members_accessors)
    - [Criteri di ricerca](#pattern_matching)
        - ["is" con il controllo "cast"](#pattern_matching_is_cast)
        - ["as" con controllo "Null"](#pattern_matching_as_null)
    - [Dichiarazioni di variabili inline](#inlined_variable_declarations)
    - [Preferenze a livello di espressione](#expression_level_csharp) -[Semplificare le espressioni `default`](#expression_level_default)
    - [Preferenze controllo "Null"](#null_checking)
        - [Espressioni throw](#null_checking_throw_expressions)
        - [Chiamate al delegato condizionale](#null_checking_conditional_delegate_calls)
    - [Preferenze di blocco del codice](#code_block)
        - [Preferire le parentesi graffe](#prefer_braces)

## <a name="this_and_me">"This." e "Me." - Qualificazione</a>
### <a name="this_and_me_fields">Campi (IDE0003/IDE0009)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `dotnet_style_qualification_for_field` | C# e Visual Basic | false:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce che tutti i campi non statici usati nei metodi non statici vengano preceduti da `this.` in C# o da `Me.` in Visual Basic. | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** <br> `Me.capacity = 0`
| False | Preferisce che tutti i campi non statici usati nei metodi non statici non vengano preceduti da `this.` in C# o da `Me.` in Visual Basic. | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** <br>`capacity = 0`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">Proprietà (IDE0003/IDE0009) </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_property`| C# e Visual Basic | false:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce che tutte le proprietà non statiche usate nei metodi non statici vengano precedute da `this.` in C# o da `Me.` in Visual Basic.| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** <br>`Me.ID = 0`
| False | Preferisce che tutte le proprietà non statiche usate nei metodi non statici *non* vengano precedute da `this.` in C# o da `Me.` in Visual Basic. | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** <br> `ID = 0`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```

### <a name="this_and_me_methods">Metodi (IDE0003/IDE0009) </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_method`| C# e Visual Basic | false:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce che tutti i metodi non statici chiamati da metodi non statici vengano preceduti da `this.` in C# o da `Me.` in Visual Basic.| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** <br> `Me.Display()`
| False | Preferisce che tutti i metodi non statici chiamati da metodi non statici *non* vengano preceduti da `this.` in C# o da `Me.` in Visual Basic. | **C#:** <br>`Display();` <br><br> **Visual Basic:** <br> `Display()`


#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">Eventi (IDE0003/IDE0009) </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_event`| C# e Visual Basic | false:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce che tutti gli eventi non statici con riferimenti da metodi non statici vengano preceduti da `this.` in C# e da `Me.` in Visual Basic.| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** <br> `AddHandler Me.Elapsed, AddressOf Handler`
| False | Preferisce che tutti gli eventi non statici con riferimenti da metodi non statici *non* vengano preceduti da `this.` in C# e da `Me.` in Visual Basic. | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** <br>`AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Parole chiave (int, string e così via) piuttosto che nomi di tipi di framework per i riferimenti di tipo </a>
### <a name="language_keywords_variables"> Variabili locali, parametri e membri (IDE0012/IDE0014)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_predefined_type_for_locals_parameters_members`| C# e Visual Basic | true:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Per variabili locali, parametri e membri dei tipi, preferisce che i tipi rappresentati da una parola chiave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) usino la parola chiave anziché il nome di tipo (`Int32`, `Int64` e così via).| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | Per variabili locali, parametri e membri dei tipi, preferisce che i tipi rappresentati da una parola chiave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) usino il nome di tipo (`Int32`, `Int64` e così via) invece della parola chiave.  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** <br> `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">Espressioni di accesso ai membri (IDE0013/IDE0015)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_predefined_type_for_member_access`| C# e Visual Basic | true:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce la parola chiave, ogni volta che viene usata un'espressione di accesso ai membri in un tipo con una rappresentazione parola chiave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`).| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Integer.MaxValue`
| False | Preferisce il nome di tipo ogni volta che viene usata un'espressione di accesso ai membri in un tipo con una rappresentazione parola chiave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`). | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">Preferenze a livello di espressione</a>
### <a name="expression_level_object_initializers">Inizializzatori di oggetto (IDE0017)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_object_initializer`| C# e Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce oggetti da inizializzare usando gli inizializzatori di oggetti, quando possibile.| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** <br> `Dim c = New Customer() With { .Age = 21 }`
| False | Preferisce oggetti da inizializzare *non* usando gli inizializzatori di oggetti, quando possibile. | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">Inizializzatori di raccolta (IDE0028)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_collection_initializer`| C# e Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce insiemi da inizializzare usando inizializzatori di insieme, quando possibile.| **C#:** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic:** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | Preferisce oggetti da inizializzare *non* usando inizializzatori di insieme, quando possibile. | **C#:** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic:** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">Nomi di tupla espliciti (IDE0033)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_explicit_tuple_names`| C# 7.0+ e Visual Basic 15+ | true:suggestion | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce nomi di tupla alle proprietà ItemX.| **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic:** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | Preferisce le proprietà ItemX ai nomi di tupla. | **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic:** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">Espressioni di unione nel controllo "null" (IDE0029)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_coalesce_expression`| C# e Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce espressioni di unione nulle al controllo degli operatori ternari.| **C#:** <br>`var v = x ?? y;` <br><br> **Visual Basic:** <br> `Dim v = If(x, y)`
| False | Preferisce il controllo degli operatori ternari all'espressione di unione nulla. | **C#:** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic:** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">Propagazione Null nel controllo "Null" (IDE0031)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_null_propagation`| C# 6.0+ e Visual Basic 14+ | true:suggestion | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce l'uso dell'operatore condizionale Null, laddove possibile.| **C#:** <br>`var v = o?.ToString();` <br><br> **Visual Basic:** <br> `Dim v = o?.ToString()`
| False | Preferisce l'uso del controllo Null ternario, laddove possibile. | **C#:** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic:** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">Impostazioni di stile codice CSharp</a>
## <a name="var">Tipi "var" ed Explicit</a>
### <a name="var_built_in">"var" per i tipi predefiniti (IDE0007, IDE0008)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_for_built_in_types`| C# | true:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce l'uso di `var` per i tipi di sistema incorporati, ad esempio `int`.| **C#:** <br>`var x = 5;`
| False | Preferisce che non venga usato `var` per i tipi di sistema incorporati, ad esempio `int`. | **C#:** <br>`int x = 5;`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">"var" quando il tipo è evidente (IDE0007, IDE0008)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_when_type_is_apparent`| C# | true:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce `var` quando il tipo è già menzionato nel lato destro di un'espressione di dichiarazione.| **C#:** <br>`var obj = new C();`
| False | Preferisce che non venga usato `var` quando il tipo è già menzionato nel lato destro di un'espressione di dichiarazione. | **C#:** <br>`C obj = new C();`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">"var" altrove (IDE0007, IDE0008) </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_elsewhere`| C# | true:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce `var` in tutti i casi a meno che non sia stato eseguito l'override da un'altra regola di stile di codice.| **C#:** <br>`var f = this.Init();`
| False | Preferisce che var non venga usato in alcun caso a meno che non sia stato eseguito l'override da un'altra regola di stile di codice.| **C#:** <br>`bool f = this.Init();`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

##<a name="expression_bodied_members">Membri con corpo di espressione</a>
### <a name="expression_bodied_members_methods">Metodi (IDE0022)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_methods`| C# 6.0+ | false:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce membri con corpo di espressione per i metodi.| **C#:** <br>`public int GetAge() => this.Age;`
| False | Non preferisce membri con corpo di espressione per i metodi.| **C#:** <br>`public int GetAge() { return this.Age; }`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">Costruttori (IDE0021)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_constructors`| C# 7.0+ | false:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce membri con corpo di espressione per i costruttori.| **C#:** <br>`public Customer(int age) => Age = age;`
| False | Non preferisce membri con corpo di espressione per i costruttori.| **C#:** <br>`public Customer(int age) { Age = age; }`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">Operatori (IDE0023, IDE0024)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_operators` | C# 7.0+ | false:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce membri con corpo di espressione per gli operatori.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | Non preferisce membri con corpo di espressione per gli operatori.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">Proprietà (IDE0025)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_properties` | C# 7.0+ | true:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce membri con corpo di espressione per le proprietà.| **C#:** <br>`public int Age => _age;`
| False | Non preferisce membri con corpo di espressione per le proprietà.| **C#:** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = true:none
``` 

### <a name="expression_bodied_members_indexers">Indicizzatori (IDE0026)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_indexers` | C# 7.0+ | true:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce membri con corpo di espressione per gli indicizzatori.| **C#:** <br>`public T this[int i] => _value[i];`
| False | Non preferisce membri con corpo di espressione per gli indicizzatori.| **C#:** <br>`public T this[int i] { get { return _values[i]; } }`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">Funzioni di accesso (IDE0027)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_accessors` | C# 7.0+ | true:none | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce membri con corpo di espressione per le funzioni di accesso.| **C#:** <br>`public int Age { get => _age; set => _age = value; }`
| False | Non preferisce membri con corpo di espressione per le funzioni di accesso.| **C#:** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">Criteri di ricerca</a>
### <a name="pattern_matching_is_cast">"is" con il controllo "cast" (IDE0020)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_pattern_matching_over_is_with_cast_check` | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce i criteri di ricerca invece delle espressioni `is` con cast dei tipi.| **C#:** <br>`if (o is int i) {...}`
| False | Preferisce le espressioni `is` con cast dei tipi invece dei criteri di ricerca.| **C#:** <br>`if (o is int) {var i = (int)o; ... }`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">"as" con controllo "null" (IDE0019)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_pattern_matching_over_as_with_null_check` | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce i criteri di ricerca anziché le espressioni `as` con i controlli Null per determinare se un elemento è di un determinato tipo.| **C#:** <br>`if (o is string s) {...}`
| False | Preferisce le espressioni `as` con i controlli Null invece dei criteri di ricerca per determinare se un elemento è di un determinato tipo.| **C#:** <br>`var s = o as string; if (s != null) {...}`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">Dichiarazioni di variabili inline (IDE0018)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_inlined_variable_declaration` | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce che le variabili `out` siano dichiarate inline, quando possibile. | **C#:** <br>`if (int.TryParse(value, out int i) {...}`
| False | Preferisce che le variabili `out` siano dichiarate esplicitamente.| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```
## <a name="expression_level_csharp">Preferenze a livello di espressione</a>
### <a name="expression_level_default">Semplificare le espressioni `default` (IDE0034) </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_prefer_simple_default_expression` | C# 7.1+ | true:suggestion | Visual Studio 2017 versione 15.3 |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce `default` rispetto a `default(T)` | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default){ ... }`
| False | Preferisce. | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default(CancellationToken)){ ... }`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

## <a name="null_checking">Preferenze controllo "Null"</a>
### <a name="null_checking_throw_expressions">Espressioni throw (IDE0016)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_throw_expression`  | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce l'uso di espressioni throw anziché di istruzioni throw. | **C#:** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | Preferisce l'uso di istruzioni throw anziché di espressioni throw.| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">Preferisce le chiamate al delegato condizionale (IDE0041)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_conditional_delegate_call`  | C# 6.0+ | true:suggestion | Visual Studio 2017 RTW |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce l'uso dell'operatore di unione condizionale (`?.`) quando si chiama un'espressione lambda anziché eseguire un controllo Null. | **C#:** <br>`func?.Invoke(args);`
| False | Preferisce l'esecuzione di un controllo Null prima di chiamare un'espressione lambda anziché usare l'operatore di unione condizionale (`?.`).| **C#:** <br>`if (func!=null) { func(args); }`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

## <a name="code_block">"Preferenze di blocco del codice</a>
### <a name="prefer_braces">Preferire le parantesi graffe (IDE0011)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_prefer_braces`  | C#  | true:none | Visual Studio 2017 versione 15.3 |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferire le parentesi graffe | **C#:** <br>`if (test) { this.Display(); }`
| False | Preferire senza parentesi graffe quando possibile | **C#:** <br>`if (test) this.Display();`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

# <a name="formatting"> Regole di formattazione </a>
## <a name="overview"></a>Panoramica
**Formato della regola:**
`options_name = false|true`

Per le opzioni di formattazione è necessario specificare **true** (opzione consigliata) o **false** (opzione non consigliata) ad eccezione di un paio di casi in cui invece è necessario specificare le condizioni a cui si vuole applicare la regola.

## <a name="net-formatting-options"></a>Opzioni di formattazione .NET

- **[Impostazioni di formattazione .NET](#usings)**
    - [Organizzare direttive using](#usings)
        - [Ordinare prima le direttive System](#usings_sort_system_first)
- **[Impostazioni di formattazione C#](#newline)**
    - [Opzioni dei caratteri di nuova riga](#newline)
        - [Nuova riga prima della parentesi graffa aperta (`{`)](#newline_before_brace)
        - [Nuova riga prima di `else`](#newline_before_else)
        - [Nuova riga prima di `catch`](#newline_before_catch)
        - [Nuova riga prima di `finally`](#newline_before_finally)
        - [Nuova riga prima dei membri di inizializzatori di oggetto](#newline_before_object)
        - [Nuova riga prima dei membri di tipi anonimi](#newline_before_anonymous)
        - [Nuova riga prima dei membri di clausole di espressione di query](#newline_before_query)
    - [Opzioni di rientro](#indent)
        - [Impostare un rientro per contenuto case `switch`](#indent_switch)
        - [Impostare un rientro per le etichette `switch`](#indent_switch_labels)
        - [Posizionamento delle etichette](#label)
    - [Opzioni di spaziatura](#spacing)
        - [Spazio dopo il cast](#space_after_cast)
        - [Spazio dopo le parole chiave nelle istruzioni del flusso di controllo](#space_control_flow)
        - [Spazio tra le parentesi per l'elenco di parametri per dichiarazioni di metodi](#space_parameter_list)
        - [Spazio all'interno delle parentesi per l'elenco di argomenti per chiamate ai metodi](#space_method_call)
        - [Spazio all'interno delle parentesi per altre opzioni](#space_other)
    - [Opzioni di ritorno a capo](#wrapping)
        - [Lascia istruzioni e dichiarazioni di membri sulla stessa riga](#wrapping_statement)
        - [Lascia blocco su una sola riga](#wrapping_block)

## <a name="usings">Organizzare direttive using</a>
### <a name="usings_sort_system_first">Ordinare prima le direttive System</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_sort_system_directives_first`  |  C# e Visual Basic | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Ordina le direttive using System.* in ordine alfabetico e le inserisce prima delle altre direttive using.| **C#:** <br>`using System.Collections.Generic;`<br> `using System.Threading.Tasks;`<br> `using Octokit;`
| False | Non sono previsti requisiti per l'ordinamento delle direttive using | **C#:** <br>`using System.Collections.Generic;`<br> `using Octokit;` <br> `using System.Threading.Tasks;`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# .NET formatting settings:
[*.cs, *.vb]
dotnet_sort_system_directives_first = true
``` 

# <a name="csharp_formatting">Impostazioni di formattazione C#</a>
## <a name="newline">Opzioni dei caratteri di nuova riga</a>
### <a name="newline_before_brace"> Nuova riga prima della parentesi graffa aperta (`{`)</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_before_open_brace`  |  C#  | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione 
| ------------- |:-------------|
| accessors, anonymous_methods, anonymous_types, control_blocks, events, indexers, lambdas, local_functions, methods, object_collection, properties, types. (Per più valori, separarli con ','). | Le parentesi graffe devono essere posizionate in una nuova riga per le espressioni specificate (stile Allman) |
| tutti | Le parentesi graffe devono essere posizionate in una nuova riga per tutte le espressioni (Allman) |
| nessuno | Le parentesi graffe devono essere posizionate nella stessa riga per tutte le espressioni (K&R) |

#### <a name="applied"></a>Applicazione:
```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}
```

```csharp
// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
``` 

### <a name="newline_before_else"> Nuova riga prima di `else`</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_before_else` |  C#  | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione 
| ------------- |:-------------|
| True | Posiziona le istruzioni `else` in una nuova riga.  |
| False | Posiziona le istruzioni `else` nella stessa riga.  |

#### <a name="applied"></a>Applicazione:
```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}
```

```csharp
// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_else = true
``` 

### <a name="newline_before_catch"> Nuova riga prima di `catch`</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_catch`|  C#  | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione 
| ------------- |:-------------|
| True | Posiziona le istruzioni `catch` in una nuova riga.  |
| False | Posiziona le istruzioni `catch` nella stessa riga. |

#### <a name="applied"></a>Applicazione:
```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}
```

```csharp
// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_catch = true
``` 

### <a name="newline_before_finally"> Nuova riga prima di `finally`</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_finally`|  C#  | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione 
| ------------- |:-------------|
| True | Le istruzioni `finally` devono essere posizionate in una nuova riga dopo la parentesi graffa chiusa.  |
| False | Le istruzioni `finally` devono essere posizionate nella stessa riga della parentesi graffa chiusa.  |

#### <a name="applied"></a>Applicazione:
```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}
```

```csharp
// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_finally = true
``` 

### <a name="newline_before_object"> Nuova riga prima dei membri di inizializzatori di oggetto</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_members_in_object_initializers`|  C#  | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione 
| ------------- |:-------------|
| True | I membri di inizializzatori di oggetto devono essere posizionati in righe separate.  |
| False | I membri di inizializzatori di oggetto devono essere posizionati nella stessa riga.  |

#### <a name="applied"></a>Applicazione:
```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_object_initializers = true
``` 

### <a name="newline_before_anonymous"> Nuova riga prima dei membri di tipi anonimi</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_members_in_anonymous_types` |  C#  | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione 
| ------------- |:-------------|
| True | I membri di tipi anonimi devono essere posizionati in righe separate.  |
| False | I membri di tipi anonimi devono essere posizionati nella stessa riga.  |

#### <a name="applied"></a>Applicazione:
```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_anonymous_types = true
``` 

### <a name="newline_before_query"> Nuova riga prima dei membri di clausole di espressione di query</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_within_query_expression_clauses`  |  C#  | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione 
| ------------- |:-------------|
| True | Gli elementi di clausole di espressione di query devono essere posizionati in righe separate.  |
| False | Gli elementi di clausole di espressione di query devono essere posizionati nella stessa riga.  |

#### <a name="applied"></a>Applicazione:
```csharp
// csharp_new_line_within_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;
```

```csharp
// csharp_new_line_within_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_within_query_expression_clauses = true
``` 

## <a name="indent">Opzioni di rientro</a>
### <a name="indent_switch">Impostare un rientro per contenuto case `switch`</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_indent_case_contents`  |  C#  | true | Visual Studio 2017 versione 15.3  |

| Valore | Descrizione 
| ------------- |:-------------|
| True | Imposta un rientro per contenuto case `switch`  |
| False | Non imposta un rientro per contenuto case `switch` |

#### <a name="applied"></a>Applicazione:
```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}
```

```csharp
// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
``` 

### <a name="indent_switch_labels"> Impostare un rientro per le etichette `switch` </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_indent_switch_labels`  |  C#  | true | Visual Studio 2017 versione 15.3  |

| Valore | Descrizione 
| ------------- |:-------------|
| True | Impostare un rientro per le etichette `switch`  |
| False | Non impostare un rientro per le etichette `switch` |

#### <a name="applied"></a>Applicazione:
```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}
```

```csharp
// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_switch_labels = true
``` 

### <a name="label">Posizionamento delle etichette</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_indent_labels`  |  C#  | one_less | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione 
| ------------- |:-------------|
| one_less | Le etichette vengono posizionate con un rientro minore rispetto al contesto corrente |
| no_change | Le etichette vengono posizionate con lo stesso rientro del contesto corrente |

#### <a name="applied"></a>Applicazione:
```csharp
// csharp_indent_labels = one_less
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
error:
    throw new Exception(...);
}

```

```csharp
// csharp_indent_labels= no_change
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
    error:
    throw new Exception(...);
}
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_labels = one_less
``` 

## <a name="spacing">Opzioni di spaziatura</a>
### <a name="space_after_cast"> Spazio dopo il cast </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_after_cast` |  C#  | false | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione | Applicazione |
| ------------- |:-------------|:-------------|
| True | È necessario uno spazio tra il cast e il valore  | **C#:** <br>`int y = (int) x;`
| False | Non è necessario alcuno spazio tra il cast e il valore | **C#:** <br>`int y = (int)x;`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
``` 

### <a name="space_control_flow"> Spazio dopo le parole chiave nelle istruzioni del flusso di controllo </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_after_keywords_in_control_flow_statements` |  C#  | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione | Applicazione |
| ------------- |:-------------|:-------------|
| True | È necessario uno spazio dopo una parola chiave | **C#:** <br>`for (int i;i<x;i++) { ... }`
| False | Non è necessario alcuno spazio dopo una parola chiave | **C#:** <br>`for(int i;i<x;i++) { ... }`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_keywords_in_control_flow_statements = true
``` 

### <a name="space_parameter_list"> Spazio tra le parentesi per l'elenco di parametri per dichiarazioni di metodi </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_between_method_declaration_parameter_list_parentheses` |  C#  | false | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione | Applicazione |
| ------------- |:-------------|:-------------|
| True | È necessario uno spazio dopo una parola chiave | **C#:** <br>`void Bark( int x ) { ... }`
| False | Non è necessario alcuno spazio dopo una parola chiave | **C#:** <br>`void Bark(int x) { ... }`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_declaration_parameter_list_parentheses = true
```

### <a name="space_method_call"> Spazio all'interno delle parentesi per l'elenco di argomenti per chiamate ai metodi </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_space_between_method_call_parameter_list_parentheses` |  C#  | false | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione | Applicazione |
| ------------- |:-------------|:-------------|
| true | Inserisce uno spazio tra le parentesi delle istruzioni del flusso di controllo | **C#:** <br>`MyMethod( argument );`
| false | Inserisce uno spazio tra le parentesi delle espressioni | **C#:** <br>`MyMethod(argument);`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_call_parameter_list_parentheses = control_flow_statements, type_casts
```  

### <a name="space_other"> Spazio all'interno delle parentesi per altre opzioni </a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_space_between_parentheses`  |  C#  | false | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione | Applicazione |
| ------------- |:-------------|:-------------|
| control_flow_statements | Inserisce uno spazio tra le parentesi delle istruzioni del flusso di controllo | **C#:** <br>`for( int i;i<x;i++ ) { ... }`
| espressioni | Inserisce uno spazio tra le parentesi delle espressioni | **C#:** <br>`var z = ( x * y ) - ( ( y - x ) * 3);`
| type_casts | Inserisce uno spazio tra le parentesi dei cast di tipo | **C#:**<br>`int y = ( int )x;`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

## <a name="wrapping">Opzioni di ritorno a capo</a>
### <a name="wrapping_statement">Lascia istruzioni e dichiarazioni di membri sulla stessa riga</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_preserve_single_line_statements`   |  C#  | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione |
| ------------- |:-------------|
| True | Lascia istruzioni e dichiarazioni di membri sulla stessa riga  | 
| False | Lascia istruzioni e dichiarazioni di membri su righe diverse | 

#### <a name="applied"></a>Applicazione
```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";
```

```csharp
//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
``` 

### <a name="wrapping_block">Lascia blocco su una sola riga</a>
| **Nome dell'opzione** | **Linguaggi applicabili** | **Impostazione predefinita di Visual Studio** | **Versione supportata** |
| ----------- | -------------------- | ----------------------| ----------------  |
|   `csharp_preserve_single_line_blocks`    |  C#  | true | Visual Studio 2017 versione 15.3  |


| Valore | Descrizione |
| ------------- |:-------------|
| True | Lascia blocco su una sola riga | 
| False | Lascia blocco su righe separate | 

#### <a name="applied"></a>Applicazione
```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }
```

```csharp
//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_blocks = true
``` 

# <a name="naming"> Convenzioni di denominazione </a>
## <a name="overview"></a>Panoramica
**Formato della regola:**<br>
namingRuleTitle:<br>
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`<br>
<br>
symbolTitle:<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter`<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = public, internal, private, protected, protected_internal`<br>
`dotnet_naming_symbols.<symbolTitle>.required_modifiers = abstract, async, const, readonly, static`<br>
<br>
styleTitle:<br>
`dotnet_naming_style.<styleTitle>.capitalization = pascal_case|camel_case|first_word_upper|all_upper|all_lower`<br>
`dotnet_naming_style.<styleTitle>.required_prefix = string`<br>
`dotnet_naming_style.<styleTitle>.required_suffix = string`<br>
`dotnet_naming_style.<styleTitle>.word_separator = string`<br>

## <a name="writing-a-naming-convention"></a>Scrittura di una convenzione di denominazione
Per le convenzioni di denominazione è necessario specificare **simboli**, **stile** e **gravità**. Le convenzioni di denominazione devono essere ordinate dalla convenzione più specifica a quella meno specifica. La prima regola rilevata che può essere applicata sarà l'unica regola applicata. 

### <a name="severity"></a>Gravità
Di seguito sono riportate le opzioni valide per la gravità di una regola di stile di denominazione: `none`, `silent`, `suggestion`, `warning`, `error`.

 `none` e `silent` sono sinonimi e indicano che non devono essere visualizzate all'utente indicazioni di nessun tipo disabilitando di conseguenza questa regola.

 `suggestion` indica che l'utente visualizzerà quanto segue nell'elenco errori e nell'IDE. La gravità `suggestion` consentirà l'esecuzione della regola di denominazione ma senza comportare l'interruzione della compilazione.

Gravità | Effetto
------------ | -------------
none/silent | Non viene visualizzato alcun avviso all'utente quando lo stile non viene rispettato, ma le funzionalità di generazione del codice generano comunque lo stile. 
suggestion | Quando lo stile non viene rispettato, viene visualizzato un suggerimento all'utente: i primi due caratteri vengono sottolineati con dei puntini.
avviso | Quando lo stile non è rispettato, viene visualizzato un avviso del compilatore.
errore | Quando lo stile non è rispettato, viene visualizzato un errore del compilatore.

### <a name="symbol-specification"></a>Specifica dei simboli
Identificare a _quali_ simboli _con quali_ modificatori e _con quale_ livello di accessibilità deve essere applicata la regola di denominazione.

|  Nome dell'opzione | `dotnet_naming_rule.<namingRuleTitle>.symbols` |
| ------------- |:-------------:|
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_kinds`
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities`
|  | `dotnet_naming_symbols.<symbolTitle>.required_modifiers`

| Simbolo | Accessibilità | Modificatori
| ------------- |------------- |------------- |
| `*` | `*` |  `abstract` | 
| `class` | `public` |  `must_inherit` | `async` | 
| `struct` | `internal` (C#) /  | `const` | 
| `interface` | `friend` (Visual Basic) | `readonly` | 
| `enum` | `private`  | `static` | 
| `property` | `protected` | `shared` |
| `method` |`protected_internal` (C#) | |
| `field` | `protected_friend` (Visual Basic) | |
| `event` | | |
| `delegate` | | |


### <a name="style-specification"></a>Specifica dello stile
Identificare lo stile di denominazione da applicare ai simboli.

|  Nome dell'opzione | `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>` |
| ------------- |:-------------:|
|  | `dotnet_naming_style.<styleTitle>.capitalization`|
|  | `dotnet_naming_style.<styleTitle>.required_prefix`|
|  | `dotnet_naming_style.<styleTitle>.required_suffix`|
|  | `dotnet_naming_style.<styleTitle>.word_separator`|


| Stile | Descrizione |
| ------------- |:-------------:|
| Prefisso | Caratteri necessari che devono essere visualizzati prima dell'identificatore. |
| Suffisso | Caratteri necessari che devono essere visualizzati dopo l'identificatore. |
| Separatore parole | Separatore necessario tra le parole nell'identificatore. |
| Maiuscole/minuscole |`pascal_case`, `camel_case`, `first_word_upper`, `all_upper`, `all_lower` | 


### <a name="example-naming-convention"></a>Esempio di convenzione di denominazione
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

