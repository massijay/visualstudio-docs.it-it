---
title: "Cenni preliminari sull&#39;analisi del codice per C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "#pragma (direttive), analisi codice"
  - "annotazioni, analisi codice"
  - "integrazione compilazione, analisi codice"
  - "C, analisi codice"
  - "analisi del codice C/C++"
  - "C++, analisi codice"
  - "criteri di archiviazione, analisi codice"
  - "strumento di analisi del codice"
  - "analisi codice, C/C++"
  - "riga di comando, analisi codice"
  - "IDE, analisi codice"
  - "pragma (direttiva), analisi codice"
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Cenni preliminari sull&#39;analisi del codice per C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lo strumento di analisi del codice C\/C\+\+ fornisce informazioni destinate agli sviluppatori sui possibili errori nel codice sorgente C\/C\+\+.  Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, l'annullamento dell'inizializzazione della memoria, le dereferenziazioni al puntatore null e le perdite di memoria e risorse.  
  
## Integrazione nell'IDE \(Integrated Development Environment\)  
 Per semplificarne l'utilizzo da parte degli sviluppatori, lo strumento di analisi è stato completamente integrato nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Durante il processo di compilazione, tutti gli avvisi generati dal codice sorgente vengono visualizzati nella finestra Elenco errori.  È possibile passare al codice sorgente che ha attivato l'avviso e visualizzare informazioni aggiuntive sulla causa e sulle possibili soluzioni al problema.  
  
## Supporto della direttiva \#pragma  
 Gli sviluppatori possono utilizzare la direttiva `#pragma` per considerare gli avvisi come errori. Abilitarli o disabilitarli ed eliminare gli avvisi per singole righe di codice.  Per ulteriori informazioni, vedere [How to: Enable and Disable Code Analysis for Specific C\/C\+\+ Warnings](http://msdn.microsoft.com/it-it/910b8518-71f1-4b2e-b012-70647795642a).  
  
## Supporto dell'annotazione  
 Le annotazioni migliorano la precisione dell'analisi del codice e  forniscono ulteriori informazioni sulle condizioni Pre e Post sui parametri di funzione e sui tipi restituiti.  Per ulteriori informazioni, vedere [Procedura: specificare informazioni aggiuntive sul codice utilizzando \_\_analysis\_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md).  
  
## Eseguire lo strumento di analisi del codice come parte dei criteri di archiviazione  
 È possibile richiedere che tutte le archiviazioni di codice sorgente soddisfino determinati criteri.  In particolare, si desidera assicurarsi che l'analisi sia stata eseguita nell'ambito della build locale più recente.  Per ulteriori informazioni sull'abilitazione dei criteri di archiviazione dell'analisi codice, vedere [Creazione e utilizzo di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md).  
  
## Integrazione di Team Build  
 È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi del codice nell'ambito del processo di compilazione di [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  Per ulteriori informazioni, vedere [Compilare l'applicazione](../Topic/Build%20the%20application.md).  
  
## Supporto dalla riga di comando.  
 Oltre all'integrazione completa all'interno dell'ambiente di sviluppo, gli sviluppatori possono utilizzare anche lo strumento di analisi dalla riga di comando, come illustrato nell'esempio seguente:  
  
 `C:\>cl /analyze Sample.cpp`