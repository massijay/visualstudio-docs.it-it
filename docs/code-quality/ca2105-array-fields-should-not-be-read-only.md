---
title: "CA2105: I campi di matrici non devono essere di sola lettura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2105"
  - "ArrayFieldsShouldNotBeReadOnly"
helpviewer_keywords: 
  - "ArrayFieldsShouldNotBeReadOnly"
  - "CA2105"
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2105: I campi di matrici non devono essere di sola lettura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ArrayFieldsShouldNotBeReadOnly|  
|CheckId|CA2105|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un campo pubblico o protetto che contiene una matrice è dichiarato in sola lettura.  
  
## Descrizione della regola  
 Quando si applica il modificatore `readonly` \(`ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) a un campo contenente una matrice, il campo non può essere modificato affinché faccia riferimento a un'altra matrice.  È tuttavia possibile modificare gli elementi della matrice archiviati in un campo in sola lettura.  Il codice con il quale si effettuano scelte o si eseguono operazioni in base agli elementi di una matrice in sola lettura accessibile pubblicamente potrebbe essere vulnerabile dal punto di vista della sicurezza.  
  
 Si noti che la presenza di un campo pubblico viola anche la regola di progettazione [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
## Come correggere le violazioni  
 Per correggere la vulnerabilità di sicurezza identificata da questa regola, non basarsi sul contenuto di una matrice in sola lettura accessibile pubblicamente.  È consigliabile eseguire una delle procedure riportate di seguito:  
  
-   Sostituire la matrice con una raccolta fortemente tipizzata non modificabile.  Per ulteriori informazioni, vedere <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.  
  
-   Sostituire il campo pubblico con un metodo che restituisca un duplicato di una matrice privata.  Poiché il codice non si basa sul duplicato, non vi è pericolo nel caso gli elementi vengano modificati.  
  
 Se si sceglie il secondo approccio, non sostituire il campo con una proprietà; le proprietà che restituiscono matrici influiscono negativamente sulle prestazioni.  Per ulteriori informazioni, vedere [CA1819: Le proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md).  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è vivamente sconsigliata.  Praticamente non esistono scenari in cui il contenuto di un campo in sola lettura non sia importante.  Se questo fosse il caso, rimuovere il modificatore `readonly` anziché escludere il messaggio.  
  
## Esempio  
 In questo esempio vengono illustrati i rischi derivanti dalla violazione di questa regola.  Nella prima parte è illustrata una libreria di esempio che dispone di un tipo, `MyClassWithReadOnlyArrayField`, contenente due campi \(`grades` e `privateGrades`\) non sicuri.  Il campo `grades` è pubblico e pertanto vulnerabile a qualsiasi chiamante.  Il campo `privateGrades` è privato, ma comunque vulnerabile poiché viene restituito ai chiamanti dal metodo `GetPrivateGrades`.  Il campo `securePrivateGrades` è esposto in modo sicuro dal metodo `GetSecurePrivateGrades`.  È dichiarato come privato, in conformità alle migliori pratiche di progettazione.  Nella seconda parte è illustrato del codice che modifica i valori archiviati nei membri `grades` e `privateGrades`.  
  
 Nell'esempio che segue è riportata la libreria di classi di esempio.  
  
 [!code-cs[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## Esempio  
 Nel codice riportato di seguito viene utilizzata la libreria di classi di esempio per illustrare problemi di sicurezza di matrici in sola lettura.  
  
 [!code-cs[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 Di seguito è riportato l'output dell'esempio:  
  
  **Prima della modifica: Gradi: 90, 90, 90 Gradi Privati: 90, 90, 90 Gradi Sicuri, 90, 90, 90 Dopo la modifica: Gradi: 90, 555, 90 Gradi Privati: 90, 555, 90 Gradi Sicuri, 90, 90, 90**   
## Vedere anche  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>