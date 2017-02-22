---
title: "CA2223: La differenza tra membri non deve limitarsi al tipo restituito | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MembersShouldDifferByMoreThanReturnType"
  - "CA2223"
helpviewer_keywords: 
  - "CA2223"
  - "MembersShouldDifferByMoreThanReturnType"
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2223: La differenza tra membri non deve limitarsi al tipo restituito
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MembersShouldDifferByMoreThanReturnType|  
|CheckId|CA2223|  
|Category|Microsoft.Usage|  
|Breaking Change|Breaking|  
  
## Causa  
 Due membri pubblici o protetti presentano firme identiche ad eccezione del tipo restituito.  
  
## Descrizione della regola  
 Nonostante il Common Language Runtime consenta l'utilizzo di tipi restituiti per differenziare membri altrimenti identici, questa funzionalità non è contenuta nella specifica CLS \(Common Language Specification\) né appartiene comunemente ai linguaggi di programmazione .NET.  Quando i membri differiscono solo per il tipo restituito, gli sviluppatori e gli strumenti di sviluppo potrebbero non essere in grado di distinguerli correttamente.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare la progettazione dei membri in modo che si basino in modo univoco esclusivamente sui relativi nomi e tipi di parametro oppure non esporre i membri.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito, in MSIL \(Microsoft Intermediate Language\), viene illustrato un tipo che viola la regola.  Si noti che questa regola non può essere violata utilizzando C\# o Visual Basic .NET.  
  
```  
  
.namespace UsageLibrary  
{  
  .class public auto ansi beforefieldinit ReturnTypeTest  
         extends [mscorlib]System.Object  
  {  
    .method public hidebysig instance int32  
            AMethod(int32 x) cil managed  
    {  
      // Code size       6 (0x6)  
      .maxstack  1  
      .locals init (int32 V_0)  
      IL_0000:  ldc.i4.0  
      IL_0001:  stloc.0  
      IL_0002:  br.s       IL_0004  
  
      IL_0004:  ldloc.0  
      IL_0005:  ret  
    } // end of method ReturnTypeTest::AMethod  
  
    .method public hidebysig instance string  
            AMethod(int32 x) cil managed  
    {  
      // Code size       10 (0xa)  
      .maxstack  1  
      .locals init (string V_0)  
      IL_0000:  ldstr      "test"  
      IL_0005:  stloc.0  
      IL_0006:  br.s       IL_0008  
  
      IL_0008:  ldloc.0  
      IL_0009:  ret  
    } // end of method ReturnTypeTest::AMethod  
  
    .method public hidebysig specialname rtspecialname  
            instance void  .ctor() cil managed  
    {  
      // Code size       7 (0x7)  
      .maxstack  1  
      IL_0000:  ldarg.0  
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()  
      IL_0006:  ret  
    } // end of method ReturnTypeTest::.ctor  
  
  } // end of class ReturnTypeTest  
  
} // end of namespace UsageLibrary  
  
```