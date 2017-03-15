---
title: "How to: Specify Verbose Log Files for ClickOnce Deployments | Microsoft Docs"
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
  - "logs, ClickOnce deployment"
  - "ClickOnce deployment, logging"
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Specify Verbose Log Files for ClickOnce Deployments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vengono gestiti file di log di attività di tutte le distribuzioni.  In questi file di log vengono registrati i dettagli relativi a di installazione, inizializzazione, aggiornamento e disinstallazione di una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Per aumentare il dettaglio delle informazioni scritte da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in questi file di log, utilizzare l'Editor del Registro di sistema \(**regedit.exe**\) per specificare il livello di dettaglio.  
  
> [!CAUTION]
>  L'utilizzo non corretto dell'Editor del Registro di sistema può causare gravi problemi che possono richiedere la reinstallazione del sistema operativo.  Utilizzare l'Editor del Registro di sistema sotto la propria responsabilità.  
  
 Nella procedura riportata di seguito viene descritto come specificare il livello di dettaglio per i file di log di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per l'utente corrente.  Per ridurre il livello di dettaglio, rimuovere questo valore del Registro di sistema.  
  
### Per specificare file di log dettagliati  
  
1.  Aprire **Regedit.exe**.  
  
2.  Spostarsi sul nodo `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Se necessario, creare un nuovo valore di stringa denominato `LogVerbosityLevel`.  
  
4.  Impostare il valore `LogVerbosityLevel` su `1`.  
  
## Vedere anche  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)