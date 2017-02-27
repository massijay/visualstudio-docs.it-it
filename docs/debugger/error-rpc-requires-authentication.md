---
title: "Errore: RPC richiede autenticazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.rpc_requires_authentication"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Errore: RPC richiede autenticazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debugger di Visual Studio non può connettersi al computer remoto.  I criteri RPC abilitati sul computer locale impediscono il debug remoto.  
  
### Per correggere l'errore  
  
1.  Eseguire `\`*windir*`\system32\regedt32.exe`  
  
2.  Individuare ed eliminare `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Riavviare il computer per rendere effettiva la modifica del Registro di sistema.  
  
4.  Se il problema persiste, contattare l'amministratore del dominio per informazioni sull'impostazione del criterio di gruppo Configurazione computer \-\> Modelli amministrativi \-\> Sistema \-\> RPC \(Remote Procedure Call\) \-\> Restrizioni per client RPC non autenticati.