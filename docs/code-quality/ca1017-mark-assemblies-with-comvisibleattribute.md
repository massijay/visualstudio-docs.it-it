---
title: "CA1017: Contrassegnare gli assembly con ComVisibleAttribute | Microsoft Docs"
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
  - "CA1017"
  - "MarkAssembliesWithComVisible"
helpviewer_keywords: 
  - "MarkAssembliesWithComVisible"
  - "CA1017"
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1017: Contrassegnare gli assembly con ComVisibleAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 A un assembly non è applicato l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>.  
  
## Descrizione della regola  
 L'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> determina le modalità con cui i client COM accedono al codice gestito.  In una buona progettazione gli assembly devono indicare in modo esplicito la visibilità COM.  È possibile impostare la visibilità COM per l'intero assembly e quindi eseguirne l'override per singoli tipi e membri dei tipi.  Se l'attributo non è presente, il contenuto dell'assembly è visibile ai client COM.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly.  Se non si desidera che l'assembly sia visibile ai client COM, applicare l'attributo e impostarne il valore su `false`.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Se si desidera che l'assembly sia visibile, applicare l'attributo e impostare il valore su `true`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un assembly con l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> applicato per impedire che sia visibile ai client COM.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-cs[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## Vedere anche  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)