---
title: "Provider di simboli | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestore dei simboli"
  - "gestore dei simboli di debug [Debugging SDK]"
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Provider di simboli
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un'implementazione dell'analizzatore di espressioni necessario accedere alle informazioni di debug sui simboli generati dal compilatore di linguaggio per valutare le variabili ed espressioni.  Viene eseguita questa operazione tramite le interfacce di provider dei simboli \(SP\), anche chiamare un gestore dei simboli.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce lo SPs per il codice gestito e il codice nativo utilizzando il formato di file di simboli del database \(PDB\) di programma.  A meno che non sia una stretta necessità di un programma di utilizzare i simboli archiviati in un formato personalizzato, è consigliabile utilizzare lo SPs fornito da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## note di implementazione  
 I motori di debug di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]previsto per comunicare con lo SPs l'utilizzo delle interfacce \(CLR\) di Common Language Runtime.  Di conseguenza, uno SP che verrà utilizzata dai motori di debug di Visual Studio deve supportare CLR.  Un elenco completo di tutte le interfacce di debug di CLR è disponibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Se SP funziona solo con il motore di debug personalizzato, è possibile implementare SP secondo necessità in base alle esigenze del motore di debug.  
  
## Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)