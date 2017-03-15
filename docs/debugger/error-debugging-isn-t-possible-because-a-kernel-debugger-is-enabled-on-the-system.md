---
title: "Errore: impossibile eseguire il debug perch&#233; nel sistema &#232; attivato un debugger del kernel | Microsoft Docs"
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
  - "vs.debug.error.kernel_dbg_enabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger del kernel"
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: impossibile eseguire il debug perch&#233; nel sistema &#232; attivato un debugger del kernel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si esegue il debug del codice gestito, è possibile che venga visualizzato il seguente messaggio di errore:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Questo messaggio viene visualizzato quando si tenta di eseguire il debug di codice gestito:  
  
-   in un sistema [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] o [!INCLUDE[win7](../debugger/includes/win7_md.md)] avviato in modalità debug.  
  
-   l'applicazione utilizzare CLR versione CLR 2.0, 3.0 o 3.5.  
  
## Soluzione  
  
#### Per risolvere il problema  
  
-   Aggiornare l'applicazione per utilizzare CLR versione 4.0 o 4.5  
  
     \-oppure\-  
  
-   Disabilitare il debug del kernel ed eseguire il debug in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     \-oppure\-  
  
-   Eseguire il debug con il debugger del kernel anziché [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     \-oppure\-  
  
-   Nel debugger del kernel disabilitare le eccezioni in modalità utente.  
  
#### Per disabilitare il debug del kernel nella sessione corrente  
  
-   Al prompt dei comandi digitare:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### Per disabilitare il debug del kernel per tutte le sessioni \(Windows Vista e Windows 7\)  
  
1.  Al prompt dei comandi digitare:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  Riavviare il computer.  
  
#### Per disabilitare il debug del kernel per tutte le sessioni \(altri sistemi operativi Windows\)  
  
1.  Individuare boot.ini nell'unità di sistema, in genere C:\\.  Il file boot.ini potrebbe essere nascosto e di sola lettura.  Per visualizzarlo, è pertanto necessario utilizzare il seguente comando:  
  
    ```  
    dir /ASH  
    ```  
  
2.  Aprire boot.ini utilizzando Blocco note e rimuovere le seguenti opzioni:  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  Riavviare il computer.  
  
#### Per eseguire il debug con il debugger del kernel  
  
1.  Se il debugger del kernel è collegato, verrà visualizzato un messaggio che chiede se si desidera continuare a eseguire il debug.  Scegliere il pulsante per continuare.  
  
2.  È possibile che venga generata un'eccezione `User break exception(Int 3).`. In questo caso, digitare il seguente comando del debugger del kernel per continuare a eseguire il debug:  
  
     `gn`  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice gestito](../debugger/debugging-managed-code.md)