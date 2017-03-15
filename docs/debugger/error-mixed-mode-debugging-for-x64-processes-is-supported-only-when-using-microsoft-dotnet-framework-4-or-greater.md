---
title: "Errore: il debug in modalit&#224; mista per i processi x64 &#232; supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: il debug in modalit&#224; mista per i processi x64 &#232; supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per eseguire il debug di codice nativo e gestito misto in un processo a 64 bit, è necessario disporre di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versione 4.  Il debug in modalità mista dei processi a 64 bit con versioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] precedenti alla 4 non è supportato.  
  
### Per correggere l'errore  
  
-   Effettuare uno dei passaggi riportati di seguito.  
  
    -   Aggiornare [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] alla versione 4.  
  
    -   Compilare una versione a 32 bit dell'applicazione per il debug.  
  
## Vedere anche  
 [Impostare Remote Tools sul dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)