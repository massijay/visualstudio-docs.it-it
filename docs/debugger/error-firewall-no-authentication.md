---
title: "Errore: nessuna autenticazione del firewall | Microsoft Docs"
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
  - "vs.debug.error.firewall.noauth"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: nessuna autenticazione del firewall
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nel computer remoto Windows Firewall non è configurato in modo da consentire il debug remoto.  Per il debug remoto con `No Authentication` è necessario aggiungere msvsmon.exe all'elenco delle eccezioni.  Potrebbe inoltre essere necessario aprire alcune porte IPSEC.  
  
> [!NOTE]
>  Il debugger remoto esegue automaticamente la configurazione di Windows Firewall.  Quando si utilizza un firewall diverso da Windows Firewall, ad esempio un firewall hardware o software di terze parti, è necessario configurarlo manualmente per consentire il debug remoto.  A tale scopo, consentire il traffico sulle porte TCP\/IP su cui msvsmon.exe è in ascolto.  Per impostazione predefinita, si tratta delle porte 4018 e 4019, dove la 4018 è utilizzata in tutti i sistemi operativi e la 4019 è utilizzata solo in Windows x64 per consentire i processi di debug x86.  
  
 Per ulteriori informazioni, vedere [Impostare Remote Tools sul dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).