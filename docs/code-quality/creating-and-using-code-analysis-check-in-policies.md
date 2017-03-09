---
title: "Creazione e utilizzo di criteri di archiviazione di analisi codice | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analisi codice, criteri di archiviazione"
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 39
caps.handback.revision: 39
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Creazione e utilizzo di criteri di archiviazione di analisi codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si utilizza Team Foundation Version Control \(TFVC\), è possibile creare criteri di archiviazione dell'analisi codice per i progetti di codice .NET Framework e nativi \(C\/C\+\+\) in un progetto team.  È possibile utilizzare i criteri di archiviazione dell'analisi codice per controllare e migliorare la qualità del codice archiviato nella codebase.  
  
 I criteri vengono soddisfatti quando la compilazione locale è aggiornata e l'analisi codice è stata eseguita sui file di origine più recenti.  A un livello minimo, le regole di analisi codice abilitate nel progetto di codice devono contenere le stesse regole definite nei criteri di archiviazione del progetto team.  Le regole specificate come errori nelle impostazioni del progetto team devono essere specificate come errori anche nel progetto di codice  
  
> [!IMPORTANT]
>  I criteri di archiviazione dell'analisi del codice non possono essere applicati ai progetti di siti Web.  Possono essere applicate ai progetti di applicazioni Web.  
  
 Per creare criteri di archiviazione dell'analisi codice, utilizzare Impostazioni progetto team di [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)].  I criteri di archiviazione vengono specificati e applicati per un progetto team, ma le esecuzioni dell'analisi codice vengono configurate ed eseguite per singoli progetti di codice sui computer di sviluppo locali.  In questa sezione viene descritto come specificare criteri di archiviazione dell'analisi codice per un progetto team e come implementare criteri di analisi codice personalizzati per il codice gestito.  
  
## In questa sezione  
 [Procedura: Creare o aggiornare criteri di archiviazione standard dell'analisi del codice](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Vengono descritti i passaggi da utilizzare per impostare e modificare criteri di analisi codice per un progetto team.  
  
 [Implementazione di criteri di archiviazione personalizzati per codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Vengono descritti i passaggi da utilizzare per creare un set di regole personalizzate per i criteri di archiviazione di un progetto team e per sincronizzare i progetti di codice del progetto team con i criteri di archiviazione.  
  
 [Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Vengono illustrati i problemi di compatibilità correlati all'archiviazione dell'analisi codice tra versioni diverse di [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Procedura: Personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Viene illustrato come aggiungere parole e token al dizionario a cui viene fatto riferimento nelle regole di denominazione dell'analisi codice.  
  
## Sezioni correlate  
 [Set and Enforce Quality Gates](../Topic/Set%20and%20Enforce%20Quality%20Gates.md)  
  
 [Miglioramento della qualità del codice con i criteri di archiviazione del progetto team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)