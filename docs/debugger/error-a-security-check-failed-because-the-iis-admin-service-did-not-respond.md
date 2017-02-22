---
title: "Errore: controllo di sicurezza non riuscito. Il servizio di amministrazione IIS non ha risposto | Microsoft Docs"
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
  - "vs.debug.error.iis_not_responding"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, errori dell'applicazione Web"
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: controllo di sicurezza non riuscito. Il servizio di amministrazione IIS non ha risposto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo errore si verifica quando il servizio di amministrazione IIS non risponde.  In questo modo viene indicato che l'installazione di IIS presenta un problema.  Verificare innanzitutto che il servizio sia in esecuzione tramite lo strumento **Servizi** in **Strumenti di amministrazione**.  
  
### Per correggere l'errore  
  
-   Reinstallare IIS tramite il pannello di controllo **Installazione applicazioni**.  
  
-   \- oppure \-  
  
-   Disinstallare IIS dal computer mediante Installazione applicazioni in Pannello di controllo.  Se è stato disinstallato IIS ma si verificano ancora problemi, controllare il Registro di sistema e accertarsi che questa chiave non esista più:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     \- oppure \-  
  
-   Disabilitare il servizio di amministrazione IIS tramite il pannello di controllo Strumenti di amministrazione.  In questo modo il servizio IIS verrà disabilitato sul proprio computer.  
  
     Dopo aver eseguito uno di questi tre passaggi, riavviare il computer.  
  
     Per ulteriori informazioni, vedere la documentazione relativa al servizio IIS.  
  
## Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)