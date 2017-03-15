---
title: "CA1019: Definire le funzioni di accesso per gli argomenti degli attributi | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
helpviewer_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1019: Definire le funzioni di accesso per gli argomenti degli attributi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un attributo definisce nel proprio costruttore argomenti che non dispongono di proprietà corrispondenti.  
  
## Descrizione della regola  
 Gli attributi possono definire argomenti obbligatori che devono essere specificati quando si applica l'attributo a una destinazione.  Sono inoltre noti come argomenti posizionali poiché vengono forniti ai costruttori di attributo come parametri posizionali.  Per ogni argomento obbligatorio, l'attributo deve fornire anche una proprietà in sola lettura corrispondente in modo che il valore dell'argomento possa essere recuperato in fase di esecuzione.  Mediante questa regola viene verificato che per ogni parametro del costruttore sia stata definita la proprietà corrispondente.  
  
 Gli attributi possono inoltre definire argomenti facoltativi, noti anche come argomenti denominati.  Questi argomenti sono forniti ai costruttori degli attributi in base al nome e devono disporre di una proprietà in lettura e scrittura corrispondente.  
  
 Per gli argomenti obbligatori e facoltativi, le proprietà corrispondenti e i parametri dei costruttori devono utilizzare lo stesso nome, ma convenzioni diverse relativamente all'uso di maiuscole e minuscole.  Le proprietà utilizzano la convenzione Pascal, i parametri la convenzione Camel.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere una proprietà in sola lettura per ogni parametro di costruttore che ne è privo.  
  
## Esclusione di avvisi  
 Eliminare un avviso da questa regola se non si desidera che il valore dell'argomento obbligatorio possa essere recuperato.  
  
## Esempio di attributi personalizzati  
  
### Descrizione  
 Nell'esempio riportato di seguito vengono illustrati due attributi che definiscono un parametro obbligatorio \(posizionale\).  La prima implementazione dell'attributo non è definita correttamente,  mentre la seconda è corretta.  
  
### Codice  
 [!code-cs[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## Argomenti posizionali e denominati  
  
### Descrizione  
 Gli argomenti posizionali e denominati rendono più chiaro agli utenti della libreria quali sono gli argomenti obbligatori per l'attributo e quali sono facoltativi.  
  
 Nell'esempio seguente viene mostrata l'implementazione di un attributo che presenta argomenti sia posizionali che denominati.  
  
### Codice  
 [!code-cs[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### Commenti  
 Nell'esempio riportato di seguito viene illustrato come applicare l'attributo personalizzato a due proprietà.  
  
### Codice  
 [!code-cs[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## Regole correlate  
 [CA1813: Evitare attributi non sealed](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## Vedere anche  
 [Attributi](../Topic/Attributes1.md)