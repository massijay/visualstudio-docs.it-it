---
title: "Procedura: specificare set di regole di codice gestito per pi&#249; progetti in una soluzione | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.solution"
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedura: specificare set di regole di codice gestito per pi&#249; progetti in una soluzione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per impostazione predefinita, a tutti i progetti gestiti di una soluzione viene assegnato il *set di regole* di analisi del codice relativo alle regole minime consigliate Microsoft.  È possibile modificare i set di regole assegnati ai progetti di una soluzione nella finestra di dialogo delle proprietà per la soluzione.  
  
> [!NOTE]
>  Per impostazione predefinita, l'analisi del codice di progetto non viene eseguita come istruzione di compilazione.  Per attivare l'analisi del codice come istruzione di compilazione, vedere [Procedura: Configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### Per specificare un set di regole per più progetti in una soluzione di codice gestito  
  
1.  In [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  Aprire la soluzione [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)].  
  
2.  Scegliere **Configura analisi codice per la soluzione** dal menu **Analizza**.  
  
3.  Se necessario, espandere **Proprietà comuni**, quindi fare clic su **Impostazioni analisi codice**.  
  
4.  È possibile specificare un set di regole per uno o più progetti.  
  
    -   Per specificare un set di regole per un progetto singolo, fare clic sul nome del progetto.  
  
    -   Per specificare un set di regole per più progetti, tenere premuto CTRL e fare clic sui nomi dei progetti.  
  
    -   Per specificare tutti i progetti nella soluzione, tenere premuto MAIUSC e fare clic sull'elenco dei progetti.  
  
5.  Fare clic sul campo **Set di regole** di un progetto e sul nome del set di regole che si desidera applicare.