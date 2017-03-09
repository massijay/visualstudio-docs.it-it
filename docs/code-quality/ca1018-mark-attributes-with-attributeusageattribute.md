---
title: "CA1018: Contrassegnare gli attributi con AttributeUsageAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
helpviewer_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1018: Contrassegnare gli attributi con AttributeUsageAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 L'attributo <xref:System.AttributeUsageAttribute?displayProperty=fullName> non è presente sull'attributo personalizzato.  
  
## Descrizione della regola  
 Quando si definisce un attributo personalizzato, contrassegnarlo mediante <xref:System.AttributeUsageAttribute> per indicare la posizione nel codice sorgente in cui può essere applicato l'attributo personalizzato.  Il significato e l'utilizzo previsto di un attributo ne determinano le posizioni valide nel codice.  Ad esempio, è possibile definire un attributo che identifica la persona responsabile della gestione e del miglioramento di ogni tipo in una libreria e tale responsabilità è sempre assegnata a livello di tipo.  In questo caso, è necessario che i compilatori abilitino l'attributo in classi, enumerazioni e interfacce, ma non in metodi, eventi o proprietà.  Le procedure e i criteri organizzativi indicano se l'attributo deve essere abilitato sugli assembly.  
  
 L'enumerazione <xref:System.AttributeTargets?displayProperty=fullName> definisce le destinazioni che è possibile specificare per un attributo personalizzato.  Se si omette <xref:System.AttributeUsageAttribute>, l'attributo personalizzato sarà valido per tutte le destinazioni, come definito dal valore `All` dell'enumerazione <xref:System.AttributeTargets>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, specificare le destinazioni per l'attributo mediante <xref:System.AttributeUsageAttribute>.  Vedere l'esempio che segue.  
  
## Esclusione di avvisi  
 È consigliabile correggere la violazione di questa regola anziché escludere il messaggio.  Anche se l'attributo eredita <xref:System.AttributeUsageAttribute>, l'attributo deve essere presente per semplificare la gestione del codice.  
  
## Esempio  
 Nell'esempio seguente vengono definiti due attributi.  In `BadCodeMaintainerAttribute` è erroneamente omessa l'istruzione <xref:System.AttributeUsageAttribute> e in `GoodCodeMaintainerAttribute` viene correttamente implementato l'attributo descritto in precedenza in questa sezione.  Si noti che la proprietà `DeveloperName` è richiesta dalla regola di progettazione [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) ed è inclusa per completezza.  
  
 [!code-cs[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## Regole correlate  
 [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813: Evitare attributi non sealed](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## Vedere anche  
 [Attributi](../Topic/Attributes1.md)