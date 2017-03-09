---
title: "CA1014: Contrassegnare gli assembly con CLSCompliantAttribute | Microsoft Docs"
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
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
helpviewer_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1014: Contrassegnare gli assembly con CLSCompliantAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 A un assembly non è applicato l'attributo <xref:System.CLSCompliantAttribute?displayProperty=fullName>.  
  
## Descrizione della regola  
 In Common Language Specification \(CLS\) vengono definite limitazioni di denominazione, tipi di dati e regole che gli assembly devono rispettare per poter essere utilizzati tra diversi linguaggi di programmazione.  In una buona programmazione tutti gli assembly devono indicare in modo esplicito la conformità CLS all'oggetto <xref:System.CLSCompliantAttribute>.  Se l'attributo non è presente su un assembly, tale assembly non è conforme.  
  
 È possibile che un assembly conforme a CLS contenga tipi o membri di tipi non compatibili.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly.  Anziché contrassegnare l'intero assembly come non conforme, è opportuno determinare quali tipi o membri di tipi non sono conformi e contrassegnarli come tali.  Se possibile, è opportuno fornire un'alternativa conforme a CLS per i membri non conformi in modo che il maggior numero possibile di destinatari possa accedere a tutte le funzionalità dell'assembly.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Se non si desidera che l'assembly sia conforme, applicare l'attributo e impostare il relativo valore su `false`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un assembly con l'attributo <xref:System.CLSCompliantAttribute?displayProperty=fullName> applicato che lo dichiara come conforme a CLS.  
  
 [!code-cs[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## Vedere anche  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)