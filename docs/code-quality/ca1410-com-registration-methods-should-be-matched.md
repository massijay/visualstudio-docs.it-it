---
title: "CA1410: I metodi di registrazione COM devono corrispondere | Microsoft Docs"
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
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
helpviewer_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1410: I metodi di registrazione COM devono corrispondere
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo dichiara un metodo contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ma non dichiara un metodo contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> o viceversa.  
  
## Descrizione della regola  
 Per consentire la creazione di un tipo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] da parte dei client COM \(Component Object Model\), è necessario innanzitutto registrare il tipo.  Se disponibile, durante il processo di registrazione viene chiamato un metodo contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> per eseguire il codice specificato dall'utente.  Un metodo corrispondente contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> viene chiamato durante il processo di annullamento della registrazione per invertire le operazioni del metodo di registrazione.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere il metodo di registrazione o di annullamento della registrazione corrispondente.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  Nel codice commentato viene riportata la correzione per la violazione.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## Regole correlate  
 [CA1411: I metodi di registrazione COM non devono essere visibili](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## Vedere anche  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registering Assemblies with COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)