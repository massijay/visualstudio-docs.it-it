---
title: "CA2117: I tipi APTCA devono estendere solo tipi di base APTCA | Microsoft Docs"
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
  - "CA2117"
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
helpviewer_keywords: 
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
  - "CA2117"
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2117: I tipi APTCA devono estendere solo tipi di base APTCA
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|Categoria|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico o protetto in un assembly con l'attributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> eredita da un tipo dichiarato in un assembly che non presenta l'attributo.  
  
## Descrizione della regola  
 Per impostazione predefinita, i tipi pubblici o protetti in assembly con nomi sicuri sono protetti in modo implicito da [Inheritance Demands](http://msdn.microsoft.com/it-it/28b9adbb-8f08-4f10-b856-dbf59eb932d9) per l'attendibilità totale.  Gli assembly con nomi sicuri contrassegnati con l'attributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) non presentano questa sicurezza.  L'attributo disabilita la richiesta di ereditarietà.  In questo modo i tipi esposti dichiarati nell'assembly vengono resi ereditabili da tipi che non presentano l'attendibilità totale.  
  
 Quando l'attributo APTCA è presente su un assembly totalmente attendibile e un tipo nell'assembly eredita da un tipo che non consente chiamanti parzialmente attendibili, è possibile che si verifichi una violazione della sicurezza.  Se due tipi `T1` e `T2` soddisfano le seguenti condizioni, i chiamanti malintenzionati possono utilizzare il tipo `T1` per ignorare la richiesta di ereditarietà con attendibilità totale implicita che protegge `T2`:  
  
-   `T1` è un tipo pubblico dichiarato in un assembly totalmente attendibile che presenta l'attributo APTCA.  
  
-   `T1` eredita da un tipo `T2` al di fuori del relativo assembly.  
  
-   L'assembly di `T2` non presenta l'attributo APTCA e pertanto non è ereditabile da tipi in assembly parzialmente attendibili.  
  
 Un tipo parzialmente attendibile `X` può ereditare da `T1` e ottenere pertanto accesso a membri ereditati dichiarati in `T2`.  Poiché `T2` non presenta l'attributo APTCA, il relativo tipo derivato immediato \(`T1`\) deve soddisfare una richiesta di ereditarietà per l'attendibilità totale; `T1` presenta attendibilità totale e pertanto soddisfa questo controllo.  Il rischio di sicurezza è dovuto al fatto che `X` non partecipa nel soddisfare la richiesta di ereditarietà che protegge `T2` dalle sottoclassi non attendibili.  Per questo motivo, i tipi con l'attributo APTCA non devono estendere tipi privi di questo attributo.  
  
 Un altro problema di sicurezza, forse più comune, è costituito dal fatto che il tipo derivato \(`T1`\) può, a causa di un errore del programmatore, esporre membri protetti dal tipo che richiede attendibilità totale \(`T2`\).  Quando si verifica questa situazione, i chiamanti non attendibili possono ottenere accesso a informazioni che dovrebbero essere disponibili solo a tipi completamente attendibili.  
  
## Come correggere le violazioni  
 Se il tipo segnalato dalla violazione si trova in un assembly che non richiede l'attributo APTCA, rimuoverlo.  
  
 Se l'attributo APTCA è necessario, aggiungere una richiesta di ereditarietà per l'attendibilità totale al tipo  come protezione dall'ereditarietà da parte di tipi non attendibili.  
  
 È possibile correggere una violazione aggiungendo l'attributo APTCA agli assembly dei tipi di base segnalati dalla violazione.  Non eseguire questa operazione senza aver precedentemente effettuato una revisione accurata della sicurezza di tutto il codice negli assembly e di tutto il codice che dipende dagli assembly.  
  
## Esclusione di avvisi  
 Affinché l'esclusione di un avviso da questa regola sia sicura, è necessario assicurarsi che i membri protetti esposti dal tipo non consentano direttamente o indirettamente a chiamanti non attendibili di accedere a informazioni, operazioni o risorse riservate che possano essere utilizzate in modo distruttivo.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono utilizzati due assembly e un'applicazione di test per illustrare la vulnerabilità della sicurezza rilevata da questa regola.  Il primo assembly non presenta l'attributo APTCA e non deve essere ereditabile da tipi parzialmente attendibili \(rappresentato da `T2` nella spiegazione precedente\).  
  
 [!code-cs[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## Esempio  
 Il secondo assembly, rappresentato da `T1` nella spiegazione precedente, è totalmente attendibile e consente l'accesso a chiamanti parzialmente attendibili.  
  
 [!code-cs[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]  
  
## Esempio  
 Il tipo di test, rappresentato da `X` nella spiegazione precedente, è contenuto in un assembly parzialmente attendibile.  
  
 [!code-cs[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **Meet at the shady glen 2\/22\/2003 12:00:00 AM\!**  
**From Test: sunny meadow**  
**Meet at the sunny meadow 2\/22\/2003 12:00:00 AM\!**   
## Regole correlate  
 [CA2116: I metodi APTCA devono chiamare solo metodi APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)  
  
## Vedere anche  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/it-it/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Using Libraries from Partially Trusted Code](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Inheritance Demands](http://msdn.microsoft.com/it-it/28b9adbb-8f08-4f10-b856-dbf59eb932d9)