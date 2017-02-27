---
title: "Procedura: disabilitare il processo di hosting | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "processo di hosting, disabilitazione"
  - "vshost.exe, disabilitazione del processo di hosting"
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Procedura: disabilitare il processo di hosting
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le chiamate di alcune API possono venire influenzate quando processo di hosting è abilitato.  In questi casi, è necessario disabilitare il processo di hosting per restituire i risultati corretti.  
  
### Per disabilitare il processo di hosting  
  
1.  Aprire un progetto eseguibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  I progetti che non producono file eseguibili \(ad esempio, librerie di classi o progetti di servizio\) non dispongono di questa opzione.  
  
2.  Scegliere **Proprietà** dal menu **Progetto**.  
  
3.  Fare clic sulla scheda **Debug**.  
  
4.  Deselezionare la casella di controllo **Attiva il processo di hosting di Visual Studio**.  
  
 Quando si disabilita il processo di hosting, diverse funzionalità di debug non sono disponibili o hanno prestazioni ridotte.  Per ulteriori informazioni, vedere [Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md).  
  
 In generale, quando il processo di hosting è disabilitato:  
  
-   Il tempo necessario per avviare il debug delle applicazioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] aumenta.  
  
-   La valutazione delle espressioni per la fase di progettazione non è disponibile.  
  
-   Il debug ad attendibilità parziale non è disponibile.  
  
## Vedere anche  
 [Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md)   
 [Processo di hosting \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Builds During Application Development](http://msdn.microsoft.com/it-it/c9497d62-3b7b-4449-88e8-cf27acc9efe6)