---
title: "CA2221: I finalizzatori devono essere protetti | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2221"
  - "FinalizersShouldBeProtected"
helpviewer_keywords: 
  - "CA2221"
  - "FinalizersShouldBeProtected"
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2221: I finalizzatori devono essere protetti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FinalizersShouldBeProtected|  
|CheckId|CA2221|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo pubblico implementa un finalizzatore che non specifica l'accesso a livello di famiglia \(protetto\).  
  
## Descrizione della regola  
 I finalizzatori devono utilizzare il modificatore di accesso a livello di famiglia.  Questa regola è applicata dai compilatori C\#, Visual Basic e Visual C\+\+.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il finalizzatore affinché sia accessibile a livello di famiglia.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Questa regola non può essere violata in alcun linguaggio .NET di livello elevato; può essere violata se si scrive in MSIL \(Microsoft Intermediate Language\).  
  
```  
// =============== CLASS MEMBERS DECLARATION ===================  
//   note that class flags, 'extends' and 'implements' clauses  
//          are provided here for information only  
  
.namespace UsageLibrary  
{  
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected  
         extends [mscorlib]System.Object  
  {  
    .method public hidebysig instance void  
            Finalize() cil managed  
    {  
  
      // Code size       1 (0x1)  
      .maxstack  0  
      IL_0000:  ret  
    } // end of method FinalizeMethodNotProtected::Finalize  
  
    .method public hidebysig specialname rtspecialname  
            instance void  .ctor() cil managed  
    {  
      // Code size       7 (0x7)  
      .maxstack  1  
      IL_0000:  ldarg.0  
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()  
      IL_0006:  ret  
    } // end of method FinalizeMethodNotProtected::.ctor  
  
  } // end of class FinalizeMethodNotProtected  
} // end of namespace  
```  
  
## Vedere anche  
 [Modello Dispose](../Topic/Dispose%20Pattern.md)