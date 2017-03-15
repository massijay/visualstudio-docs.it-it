---
title: "CA1059: I membri non devono esporre tipi concreti specifici | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
helpviewer_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1059: I membri non devono esporre tipi concreti specifici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MembersShouldNotExposeCertainConcreteTypes|  
|CheckId|CA1059|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un membro visibile esternamente è un tipo concreto specifico oppure espone tipi concreti specifici attraverso uno dei relativi parametri o valori restituiti.  Attualmente questa regola indica l'esposizione dei seguenti tipi concreti:  
  
-   Tipo derivato dall'oggetto <xref:System.Xml.XmlNode?displayProperty=fullName>.  
  
## Descrizione della regola  
 Un tipo concreto è un tipo con implementazione completa, pertanto è possibile crearne un'istanza.  Per consentire l'utilizzo diffuso del membro, sostituire il tipo concreto con l'interfaccia suggerita.  In tal modo il membro può accettare qualsiasi tipo che implementa l'interfaccia o essere utilizzato dove è previsto un tipo che implementa l'interfaccia.  
  
 Nella tabella riportata di seguito sono elencati i tipi concreti di destinazione e le relative sostituzioni consigliate.  
  
|Tipo concreto|Replacement|  
|-------------------|-----------------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Utilizzando l'istanza è possibile separare il membro da un'implementazione specifica di un'origine dati XML.|  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il tipo concreto nell'interfaccia consigliata.  
  
## Esclusione di avvisi  
 Si consiglia di escludere un messaggio dalla regola se è necessaria la funzionalità specifica fornita dal tipo concreto.  
  
## Regole correlate  
 [CA1011: Considerare il passaggio di tipi di base come parametri](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)