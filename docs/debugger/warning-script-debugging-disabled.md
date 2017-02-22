---
title: "Avviso: debug degli script disabilitato | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.scriptdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Avviso: debug degli script disabilitato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debug degli script è attualmente disabilitato in Internet Explorer  
  
 Questo avviso viene visualizzato quando si tenta di eseguire il debug dello script senza abilitare il debug degli script in Internet Explorer.  Per motivi di sicurezza, il debug degli script è disabilitato in Internet Explorer per impostazione predefinita.  
  
### Per abilitare il debug di script in Internet Explorer  
  
1.  Scegliere **Opzioni Internet** dal menu **Strumenti** di Internet Explorer.  
  
2.  Nella finestra di dialogo **Opzioni Internet** scegliere la scheda **Avanzate**.  
  
3.  Nella casella **Impostazioni** della scheda **Avanzate**, cercare la categoria **Esplorazione**.  
  
4.  Deselezionare **Disabilita debugging degli script \(Internet Explorer\)**.  
  
5.  Scegliere **OK**.  
  
6.  Chiudere e riavviare Internet Explorer.  
  
     Le nuove impostazioni risulteranno ora attive.  
  
## Vedere anche  
 [Procedura: connettersi a file script](../debugger/how-to-attach-to-script.md)