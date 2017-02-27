---
title: "CA1031: Non rilevare tipi di eccezione generali | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1031"
  - "DoNotCatchGeneralExceptionTypes"
helpviewer_keywords: 
  - "CA1031"
  - "DoNotCatchGeneralExceptionTypes"
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1031: Non rilevare tipi di eccezione generali
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCatchGeneralExceptionTypes|  
|CheckId|CA1031|  
|Categoria|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un'eccezione generale quale <xref:System.Exception?displayProperty=fullName> o <xref:System.SystemException?displayProperty=fullName> viene rilevata in un'istruzione `catch` oppure viene utilizzata una clausola catch generale come `catch()`.  
  
## Descrizione della regola  
 Le eccezioni generali non devono essere rilevate.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rilevare un'eccezione più specifica o generare nuovamente l'eccezione generale come ultima istruzione nel blocco `catch`.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Il rilevamento di tipi di eccezioni generali può nascondere i problemi di runtime all'utente della libreria e complicare il debug.  
  
> [!NOTE]
>  A partire da [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], il Common Language Runtime \(CLR\) non recapita più eccezioni di stato danneggiato che si verifichino nel sistema operativo e nel codice gestito, ad esempio le violazioni di accesso in [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], per essere trattato dal codice gestito.  Se si desidera compilare un'applicazione in [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] \(o versioni successive\) e gestire le eccezioni di stato danneggiate, è possibile applicare l'attributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> al metodo che gestisce l'eccezione di stato danneggiata.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola questa regola e un tipo che implementa correttamente il blocco `catch`.  
  
 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-cs[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]  
  
## Regole correlate  
 [CA2200: Eseguire il rethrow per conservare i dettagli dello stack](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)