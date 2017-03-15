---
title: "CA2116: I metodi APTCA devono chiamare solo metodi APTCA | Microsoft Docs"
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
  - "AptcaMethodsShouldOnlyCallAptcaMethods"
  - "CA2116"
helpviewer_keywords: 
  - "AptcaMethodsShouldOnlyCallAptcaMethods"
  - "CA2116"
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2116: I metodi APTCA devono chiamare solo metodi APTCA
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|  
|CheckId|CA2116|  
|Categoria|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo in un assembly con l'attributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> chiama un metodo in un assembly che non presenta l'attributo.  
  
## Descrizione della regola  
 Per impostazione predefinita, i metodi pubblici o protetti negli assembly con nomi sicuri sono protetti in modo implicito da [Link Demands](../Topic/Link%20Demands.md) per l'attendibilità totale; solo i chiamanti totalmente attendibili possono accedere a un assembly con nome sicuro.  Gli assembly con nomi sicuri contrassegnati con l'attributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) non presentano questa sicurezza.  L'attributo disabilita la richiesta di collegamento, rendendo l'assembly accessibile ai chiamanti non totalmente attendibili, ad esempio l'esecuzione di codice da una rete Intranet o da Internet.  
  
 Quando l'attributo APTCA è presente su un assembly totalmente attendibile e l'assembly esegue codice in un altro assembly che non consente chiamanti parzialmente attendibili, è possibile essere in presenza di una violazione della sicurezza.  Se due metodi `M1` e `M2` soddisfano le seguenti condizioni, i chiamanti malintenzionati possono utilizzare il metodo `M1` per ignorare la richiesta di collegamento di attendibilità totale implicita che protegge `M2`:  
  
-   `M1` è un metodo pubblico dichiarato in un assembly totalmente attendibile che presenta l'attributo APTCA.  
  
-   `M1` chiama un metodo `M2` al di fuori dell'assembly di `M1`.  
  
-   L'assembly di `M2` non presenta l'attributo APTCA, pertanto non deve essere eseguito da o per conto di chiamanti parzialmente attendibili.  
  
 Un chiamante parzialmente attendibile `X` può chiamare il metodo `M1` facendo in modo che `M1` chiami `M2`.  Poiché `M2` non presenta l'attributo APTCA, il relativo chiamante immediato \(`M1`\) deve soddisfare una richiesta di collegamento per l'attendibilità totale; `M1` presenta attendibilità totale e pertanto soddisfa questo controllo.  Il rischio di sicurezza è dovuto al fatto che `X` non contribuisce a soddisfare la richiesta di collegamento che protegge `M2` dai chiamanti non attendibili.  I metodi con l'attributo APTCA non devono pertanto chiamare metodi che non presentano tale attributo.  
  
## Come correggere le violazioni  
 Se è richiesto l'attributo APCTA, utilizzare una richiesta per proteggere il metodo che esegue la chiamata nell'assembly totalmente attendibile.  Le autorizzazioni esatte richieste dipendono dalla funzionalità esposta dal metodo.  Se possibile, proteggere il metodo con una richiesta di attendibilità totale per assicurare che la funzionalità sottostante non sia esposta a chiamanti parzialmente attendibili.  Se questo non è possibile, selezionare un insieme di autorizzazioni che proteggano efficacemente la funzionalità esposta.  Per ulteriori informazioni sulle domande, vedere [Demands](http://msdn.microsoft.com/it-it/e5283e28-2366-4519-b27d-ef5c1ddc1f48).  
  
## Esclusione di avvisi  
 Affinché l'esclusione di un avviso da questa regola sia sicura, è necessario assicurarsi che la funzionalità esposta dal metodo non consenta direttamente o indirettamente ai chiamanti di accedere a informazioni, operazioni o risorse riservate che possano essere utilizzate in modo distruttivo.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono utilizzati due assembly e un'applicazione di test per illustrare la vulnerabilità della sicurezza rilevata da questa regola.  Il primo assembly non presenta l'attributo APTCA e non deve essere accessibile ai chiamanti parzialmente attendibili \(rappresentato da `M2` nella spiegazione precedente\).  
  
 [!code-cs[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]  
  
## Esempio  
 Il secondo assembly è totalmente attendibile e consente l'accesso a chiamanti parzialmente attendibili \(rappresentato da `M1` nella spiegazione precedente\).  
  
 [!code-cs[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]  
  
## Esempio  
 L'applicazione di test \(rappresentata da `X` nella spiegazione precedente\) è parzialmente attendibile.  
  
 [!code-cs[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **Demand for full trust:Request failed.**  
**ClassRequiringFullTrust.DoWork was called.**   
## Regole correlate  
 [CA2117: I tipi APTCA devono estendere solo tipi di base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)  
  
## Vedere anche  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/it-it/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Using Libraries from Partially Trusted Code](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Demands](http://msdn.microsoft.com/it-it/e5283e28-2366-4519-b27d-ef5c1ddc1f48)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Dati e modellazione](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)