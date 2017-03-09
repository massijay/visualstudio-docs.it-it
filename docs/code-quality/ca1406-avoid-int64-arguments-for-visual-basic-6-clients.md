---
title: "CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
helpviewer_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo specificatamente contrassegnato come visibile a Component Object Model \(COM\) dichiara un membro che accetta un argomento <xref:System.Int64?displayProperty=fullName>.  
  
## Descrizione della regola  
 I client COM Visual Basic 6 non sono in grado di accedere a Integer a 64 bit.  
  
 Per impostazione predefinita, i seguenti elementi sono visibili a COM: assembly, tipi pubblici, membri di istanza pubblici in tipi pubblici e tutti i membri di tipi di valore pubblici.  Per ridurre i falsi positivi, tuttavia, la regola richiede che la visibilità COM del tipo sia dichiarata esplicitamente. L'assembly che lo contiene deve essere contrassegnato dall'impostazione dell'oggetto <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> su `false` mentre il tipo deve essere contrassegnato dall'impostazione dell'oggetto <xref:System.Runtime.InteropServices.ComVisibleAttribute> su `true`.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola per un parametro il cui valore può sempre essere espresso come integrale a 32 bit, modificare il tipo di parametro in <xref:System.Int32?displayProperty=fullName>.  Se il valore del parametro può essere maggiore di quanto è possibile esprimere con un integrale a 32 bit, modificare il tipo di parametro in <xref:System.Decimal?displayProperty=fullName>.  Si noti che sia per <xref:System.Single?displayProperty=fullName> che per <xref:System.Double?displayProperty=fullName> si determina una riduzione della precisione in corrispondenza degli intervalli superiori del tipo di dati <xref:System.Int64>.  Se non si intende rendere il membro visibile a COM, contrassegnarlo impostando <xref:System.Runtime.InteropServices.ComVisibleAttribute> su `false`.  
  
## Esclusione di avvisi  
 È possibile escludere senza rischi un avviso da questa regola se si è certi che i client COM Visual Basic 6 non accederanno al tipo.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  
  
 [!code-cs[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## Regole correlate  
 [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Vedere anche  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)