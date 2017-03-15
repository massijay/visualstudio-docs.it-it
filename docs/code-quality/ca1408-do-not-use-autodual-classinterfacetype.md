---
title: "CA1408: Non utilizzare AutoDual ClassInterfaceType | Microsoft Docs"
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
  - "DoNotUseAutoDualClassInterfaceType"
  - "CA1408"
helpviewer_keywords: 
  - "CA1408"
  - "DoNotUseAutoDualClassInterfaceType"
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1408: Non utilizzare AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo visibile a COM \(Component Object Model\) è contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> impostato sul valore `AutoDual` di <xref:System.Runtime.InteropServices.ClassInterfaceType>.  
  
## Descrizione della regola  
 I tipi che utilizzano un'interfaccia duale consentono l'associazione dei client a uno specifico layout di interfaccia.  Eventuali modifiche apportate in una versione futura al layout del tipo o ai tipi base interromperanno l'associazione dei client COM all'interfaccia.  Per impostazione predefinita, se l'attributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> non è specificato, viene utilizzata un'interfaccia di solo invio.  
  
 A meno che non sia specificato diversamente, tutti i tipi pubblici non generici sono visibili a COM, mentre i tipi non pubblici e generici sono invisibili.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il valore dell'attributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> nel valore `None` di <xref:System.Runtime.InteropServices.ClassInterfaceType> e definire in modo esplicito l'interfaccia.  
  
## Esclusione di avvisi  
 Non escludere un avviso per questa regola a meno che non sia certo che il layout del tipo e i relativi tipi base non verranno modificati in una versione successiva.  
  
## Esempio  
 Nell'esempio riportato di seguito sono riportate una classe che viola le regole e una nuova dichiarazione della classe per l'utilizzo di un'interfaccia esplicita.  
  
 [!code-cs[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## Regole correlate  
 [CA1403: I tipi layout automatici non devono essere visibili a COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: Contrassegnare le interfacce ComSource come IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## Vedere anche  
 [Introducing the Class Interface](http://msdn.microsoft.com/it-it/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)