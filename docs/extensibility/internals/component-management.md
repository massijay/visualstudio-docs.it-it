---
title: "Gestione dei componenti | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installazione [Visual Studio SDK], componenti"
  - "installazione [Visual Studio SDK], gestione dei file"
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Gestione dei componenti
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le unità delle attività in Windows Installer sono definiti componenti di Windows Installer \(talvolta chiamate WICs o semplicemente componenti\).  Un GUID identifica ogni WIC, che è l'unità di base di installazione e di conteggio dei riferimenti per le impostazioni che utilizzano Windows Installer.  
  
 Sebbene sia possibile utilizzare diversi prodotti per creare il programma di installazione di pacchetto VS, questa discussione si presuppone l'utilizzo di file di Windows Installer \(MSI\).  Nel creare il programma di installazione, è necessario gestire correttamente la distribuzione di file in modo che il conteggio dei riferimenti corretto si verifichi sempre.  Di conseguenza, le diverse versioni del prodotto non interferiranno con o interrompersi in una combinazione di installare e disinstallare gli scenari.  
  
 In Windows Installer, il conteggio dei riferimenti si verifica al livello componente.  È necessario organizzare con attenzione i file di risorse, le voci del Registro di sistema e così via, in componenti.  Esistono altri livelli di organizzazione quali moduli, le funzionalità e prodotti \- che possono aiutare in scenari diversi.  Per ulteriori informazioni, vedere [Nozioni di base di Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## Linee guida di installazione di creazione per l'installazione affiancata  
  
-   I file e le chiavi del Registro di sistema creator condivisi tra le versioni nelle proprie componenti.  
  
     Ciò consente facilmente utilizzarli nella versione successiva.  Ad esempio, librerie dei tipi registrate globalmente, estensioni di file, altri elementi sono registrate in HKEY\_CLASSES\_ROOT, e così via.  
  
-   Raggruppare i componenti condivisi nei modelli unione separati.  
  
     Questo consente di creare correttamente per passare più avanti.  
  
-   Installare i file condivisi e le chiavi del Registro di sistema utilizzando gli stessi componenti di Windows Installer tramite le versioni.  
  
     Se si utilizza un componente diverso, i file e le voci del Registro di sistema vengano disinstallati quando un package VS con versione viene disinstallato ma un altro package VS è ancora installato.  
  
-   Non combinare elementi con versione e condivisi nello stesso componente.  
  
     In tal modo è impossibile installare gli elementi condivisi in un punto globale e gli elementi con versione alle posizioni isolati.  
  
-   Non condiviso delle chiavi del Registro di sistema che facciano riferimento a file con versione.  
  
     In questo caso, le chiavi condivisi verranno sovrascritte quando un altro package VS con versione è installato.  Dopo aver rimosso la seconda versione, il file a cui la chiave è posizionato è stata rimossa.  
  
## Vedere anche  
 [Scelta tra i package VS condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scenari di installazione di VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)