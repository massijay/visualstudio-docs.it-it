---
title: "CA2151: I campi con tipi critici devono essere SecurityCritical | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2151: I campi con tipi critici devono essere SecurityCritical
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName||  
|CheckId|CA2151|  
|Categoria|Microsoft.Security|  
|Breaking Change|Interruzione|  
  
## Causa  
 Un campo trasparente per la sicurezza o un campo critico sicuro è dichiarato.  Il tipo è specificato come critico per la sicurezza.  Di seguito è riportato un esempio.  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      Type1 m_field; // CA2151, transparent field of critical type  
   }  
  
```  
  
 In questo esempio, `m_field` è un campo trasparente per la sicurezza di un tipo che è critico per la sicurezza.  
  
## Descrizione della regola  
 Per utilizzare i tipi critici per la sicurezza, il codice che fa riferimento al tipo deve essere critico per la sicurezza critico per la sicurezza e richiamabile da codice trasparente.  Questo vale anche se il riferimento è indiretto.  Ad esempio, quando si fa riferimento a un campo trasparente che dispone di un tipo critico, il codice deve essere critico per la sicurezza o critico per la sicurezza e richiamabile da codice trasparente.  Pertanto, un campo trasparente per la sicurezza o critico per la sicurezza e richiamabile da codice trasparente è fuorviante perché il codice trasparente non potrà comunque accedere al campo.  
  
## Come correggere le violazioni  
 Per correggere la violazione di questa regola, contrassegnare il campo con l'attributo <xref:System.Security.SecurityCriticalAttribute> oppure rendere il tipo a cui il campo fa riferimento trasparente per la sicurezza o critico per la sicurezza e richiamabile da codice trasparente.  
  
```c#  
// Fix 1: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
// Fix 2: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   class Type1 { } // Type1 is now transparent  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
```  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
### Codice  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]  
  
### Commenti