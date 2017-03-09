---
title: "CA1412: Contrassegnare le interfacce ComSource come IDispatch | Microsoft Docs"
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
  - "MarkComSourceInterfacesAsIDispatch"
  - "CA1412"
helpviewer_keywords: 
  - "CA1412"
  - "MarkComSourceInterfacesAsIDispatch"
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1412: Contrassegnare le interfacce ComSource come IDispatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo è contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> e almeno una delle interfacce specificate non è contrassegnata con l'attributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> impostato sul valore di `InterfaceIsDispatch`.  
  
## Descrizione della regola  
 L'oggetto <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> consente di identificare le interfacce di eventi che una classe espone ai client COM \(Component Object Model\).  Tali interfacce devono essere esposte come `InterfaceIsIDispatch` per consentire ai client COM di Visual Basic 6 di ricevere notifiche di eventi.  Per impostazione predefinita, se un'interfaccia non viene contrassegnata dall'attributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, essa viene esposta come interfaccia duale.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere o modificare l'attributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> in modo che il relativo valore sia impostato su InterfaceIsIDispatch per tutte le interfacce specificate con l'attributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio illustrato di seguito viene visualizzata una classe in cui una delle interfacce viola la regola.  
  
 [!code-cs[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## Regole correlate  
 [CA1408: Non utilizzare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## Vedere anche  
 [How to: Raise Events Handled by a COM Sink](http://msdn.microsoft.com/it-it/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)