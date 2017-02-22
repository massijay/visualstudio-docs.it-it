---
title: "Procedura: eseguire il debug di DLL native | Microsoft Docs"
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
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug di DLL"
  - "DLL, debug"
  - "file eseguibili, specifica per sessioni di debug"
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: eseguire il debug di DLL native
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere Importa\/Esporta impostazioni dal menu Strumenti.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Il debug di una DLL può essere avviato:  
  
-   Dal progetto utilizzato per la creazione dell'eseguibile che chiama la DLL.  
  
 \-oppure\-  
  
-   Dal progetto stesso utilizzato per la creazione della DLL.  
  
 Se si dispone del progetto utilizzato per la creazione dell'eseguibile, iniziare il debug da tale progetto.  Sarà quindi possibile aprire un file di origine relativo alla DLL e impostare i punti di interruzione in tale file, anche se non appartiene al progetto utilizzato per la creazione dell'eseguibile.  Per ulteriori informazioni, vedere [Punti di interruzione](http://msdn.microsoft.com/it-it/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
 Se il debug viene avviato dal progetto che crea la DLL, è necessario specificare l'eseguibile che si desidera utilizzare per il debug della DLL.  
  
### Per specificare un eseguibile per la sessione di debug  
  
1.  In **Esplora soluzioni** selezionare il progetto che crea la DLL.  
  
2.  Scegliere **Pagine delle proprietà** dal menu **Visualizza**.  
  
3.  Nella finestra di dialogo **Pagine delle proprietà** aprire la cartella **Proprietà di configurazione** e selezionare la categoria **Debug**.  
  
4.  Nella casella **Comando** specificare il percorso del contenitore.  Ad esempio, C:\\Programmi\\Applicazione\\APP.EXE.  
  
5.  Nella casella **Argomenti del comando** specificare tutti gli argomenti necessari per l'eseguibile.  
  
 Se non si specifica l'eseguibile nella finestra di dialogo **Pagine delle proprietà** di *Project*, all'avvio del debug verrà visualizzata la finestra di dialogo [Eseguibile per la sessione di debug](../debugger/executable-for-debugging-session-dialog-box.md).  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)