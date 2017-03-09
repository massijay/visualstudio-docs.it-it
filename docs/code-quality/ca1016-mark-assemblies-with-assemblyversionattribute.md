---
title: "CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute | Microsoft Docs"
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
  - "MarkAssembliesWithAssemblyVersion"
  - "CA1016"
helpviewer_keywords: 
  - "CA1016"
  - "MarkAssembliesWithAssemblyVersion"
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 L'assembly non dispone di un numero di versione.  
  
## Descrizione della regola  
 L'identità di un assembly è composta dalle informazioni riportate di seguito:  
  
-   Nome assembly  
  
-   Numero di versione  
  
-   Impostazioni cultura  
  
-   Chiave pubblica \(per assembly con nome sicuro\).  
  
 In [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] viene utilizzato il numero di versione per identificare in modo univoco un assembly e per stabilire associazioni a tipi in assembly con nome sicuro.  Il numero di versione viene utilizzato insieme ai criteri di versione ed editore.  Per impostazione predefinita, le applicazioni vengono eseguite solo con la versione di assembly con cui sono state compilate.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere un numero di versione all'assembly utilizzando l'attributo <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>.  Vedere l'esempio che segue.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola per gli assembly utilizzati da terze parti o in un ambiente di produzione.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un assembly a cui è applicato l'attributo <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 [!code-cs[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## Vedere anche  
 [Controllo delle versioni degli assembly](../Topic/Assembly%20Versioning.md)   
 [Procedura: creare criteri editore](../Topic/How%20to:%20Create%20a%20Publisher%20Policy.md)