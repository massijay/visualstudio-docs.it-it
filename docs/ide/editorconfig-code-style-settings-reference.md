---
title: Impostazioni di stile di codice .NET per EditorConfig | Microsoft Docs
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 01
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
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: a5b26ed093ed86c8c438b2024f69d371fde2de36
ms.lasthandoff: 03/27/2017

---

# <a name="net-code-style-settings-for-editorconfig"></a>Impostazioni di stile di codice .NET per EditorConfig

## <a name="possible-values"></a>Valori possibili

`options_name = false|true : none|suggestion|warning|error`

Per l'opzione di stile di codice è necessario specificare **true** (opzione consigliata) o **false** (opzione non consigliata), i due punti (`:`) e un livello di gravità (`none`, `suggestion`, `warning`, o `error`). La gravità indica il livello di applicazione dello stile nella base di codice.

Gravità | Effetto
------------ | -------------
nessuno | Non viene visualizzato alcun avviso all'utente quando lo stile non viene rispettato, ma le funzionalità di generazione del codice generano comunque lo stile. 
suggestion | Quando lo stile non viene rispettato, viene visualizzato un suggerimento all'utente: i primi due caratteri vengono sottolineati con dei puntini.
avviso | Quando lo stile non è rispettato, viene visualizzato un avviso del compilatore.
errore | Quando lo stile non è rispettato, viene visualizzato un errore del compilatore.

## <a name="net-code-style-options"></a>Opzioni di stile di codice .NET

- [Impostazioni di stile codice dotnet](#this_and_me)
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
- [Impostazioni di stile codice CSharp](#csharp_codestyle)
    - ["var"](#var)
        - ["var" per tipi incorporati](#var_built_in)
        - ["var" quando il tipo è evidente](#var_apparent)
        - ["var" altrove](#var_elsewhere)
    - [Membri con corpo di espressione](#expression_bodied_members)
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
    - [Preferenze controllo "Null"](#null_checking)
        - [Espressioni throw](#null_checking_throw_expressions)
        - [Chiamate al delegato condizionale](#null_checking_conditional_delegate_calls)

## <a name="this_and_me">"This." e "Me." - Qualificazione</a>

### <a name="this_and_me_fields">Campi</a>

|  Nome dell'opzione | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce che tutti i campi non statici usati nei metodi non statici vengano preceduti da `this.` in C# o da `Me.` in Visual Basic. | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** `Me.capacity = 0`
| False | Preferisce che tutti i campi non statici usati nei metodi non statici non vengano preceduti da `this.` in C# o da `Me.` in Visual Basic. | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** `capacity = 0`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">Proprietà</a>

|  Nome dell'opzione | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce che tutte le proprietà non statiche usate nei metodi non statici vengano precedute da `this.` in C# o da `Me.` in Visual Basic.| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** `Me.ID = 0`
| False | Preferisce che tutte le proprietà non statiche usate nei metodi non statici *non* vengano precedute da `this.` in C# o da `Me.` in Visual Basic. | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** `ID = 0`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```


### <a name="this_and_me_methods">Metodi</a>
|  Nome dell'opzione | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce che tutti i metodi non statici chiamati da metodi non statici vengano preceduti da `this.` in C# o da `Me.` in Visual Basic.| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** `Me.Display()`
| False | Preferisce che tutti i metodi non statici chiamati da metodi non statici *non* vengano preceduti da `this.` in C# o da `Me.` in Visual Basic. | **C#:** <br>`Display();` <br><br> **Visual Basic:** `Display()`


#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">Eventi</a>
|  Nome dell'opzione | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce che tutti gli eventi non statici con riferimenti da metodi non statici vengano preceduti da `this.` in C# e da `Me.` in Visual Basic.| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Me.Elapsed, AddressOf Handler`
| False | Preferisce che tutti gli eventi non statici con riferimenti da metodi non statici *non* vengano preceduti da `this.` in C# e da `Me.` in Visual Basic. | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Parole chiave (int, string e così via) piuttosto che nomi di tipi di framework per i riferimenti di tipo </a>
### <a name="language_keywords_variables">Variabili locali, parametri e membri</a>
|  Nome dell'opzione | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Per variabili locali, parametri e membri dei tipi, preferisce che i tipi rappresentati da una parola chiave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) usino la parola chiave anziché il nome di tipo (`Int32`, `Int64` e così via).| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | Per variabili locali, parametri e membri dei tipi, preferisce che i tipi rappresentati da una parola chiave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) usino il nome di tipo (`Int32`, `Int64` e così via) invece della parola chiave.  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">Espressioni di accesso ai membri</a>
|  Nome dell'opzione | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce la parola chiave, ogni volta che viene usata un'espressione di accesso ai membri in un tipo con una rappresentazione parola chiave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`).| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** `Dim local = Integer.MaxValue`
| False | Preferisce il nome di tipo ogni volta che viene usata un'espressione di accesso ai membri in un tipo con una rappresentazione parola chiave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`). | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">Preferenze a livello di espressione</a>
### <a name="expression_level_object_initializers">Inizializzatori di oggetti</a>
|  Nome dell'opzione | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce oggetti da inizializzare usando gli inizializzatori di oggetti, quando possibile.| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** `Dim c = New Customer() With { .Age = 21 }`
| False | Preferisce oggetti da inizializzare *non* usando gli inizializzatori di oggetti, quando possibile. | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">Inizializzatori di insieme</a>
|  Nome dell'opzione | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

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

### <a name="expression_level_tuple_names">Nomi di tupla espliciti</a>
|  Nome dell'opzione | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

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

### <a name="expression_level_null_checking">Espressioni di unione nel controllo "null"</a>
|  Nome dell'opzione | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

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

### <a name="expression_level_null_propogation">Propagazione Null nel controllo "Null"</a>
|  Nome dell'opzione | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C# e Visual Basic

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
## <a name="var">"var"</a>
### <a name="var_built_in">"var" per tipi incorporati</a>
|  Nome dell'opzione | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

### <a name="var_apparent">"var" quando il tipo è evidente</a>
|  Nome dell'opzione | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

### <a name="var_elsewhere">"var" altrove</a>
|  Nome dell'opzione | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

### <a name="expression_bodied_members">Metodi</a>
|  Nome dell'opzione | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

### <a name="expression_bodied_members_constructors">Costruttori</a>
|  Nome dell'opzione | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

### <a name="expression_bodied_members_operators">Operatori</a>
|  Nome dell'opzione | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

### <a name="expression_bodied_members_properties">Proprietà</a>
|  Nome dell'opzione | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

| Valore | Descrizione | Applicazione 
| ------------- |:-------------|:-------------|
| True | Preferisce membri con corpo di espressione per le proprietà.| **C#:** <br>`public int Age => _age;`
| False | Non preferisce membri con corpo di espressione per le proprietà.| **C#:** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>Esempio di file editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="expression_bodied_members_indexers">Indicizzatori</a>
|  Nome dell'opzione | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

### <a name="expression_bodied_members_accessors">Funzioni di accesso</a>
|  Nome dell'opzione | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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
### <a name="pattern_matching_is_cast">"is" con il controllo "cast"</a>
|  Nome dell'opzione | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

### <a name="pattern_matching_as_null">"as" con controllo "null"</a>
|  Nome dell'opzione | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

### <a name="inlined_variable_declarations">Dichiarazioni di variabili inline</a>
|  Nome dell'opzione | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

## <a name="null_checking">Preferenze controllo "Null"</a>
### <a name="null_checking_throw_expressions">Espressioni throw</a>
|  Nome dell'opzione | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

### <a name="null_checking_conditional_delegate_calls">Preferisce le chiamate al delegato condizionale</a>
|  Nome dell'opzione | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **Linguaggi applicabili** | C#

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

