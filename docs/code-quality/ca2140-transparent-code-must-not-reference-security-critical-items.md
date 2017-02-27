---
title: "CA2140: Il codice Transparent non deve far riferimento a elementi SecurityCritical | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2129"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
  - "CA2140"
helpviewer_keywords: 
  - "CA2129"
  - "CA2140"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA2140: Il codice Transparent non deve far riferimento a elementi SecurityCritical
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo Trasparent:  
  
-   gestisce un tipo di eccezione di sicurezza SecurityCritical  
  
-   dispone di un parametro contrassegnato come un tipo SecurityCritical  
  
-   dispone di un parametro generico con vincoli SecurityCritical  
  
-   dispone di una variabile locale di un tipo SecurityCritical  
  
-   fa riferimento a un tipo contrassegnato come SecurityCritical  
  
-   chiama un metodo contrassegnato come SecurityCritical  
  
-   fa riferimento a un campo contrassegnato come un tipo SecurityCritical  
  
-   restituisce un tipo contrassegnato come SecurityCritical  
  
## Descrizione della regola  
 Un elemento di codice contrassegnato con l'attributo <xref:System.Security.SecurityCriticalAttribute> è critico per la sicurezza.  Un metodo trasparente non può utilizzare un elemento critico per la sicurezza.  Se il tipo trasparente tenta di utilizzare un tipo SecurityCritical viene generato <xref:System.TypeAccessException>, <xref:System.MethodAccessException> o <xref:System.FieldAccessException>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, eseguire una delle seguenti azioni:  
  
-   Contrassegnare l'elemento di codice che utilizza il codice SecurityCritical con l'attributo <xref:System.Security.SecurityCriticalAttribute>  
  
     \- oppure \-  
  
-   Rimuovere l'attributo <xref:System.Security.SecurityCriticalAttribute> dagli elementi di codice contrassegnati come SecurityCritical e invece contrassegnarli con l'attributo <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityTransparentAttribute>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Negli esempi seguenti, un metodo trasparente tenta di fare riferimento a una raccolta generica, un campo e un metodo SecurityCritical.  
  
 [!code-cs[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## Vedere anche  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>