---
title: "CA1008: Gli enum devono avere valore zero | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
helpviewer_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1008: Gli enum devono avere valore zero
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale \- Quando viene richiesta l'aggiunta di un valore **None** a un'enumerazione priva di attributi flag. Sostanziale \- Quando viene richiesta la ridenominazione o l'eliminazione di qualsiasi valore di enumerazione.|  
  
## Causa  
 Un'enumerazione a cui non è applicato un attributo <xref:System.FlagsAttribute?displayProperty=fullName> non definisce un membro con un valore zero oppure un'enumerazione a cui è applicato un attributo <xref:System.FlagsAttribute> definisce un membro con un valore zero, ma il relativo nome non è "None" oppure l'enumerazione definisce più membri con valore zero.  
  
## Descrizione della regola  
 Il valore predefinito di un'enumerazione non inizializzata, come altri tipi di valore, è zero.  Un'enumerazione senza attributi flag definisce un membro con il valore zero in modo che il valore predefinito sia un valore valido dell'enumerazione.  Se appropriato, denominare il membro "None".  In caso contrario, assegnare zero al membro più frequentemente utilizzato.  Si noti che se il valore del primo membro dell'enumerazione non è impostato nella dichiarazione, il relativo valore sarà zero per impostazione predefinita.  
  
 Se un'enumerazione a cui è applicato l'attributo <xref:System.FlagsAttribute> definisce un membro con valore zero, il relativo nome deve essere "None" per indicare che nell'enumerazione non è stato impostato alcun valore.  L'utilizzo di un membro con valore zero per altri scopi è contrario all'utilizzo dell'attributo <xref:System.FlagsAttribute> in quanto gli operatori bit per bit AND e OR sono inutili con il membro.  Il valore zero dovrà pertanto essere assegnato a un solo membro.  Si noti che se sono presenti più membri con valore zero in un'enumerazione con attributi flag, `Enum.ToString()` restituirà risultati errati per i membri che non hanno valore zero.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola per enumerazioni senza attributi flag, definire un membro con valore zero. Si tratta di una modifica non sostanziale.  Per le enumerazioni con attributi flag che definiscono un membro con valore zero, denominare tale membro "None" ed eliminare qualsiasi altro membro con valore zero. Si tratta di una modifica sostanziale.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola se non per enumerazioni con attributi flag rilasciate in precedenza.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate due enumerazioni che soddisfano la regola e un'enumerazione, `BadTraceOptions`, che la viola.  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-cs[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## Regole correlate  
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: Non utilizzare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: L'archivio di enum deve essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## Vedere anche  
 <xref:System.Enum?displayProperty=fullName>