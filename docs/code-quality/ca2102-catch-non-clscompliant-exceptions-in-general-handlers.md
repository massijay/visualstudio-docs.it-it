---
title: "CA2102: Individuare le eccezioni non conformi a CLS nei gestori generali | Microsoft Docs"
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
  - "CA2102"
  - "CatchNonClsCompliantExceptionsInGeneralHandlers"
helpviewer_keywords: 
  - "CA2102"
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2102: Individuare le eccezioni non conformi a CLS nei gestori generali
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|Category|Microsoft.Security|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un membro in un assembly che non è contrassegnato con l'attributo <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> o che è contrassegnato con `RuntimeCompatibility(WrapNonExceptionThrows = false)` contiene un blocco catch che gestisce <xref:System.Exception?displayProperty=fullName> e non contiene un blocco catch generale immediatamente successivo.  Questa regola ignora gli assembly [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Descrizione della regola  
 Un blocco catch che gestisce <xref:System.Exception> rileva tutte le eccezioni conformi a CLS \(Common Language Specification\).  Non rileva invece le eccezioni non conformi a CLS.  Le eccezioni non conformi a CLS possono essere generate da codice nativo o da codice gestito generato dall'assembler Microsoft Intermediate Language \(MSIL\).  Si noti che i compilatori C\# e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] non consentono la generazione di eccezioni non conformi a CLS e che in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tali eccezioni non vengono rilevate.  Se lo scopo del blocco catch è la gestione di tutte le eccezioni, utilizzare la seguente sintassi del blocco catch generale.  
  
-   C\#: `catch {}`  
  
-   C\+\+: `catch(...) {}` o `catch(Object^) {}`  
  
 Un'eccezione non conforme a CLS non gestita diviene un problema di sicurezza quando dal blocco catch vengono rimosse autorizzazioni concesse in precedenza.  Poiché le eccezioni non conformi a CLS non vengono intercettate, potrebbe essere eseguito un metodo dannoso che genera un'eccezione non conforme a CLS con autorizzazioni elevate.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola quando lo scopo è intercettare tutte le eccezioni, sostituire o aggiungere un blocco catch generale o contrassegnare l'assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`.  Se le autorizzazioni vengono rimosse dal blocco catch, duplicare la funzionalità nel blocco catch generale.  Se non si intende gestire tutte le eccezioni, sostituire il blocco catch che gestisce <xref:System.Exception> con blocchi catch che gestiscono i tipi di eccezione specifici.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il blocco try non contiene istruzioni che potrebbero generare un'eccezione non conforme a CLS.  Poiché il codice nativo o codice gestito potrebbe generare un'eccezione non conforme a CLS, tale scenario richiede la conoscenza di tutto il codice che può essere eseguito in tutti i percorsi di codice all'interno del blocco try.  Si noti che le eccezioni non conformi a CLS non vengono generate da Common Language Runtime.  
  
## Esempio  
 Nell'esempio riportato di seguito è illustrata una classe MSIL che genera un'eccezione non conforme a CLS.  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## Esempio  
 Nell'esempio riportato di seguito è illustrato un metodo che contiene un blocco catch generale che soddisfà la regola.  
  
 [!code-cs[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Compilare gli esempi precedenti come segue.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## Regole correlate  
 [CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## Vedere anche  
 [Eccezioni e gestione delle eccezioni](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe \(IL Assembler\)](../Topic/Ilasm.exe%20\(IL%20Assembler\).md)   
 [Overriding Security Checks](http://msdn.microsoft.com/it-it/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)