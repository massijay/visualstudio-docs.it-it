---
title: 'CA2142: Il codice Transparent non deve essere protetto con LinkDemand | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d0b9712ec0ed9d5ecd8e76b1ecf208505f07623
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Il codice Transparent non deve essere protetto con LinkDemand
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|Categoria|Microsoft.Security|  
|Breaking Change|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo trasparente richiede un <xref:System.Security.Permissions.SecurityAction> o un'altra richiesta di sicurezza.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola funziona su metodi trasparenti di cui richiedono a LinkDemands l'accesso. Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Poiché i metodi transparent dovrebbero essere indipendente dalla sicurezza, essi devono prendere le decisioni di sicurezza. Inoltre, il codice SafeCritical, quale decisioni di protezione, non deve basarsi sul codice trasparente per apportate in precedenza questa decisione.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere la richiesta di collegamento sul metodo trasparente o contrassegnare il metodo con <xref:System.Security.SecuritySafeCriticalAttribute> controlla attributo se le prestazioni di sicurezza, ad esempio richieste di sicurezza.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, la regola viene attivata sul metodo perché non è visibile ed è contrassegnato con un LinkDemand <xref:System.Security.PermissionSet> che contiene un <xref:System.Security.Permissions.SecurityAction>.  
  
 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 Non escludere un avviso da questa regola.