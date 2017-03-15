---
title: "CA1903: Utilizzare solo API della versione di .NET Framework di destinazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOnlyAPIFromTargetedFramework"
  - "CA1903"
helpviewer_keywords: 
  - "CA1903"
  - "UseOnlyApiFromTargetedFramework"
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# CA1903: Utilizzare solo API della versione di .NET Framework di destinazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Category|Microsoft.Portability|  
|Breaking Change|Sostanziale: in caso di generazione rispetto alla firma di un membro o tipo esternamente visibile.<br /><br /> Non sostanziale: in caso di generazione nel corpo di un metodo.|  
  
## Causa  
 Un membro o un tipo sta utilizzando un membro o un tipo introdotto in un service pack non incluso nella versione di .NET Framework di destinazione del progetto.  
  
## Descrizione della regola  
 I nuovi membri e tipi erano inclusi in .NET Framework 2.0 Service Pack 1 e 2, .NET Framework 3.0 Service Pack 1 e 2 e .NET Framework 3.5 Service Pack 1.  Progetti che vengono destinati alle versioni principali di .NET Framework possono erroneamente acquisire una dipendenza da queste nuove API.  Per impedire la dipendenza, questa regola viene eseguita in caso di utilizzo di nuovi membri e tipi non inclusi per impostazione predefinita nella versione di .NET Framework di destinazione del progetto.  
  
 **Dipendenze dalla versione di .NET Framework di destinazione e dai service pack**  
  
|||  
|-|-|  
|Quando la versione di .NET Framework di destinazione è|La regola viene eseguita in caso di utilizzo di membri introdotti in|  
|.NET Framework 2.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2|  
|.NET Framework 3,0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|N\/D|  
  
 Per modificare la versione di .NET Framework di destinazione di un progetto, vedere [Sviluppo per una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## Come correggere le violazioni  
 Per rimuovere la dipendenza dal service pack, rimuovere tutti gli utilizzi del nuovo membro o tipo.  Se la dipendenza è intenzionale, eliminare l'avviso o disattivare la regola.  
  
## Esclusione di avvisi  
 Non eliminare un avviso dalla regola se la dipendenza dal service pack specificato non è intenzionale.  In questa situazione, è possibile che l'applicazione non venga eseguita nei sistemi in cui il service pack non è installato.  Se la dipendenza è intenzionale, eliminare l'avviso o disattivare la regola.  
  
## Esempio  
 Nell'esempio seguente viene mostrata una classe che utilizza il tipo DateTimeOffset disponibile solo nella Service Pack 1 di .NET 2.0.  Questo esempio richiede che sia stato selezionato .NET Framework 2.0 nell'elenco a discesa Framework di destinazione nelle proprietà del progetto.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## Esempio  
 Nell'esempio seguente viene risolta la violazione descritta in precedenza tramite la sostituzione degli utilizzi del tipo DateTimeOffset con il tipo DateTime.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## Vedere anche  
 [Avvisi di portabilità](../code-quality/portability-warnings.md)   
 [Sviluppo per una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)