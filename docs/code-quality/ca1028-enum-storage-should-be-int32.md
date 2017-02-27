---
title: "CA1028: L&#39;archivio di enum deve essere Int32 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
helpviewer_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1028: L&#39;archivio di enum deve essere Int32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Il tipo sottostante di un'enumerazione pubblica non è <xref:System.Int32?displayProperty=fullName>.  
  
## Descrizione della regola  
 Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate.  Per impostazione predefinita, il tipo di dati <xref:System.Int32?displayProperty=fullName> viene utilizzato per archiviare il valore costante.  Anche se è possibile modificare questo tipo sottostante, non è necessario né consigliato nella maggior parte degli scenari.  Si noti che l'utilizzo di un tipo di dati di dimensioni inferiori a <xref:System.Int32> non comporta vantaggi significativi in termini di prestazioni.  Se non è possibile utilizzare il tipo di dati predefinito, è opportuno utilizzare uno dei tipi integrali conformi a Common Language System \(CLS\), <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> o <xref:System.Int64> per assicurare che tutti i valori dell'enumerazione possano essere rappresentanti nei linguaggi di programmazione conformi a CLS.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, a meno che non esistano problemi di dimensioni o di compatibilità, utilizzare <xref:System.Int32>.  Nelle situazioni in cui le dimensioni di <xref:System.Int32> non sono sufficienti per contenere i valori, utilizzare <xref:System.Int64>.  Se per compatibilità con le versioni precedenti è richiesto un tipo di dati di dimensioni inferiori, utilizzare <xref:System.Byte> o <xref:System.Int16>.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola solo se richiesto per problemi di compatibilità con le versioni precedenti.  Nelle applicazioni, la mancata conformità a questa regola non causa in genere problemi.  Nelle librerie in cui è richiesta l'interoperabilità dei linguaggi, la mancata conformità a questa regola può influire negativamente sugli utenti.  
  
## Esempio di una violazione  
  
### Descrizione  
 Nell'esempio riportato di seguito vengono illustrate due enumerazioni che non utilizzano il tipo di dati sottostante consigliato.  
  
### Codice  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-cs[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## Esempio di correzione  
  
### Descrizione  
 Nell'esempio seguente viene corretta la violazione precedente modificando il tipo di dati sottostante in <xref:System.Int32>.  
  
### Codice  
 [!code-cs[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## Regole correlate  
 [CA1008: Gli enum devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: Non utilizzare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## Vedere anche  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>