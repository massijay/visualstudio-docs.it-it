---
title: "Criteri di archiviazione relativi alla compatibilit&#224; delle versioni per l&#39;analisi del codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "criteri di archiviazione, compatibilità tra versioni per l'analisi del codice"
  - "compatibilità tra versioni, analisi del codice (criteri di archiviazione)"
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# Criteri di archiviazione relativi alla compatibilit&#224; delle versioni per l&#39;analisi del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se è necessario valutare e modificare criteri di archiviazione dell'analisi del codice utilizzando versioni diverse di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], è necessario conoscere le differenze nelle modalità di valutazione dei criteri di archiviazione di [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] e [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].  
  
## Criteri di archiviazione relativi alla compatibilità delle versioni per la valutazione  
  
-   Quando i criteri di archiviazione dell'analisi del codice vengono valutati in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], tutte le regole esistenti in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ma non in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vengono ignorate.  
  
-   Quando i criteri di archiviazione dell'analisi del codice vengono valutati in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], tutte le regole esclusive di [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vengono ignorate.  
  
-   Se i criteri di archiviazione dell'analisi del codice specificano assembly di regole, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignora tutte le regole specificate dagli assembly e non riconosciute.  
  
-   Se i criteri di archiviazione dell'analisi del codice specificano assembly non riconosciuti da [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], verrà visualizzato un messaggio.  
  
## Criteri di archiviazione relativi alla compatibilità delle versioni per l'authoring  
  
-   Se si creano criteri di archiviazione dell'analisi del codice utilizzando la versione [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], non è possibile utilizzare la versione [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] per modificarli.  Inoltre, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] non è in grado di valutare i criteri.  
  
-   Se si creano criteri di archiviazione dell'analisi codice utilizzando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], è possibile utilizzare [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] per apportarvi modifiche e i criteri possono anche essere valutati da [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  Dopo aver modificato i criteri utilizzando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], non è più possibile modificarli utilizzando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].  [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] può valutare i criteri senza problemi con i nomi sicuri non corrispondenti.  
  
-   Per creare criteri di archiviazione dell'analisi codice con impostazioni delle regole valide per [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] e [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], è necessario creare tali criteri in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], apportare tutte le modifiche necessarie e salvare i criteri.  Se le modifiche alle regole sono presenti solo in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], modificare e salvare i criteri in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  
  
     Dopo aver salvato i criteri in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], non sarà più possibile modificare queste impostazioni per regole esistenti solo in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].