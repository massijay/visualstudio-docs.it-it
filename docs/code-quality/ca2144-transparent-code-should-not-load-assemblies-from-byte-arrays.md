---
title: 'CA2144: Il codice Transparent non deve caricare assembly da matrici di byte | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6eb3b2ade52f0870240db1fac24f0ab3f6c6de17
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: Il codice Transparent non deve caricare assembly da matrici di byte
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|  
|CheckId|CA2144|  
|Categoria|Microsoft.Security|  
|Breaking Change|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo trasparente carica un assembly da una matrice di byte utilizzando uno dei metodi seguenti:  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
## <a name="rule-description"></a>Descrizione della regola  
 La revisione di sicurezza per il codice trasparente non è accurata come la revisione di sicurezza per il codice critico, perché il primo non può eseguire azioni sensibili per la sicurezza. Assembly caricati da una matrice di byte potrebbero non essere notati nel codice trasparente e quella matrice di byte potrebbe contenere codice critico o ancora più importante codice critico per la sicurezza, che deve essere controllato. Pertanto, il codice transparent non deve caricare assembly da una matrice di byte.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, contrassegnare il metodo che carica l'assembly con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 La regola viene attivata nel codice riportato di seguito perché un metodo trasparente carica un assembly da una matrice di byte.  
  
 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]