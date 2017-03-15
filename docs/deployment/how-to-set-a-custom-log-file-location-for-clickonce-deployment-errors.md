---
title: "How to: Set a Custom Log File Location for ClickOnce Deployment Errors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "troubleshooting ClickOnce deployments"
  - "ClickOnce deployment, troubleshooting"
  - "ClickOnce deployment, error logging"
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Set a Custom Log File Location for ClickOnce Deployment Errors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vengono gestiti file di log di attivazione di tutte le distribuzioni.  In questi file di log vengono registrati eventuali errori di installazione e inizializzazione di una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Per impostazione predefinita, in [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene creato un file di log per ogni attivazione di distribuzione.  Questi file di log vengono archiviati nella cartella dei file temporanei Internet.  Il file di log relativo a una distribuzione viene visualizzato quando si verifica un errore di attivazione e si fa clic su **Dettagli** nella finestra di dialogo di errore risultante.  
  
 È possibile modificare questo comportamento per un client specifico utilizzando l'Editor del Registro di sistema \(**regedit.exe**\) per impostare un percorso di file di log personalizzato.  In questo caso [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registra le attivazioni riuscite e gli errori di attivazione di tutte le distribuzioni in un singolo file.  
  
> [!CAUTION]
>  L'utilizzo non corretto dell'Editor del Registro di sistema può causare gravi problemi che possono richiedere la reinstallazione del sistema operativo.  Utilizzare l'Editor del Registro di sistema sotto la propria responsabilità.  
  
> [!NOTE]
>  Sarà necessario di tanto in tanto troncare o eliminare il file di log per evitare che raggiunga dimensioni eccessive.  
  
 Nella procedura riportata di seguito viene descritto come impostare un percorso di file di log personalizzato per un singolo client.  
  
### Per impostare un percorso di file di log personalizzato  
  
1.  Aprire **Regedit.exe**.  
  
2.  Spostarsi sul nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Impostare il valore della stringa `LogFilePath` sul percorso completo personalizzato desiderato per il file di log e sul nome file.  
  
     Questo percorso deve essere una directory per la quale l'utente dispone dell'accesso in scrittura.  Ad esempio, su Windows Vista, creare la struttura di cartelle seguente e impostare `LogFilePath` su C:\\Utenti\\\<nomeutente\>\\Documenti\\Logs\\ClickOnce\\installation.log.  
  
## Vedere anche  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)