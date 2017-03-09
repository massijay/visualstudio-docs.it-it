---
title: "CA1402: Evitare gli overload nelle interfacce visibili a COM | Microsoft Docs"
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
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
helpviewer_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1402: Evitare gli overload nelle interfacce visibili a COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## Causa  
 Un'interfaccia visibile di COM \(Component Object Model\) dichiara i metodi sottoposti a overload.  
  
## Descrizione della regola  
 Quando i metodi sottoposti a overload vengono esposti ai client COM, solo il primo overload del metodo conserva il proprio nome.  Gli overload successivi vengono rinominati in maniera univoca aggiungendo al nome un carattere di sottolineatura '\_' e un intero che corrisponde all'ordine di dichiarazione dell'overload.  Si considerino ad esempio i metodi seguenti.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Questi metodi sono esposti ai client COM analoghi al seguente.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 I client COM Visual Basic 6 non sono in grado di implementare i metodi di interfaccia mediante un carattere di sottolineatura nel nome.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rinominare i metodi sottoposti a overload in modo che i nomi risultino univoci.  In alternativa, rendere l'interfaccia invisibile a COM modificando l'accessibilità in `internal` \(`Friend` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) oppure applicando l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> impostato su `false`.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate un'interfaccia che viola la regola e una che la soddisfa.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-cs[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## Regole correlate  
 [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Vedere anche  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)