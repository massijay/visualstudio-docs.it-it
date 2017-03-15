---
title: "CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM | Microsoft Docs"
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
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
helpviewer_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo di valore specificatamente contrassegnato come visibile a COM \(Component Object Model\) dichiara un campo di istanza non pubblico.  
  
## Descrizione della regola  
 I campi di istanza non pubblici di tipi di valori visibili a COM sono visibili ai client COM.  Esaminare il contenuto del campo alla ricerca di informazioni che non devono essere esposte o che avranno un impatto non previsto sulla progettazione o la sicurezza.  
  
 Per impostazione predefinita, tutti i tipi di valori pubblici sono visibili a COM.  Per ridurre i falsi positivi, tuttavia, la regola richiede che la visibilità COM del tipo sia dichiarata esplicitamente.  È necessario che l'assembly contenitore sia contrassegnato con <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> impostato su `false` e che il tipo sia contrassegnato con <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `true`.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola e mantenere il campo nascosto, modificare il tipo di valore in un tipo di riferimento oppure rimuovere l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> dal tipo.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se l'esposizione pubblica del campo è accettabile.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  
  
 [!code-cs[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## Regole correlate  
 [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Vedere anche  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)