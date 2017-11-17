---
title: Analisi del codice per codice gestito Panoramica | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eebc25b344e603cb66546db6d9179067d5995496
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="code-analysis-for-managed-code-overview"></a>Panoramica dell'analisi codice gestito
L'analisi del codice gestito analizza gli assembly gestiti e fornisce informazioni sugli assembly, ad esempio le violazioni delle regole di programmazione e progettazione definite nelle linee guida di progettazione di Microsoft .NET Framework.  
  
 Lo strumento di analisi rappresenta i controlli eseguiti durante un'analisi come messaggi di avviso. I messaggi di avviso identificano eventuali problemi di programmazione e progettazione e, se possibile, forniscono informazioni su come risolverli.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (Integrated Development Environment)  
 Gli sviluppatori possono eseguire l'analisi del codice del progetto automaticamente o manualmente.  
  
 Per eseguire l'analisi codice ogni volta che si compila un progetto, si seleziona **Attiva analisi codice in fase di compilazione (definisce la costante CODE_ANALYSIS)** nella pagina delle proprietà del progetto. Per ulteriori informazioni, vedere [procedura: abilitare e disabilitare analisi del codice automatica](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Per eseguire l'analisi codice manualmente in un progetto, scegliere il **Analizza** menu, fare clic su **Esegui analisi del codice su***ProjectName*. Per ulteriori informazioni, vedere [procedura: abilitare e disabilitare analisi del codice automatica](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## <a name="rule-sets"></a>Set di regole  
 Regole di analisi del codice per il codice gestito raggruppate in *set di regole*. È possibile utilizzare uno dei set di regole standard Microsoft oppure creare un set di regole personalizzato per soddisfare una specifica esigenza. Per ulteriori informazioni, vedere [utilizzando il set di regole per raggruppare regole di analisi codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## <a name="in-source-suppression"></a>Eliminazione nell'origine  
 È in genere utile indicare se un avviso non è applicabile. In questo modo lo sviluppatore e altri individui che potrebbero rivedere il codice in un secondo momento verranno informati del fatto che un avviso è stato sottoposto ad analisi, quindi è stato eliminato o ignorato.  
  
 L'eliminazione nell'origine degli avvisi viene implementata attraverso attributi personalizzati. Per non visualizzare un avviso, aggiungere l'attributo `SuppressMessage` al codice sorgente, come illustrato nell'esempio seguente:  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Per ulteriori informazioni, vedere [esclusione di avvisi mediante l'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Eseguire l'analisi del codice come parte dei criteri di archiviazione  
 Le organizzazioni richiedono talvolta che tutte le archiviazioni soddisfino determinati criteri, tra cui, in particolare:  
  
-   Assenza di errori di compilazione nel codice da archiviare.  
  
-   Esecuzione dell'analisi del codice durante la compilazione più recente.  
  
 A tale scopo, è utile quindi definire dei criteri specifici per l'archiviazione. Per ulteriori informazioni, vedere [miglioramento della qualità del codice con i criteri di archiviazione del progetto Team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Integrazione di Team Build  
 È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi come parte del processo di compilazione. Per altre informazioni, vedere [Build the application](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692) (Compilare l'applicazione).  
  
## <a name="see-also"></a>Vedere anche  
 [Regola di utilizzo di set per raggruppare regole di analisi codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Procedura: abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)