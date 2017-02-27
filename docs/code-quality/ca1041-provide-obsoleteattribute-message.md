---
title: "CA1041: Fornire una propriet&#224; ObsoleteAttribute.Message | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1041"
  - "ProvideObsoleteAttributeMessage"
helpviewer_keywords: 
  - "ProvideObsoleteAttributeMessage"
  - "CA1041"
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1041: Fornire una propriet&#224; ObsoleteAttribute.Message
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|CheckId|CA1041|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo o un membro è contrassegnato con un attributo <xref:System.ObsoleteAttribute?displayProperty=fullName> per cui non è specificata la proprietà <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>.  
  
## Descrizione della regola  
 L'oggetto <xref:System.ObsoleteAttribute> è utilizzato per contrassegnare tipi e membri di libreria deprecati.  Gli utenti della libreria dovrebbero evitare l'utilizzo di qualsiasi tipo o membro contrassegnato come obsoleto.  Questo si verifica perché potrebbe non essere supportato e venire rimosso dalle versioni successive della libreria.  Quando viene compilato un membro o un tipo contrassegnato utilizzando <xref:System.ObsoleteAttribute>, viene visualizzata la proprietà <xref:System.ObsoleteAttribute.Message%2A> dell'attributo.  In questo modo vengono fornite le informazioni utente sul tipo o sul membro obsoleto.  Queste informazioni includono in genere per quanto tempo il tipo o il membro obsoleto verrà supportato dai progettisti di librerie e l'elemento sostitutivo consigliato da utilizzare.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere il parametro `message` al costruttore <xref:System.ObsoleteAttribute>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola poiché la proprietà <xref:System.ObsoleteAttribute.Message%2A> fornisce informazioni essenziali sul tipo o membro obsoleto.  
  
## Esempio  
 Nell'esempio seguente viene illustrato un membro obsoleto che dispone di un oggetto <xref:System.ObsoleteAttribute> dichiarato in modo corretto.  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-cs[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## Vedere anche  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>