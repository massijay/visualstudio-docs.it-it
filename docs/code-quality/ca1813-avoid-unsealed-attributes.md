---
title: "CA1813: Evitare attributi non sealed | Microsoft Docs"
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
  - "CA1813"
  - "AvoidUnsealedAttributes"
helpviewer_keywords: 
  - "AvoidUnsealedAttributes"
  - "CA1813"
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1813: Evitare attributi non sealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|Category|Microsoft.Performance|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico eredita da <xref:System.Attribute?displayProperty=fullName>, non è astratto e non è sealed \(`NotInheritable` in Visual Basic\).  
  
## Descrizione della regola  
 La libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fornisce metodi per recuperare attributi personalizzati.  Per impostazione predefinita, questi metodi cercano la gerarchia di ereditarietà degli attributi; ad esempio <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> cerca il tipo di attributo specificato o qualsiasi tipo di attributo che estenda l'attributo specificato.  L'utilizzo di attributi sealed elimina la ricerca tramite la gerarchia di ereditarietà e può migliorare le prestazioni.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rendere l'attributo sealed o astratto.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura.  È opportuno eseguire questa operazione solo se si definisce la gerarchia di un attributo e non è possibile rendere l'attributo sealed o astratto.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un attributo personalizzato che soddisfa questa regola.  
  
 [!code-cs[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## Regole correlate  
 [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018: Contrassegnare gli attributi con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## Vedere anche  
 [Attributi](../Topic/Attributes1.md)