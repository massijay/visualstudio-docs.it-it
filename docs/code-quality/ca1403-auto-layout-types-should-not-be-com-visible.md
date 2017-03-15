---
title: "CA1403: I tipi layout automatici non devono essere visibili a COM | Microsoft Docs"
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
  - "AutoLayoutTypesShouldNotBeComVisible"
  - "CA1403"
helpviewer_keywords: 
  - "CA1403"
  - "AutoLayoutTypesShouldNotBeComVisible"
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1403: I tipi layout automatici non devono essere visibili a COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo valore visibile a COM \(Component Object Model\) è contrassegnato con l'attributo <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> impostato su <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
## Descrizione della regola  
 I tipi di layout <xref:System.Runtime.InteropServices.LayoutKind> sono gestiti da Common Language Runtime.  Il layout di tali tipi può variare a seconda delle versioni di .NET Framework, con conseguente compromissione delle funzionalità dei client COM che prevedono un layout specifico.  Si noti che se l'attributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> non è specificato, i compilatori C\#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e C\+\+ specificheranno il layout <xref:System.Runtime.InteropServices.LayoutKind> per i tipi di valori.  
  
 A meno che non sia specificato diversamente, tutti i tipi pubblici non generici sono visibili a COM, mentre i tipi non pubblici e generici sono invisibili.  Per ridurre i falsi positivi, tuttavia, la regola richiede che la visibilità COM del tipo sia dichiarata esplicitamente. L'assembly che lo contiene deve essere contrassegnato dall'impostazione dell'oggetto <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> su `false` mentre il tipo deve essere contrassegnato dall'impostazione dell'oggetto <xref:System.Runtime.InteropServices.ComVisibleAttribute> su `true`.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il valore dell'attributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> in <xref:System.Runtime.InteropServices.LayoutKind> o <xref:System.Runtime.InteropServices.LayoutKind> oppure rendere il tipo invisibile a COM.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati due tipi: uno che viola la regola e uno che la soddisfa.  
  
 [!code-cs[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]  
  
## Regole correlate  
 [CA1408: Non utilizzare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## Vedere anche  
 [Introducing the Class Interface](http://msdn.microsoft.com/it-it/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)