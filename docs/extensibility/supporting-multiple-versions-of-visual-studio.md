---
title: "Supporto di pi&#249; versioni di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio, il supporto di più versioni"
  - "Package VS, compatibilità side-by-side"
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Supporto di pi&#249; versioni di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il termine *side\-by\-side* significa che è possibile installare e gestire più versioni di un prodotto nello stesso computer. Per i package VS, che significa che un utente può avere diverse versioni di Visual Studio installate nello stesso computer. Tuttavia, è possibile avere versioni side\-by\-side del package VS caricati in una sola versione di Visual Studio.  
  
 Prima di eseguire il pacchetto Visual Studio in grado di essere caricato in versioni side\-by\-side di Visual Studio, considerare quanto segue:  
  
-   È necessario determinare la strategia di implementazione side\-by\-side che si desidera seguire.  
  
     Per altre informazioni, vedere [Scelta tra i package VS condivisi e con controllo delle versioni](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   I formati di file di soluzione e progetto devono superare la strategia di implementazione.  
  
     Per altre informazioni, vedere [Aggiornamento di progetti personalizzati](../misc/upgrading-custom-projects.md) e [Registrazione di estensioni di File per le distribuzioni Side\-By\-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Il programma di installazione deve gestire la strategia di implementazione in modo che i componenti con controllo delle versioni e componenti condivisi da tutte le versioni, sono correttamente installati e registrati.  
  
     Per ulteriori informazioni, vedere [L'installazione di VS con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [Gestione dei componenti](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Una versione di Visual Studio viene installata anche una versione corrispondente di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Ad esempio, Visual Studio 2010 e Visual Studio 2012 nello stesso computer viene installata anche versioni 4.0 e 4.5 di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], rispettivamente.  
  
## In questa sezione  
 [Scelta tra i package VS condivisi e con controllo delle versioni](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Viene descritto come risolvere i problemi relativi side\-by\-side di VSPackage.  
  
 [Registrazione di estensioni di File per le distribuzioni Side\-By\-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Viene descritto come il VSPackage può registrare le associazioni di file in uno scenario side\-by\-side.  
  
## Sezioni correlate  
 [Installazione di VSPackage](../misc/installing-vspackages.md)  
 Viene illustrato come creare e installare i package VS e come supportare gli utenti che eseguono più versioni di Visual Studio nello stesso momento.