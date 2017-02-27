---
title: "Scenari di installazione di VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Package VS, considerazioni sulla distribuzione"
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Scenari di installazione di VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È importante progettare il programma di installazione di VSPackage flessibilità. Ad esempio, è possibile rilasciare una patch di protezione in futuro oppure è possibile modificare una strategia di business che richiede il supporto completo controllo delle versioni side\-by\-side.  
  
 In [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), per scoprire i vantaggi e i problemi di supportare le installazioni side\-by\-side di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con installazioni condivise o side\-by\-side del pacchetto Visual Studio. In breve, i package VS side\-by\-side offrono una maggiore flessibilità per supportare nuove funzionalità di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Gli scenari illustrati in questo argomento non sono le uniche scelte a disposizione, ma sono presentati come procedure consigliate.  
  
## I componenti, Privacy e la condivisione  
  
##### Creazione di componenti indipendenti  
 Dopo avere identificato e compilare un componente, assegnare un `GUID`, e distribuire il componente non è possibile modificare la composizione. Se si modifica la composizione del componente, il componente risulta deve essere un nuovo componente con un nuovo `GUID`. Dato questi concetti, viene offerta la massima flessibilità per il controllo delle versioni rendendo ogni unità indipendenti, radicato componente. Per ulteriori informazioni sulle regole che controllano i componenti, vedere [Modifica del codice del componente](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) e [cosa accade se il componente regole non vengono visualizzati?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### Non combinare risorse condivise e private in un componente  
 Il conteggio dei riferimenti si verifica a livello di componente. Di conseguenza, la combinazione di risorse condivise e private in un singolo componente rende Impossibile aggiornare le risorse private, ad esempio un file eseguibile, senza sovrascrivere anche risorse condivise. Questo scenario consente di creare problemi di compatibilità con le versioni precedenti e si impedisce la creazione di funzionalità side\-by\-side.  
  
 Ad esempio, i valori del Registro di sistema utilizzato per registrare il pacchetto Visual Studio con il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] deve essere incluso in un componente separato da quello utilizzato per registrare il pacchetto Visual Studio con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. I valori del Registro di sistema o file condivisi inseriti in un altro componente.  
  
## Scenario 1: Package VS condivisi  
 In questo scenario, un package VS condivisi \(un solo file binario che supporta più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\) viene fornito in un pacchetto Windows Installer. La registrazione con ogni versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dipende dalle funzionalità selezionabili dall'utente. Significa inoltre che quando assegnato per separare le funzionalità, ogni componente può essere selezionato singolarmente per l'installazione o disinstallazione, inserisce l'utente nel controllo dell'integrazione di VSPackage in versioni diverse di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. \(Vedere [funzionalità di Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) per ulteriori informazioni sull'utilizzo delle funzionalità nei pacchetti di Windows Installer.\)  
  
 ![Rappresentazione grafica dei prodotti del package VS condivisi](../../extensibility/internals/media/vs_sharedpackage.png "VS\_SharedPackage")  
Programma di installazione del package VS condiviso  
  
 Come illustrato nella figura, i componenti condivisi diventano parte della funzionalità di Feat\_Common, viene sempre installata. Per rendere visibili le funzionalità Feat\_VS2002 e Feat\_VS2003, gli utenti possono scegliere in fase di installazione in quali versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] desiderano VSPackage integrare. Gli utenti possono inoltre utilizzare modalità di manutenzione di Windows Installer per aggiungere o rimuovere funzionalità, che in questo caso aggiunge o rimuove le informazioni di registrazione VSPackage da versioni diverse di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  L'impostazione di colonna di visualizzazione di una funzionalità su 0 la nasconde. Un valore di colonna di livello basso, ad esempio 1, garantisce che verrà sempre installata. Per ulteriori informazioni, vedere [proprietà INSTALLLEVEL](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) e [tabella delle funzionalità](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## Scenario 2: Condiviso aggiornamento VSPackage  
 In questo scenario, è disponibile una versione aggiornata del programma di installazione VSPackage nello scenario 1. Ai fini di discussione, l'aggiornamento aggiunge il supporto per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ma potrebbe anche essere un semplice protezione patch o correzione di bug service pack. Regole del programma di installazione di Windows per l'installazione dei componenti più recenti richiedono che invariati i componenti già installati nel sistema non vengono ricopiati. In questo caso, un sistema con la versione 1.0 è già presente sovrascriverà il componente aggiornato Comp\_MyVSPackage.dll e consentire agli utenti di scegliere di aggiungere la nuova funzionalità Feat\_VS2005 con il componente Comp\_VS2005\_Reg.  
  
> [!CAUTION]
>  Ogni volta che un VSPackage è condiviso tra più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è essenziale che le versioni successive di VSPackage mantenere la compatibilità con le versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Dove è possibile mantenere la compatibilità con le versioni precedenti, è necessario utilizzare i package VS side\-by\-side e privati. Per altre informazioni, vedere [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Immagine dell'aggiornamento dei prodotti del package VS condivisi](../../extensibility/internals/media/vs_sharedpackageupdate.png "VS\_SharedPackageUpdate")  
Programma di installazione aggiornamento package VS condivisi  
  
 Questo scenario presenta un nuovo installer VSPackage, sfruttando il supporto del programma di installazione di Windows per aggiornamenti secondari. Gli utenti è sufficiente installano la versione 1.1 e viene aggiornato alla versione 1.0. Non è tuttavia necessario che la versione 1.0 del sistema. Lo stesso di installazione installerà la versione 1.1 in un sistema senza versione 1.0. Il vantaggio di fornire aggiornamenti secondari in questo modo è che non è necessario passare attraverso il lavoro di sviluppo di un programma di installazione di aggiornamento e un programma di installazione del prodotto completo. Un programma di installazione esegue entrambi i processi. Una correzione di sicurezza o un servizio di tipo pack potrebbe invece usufruire delle patch di Windows Installer. Per ulteriori informazioni, vedere [l'applicazione di patch e aggiornamenti](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## Scenario 3: Side\-by\-Side VSPackage  
 Questo scenario presenta due programmi di installazione del package VS, uno per ogni versione di Visual Studio .NET 2003 e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ogni programma di installazione installa un side\-by\-side privati, VSPackage \(uno in particolare compilato e installato per una particolare versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\). Ogni pacchetto VS è nel proprio componente. Di conseguenza, ogni possano essere singolarmente gestite con le patch o manutenzione rilascia. Poiché la DLL VSPackage è ora specifici della versione, è consigliabile includere le informazioni di registrazione nello stesso componente della DLL.  
  
 ![Rappresentazione grafica dei prodotti del package VS affiancati](../../extensibility/internals/media/vs_sbys_package.png "VS\_SbyS\_Package")  
Programma di installazione side\-by\-side VSPackage  
  
 Ogni programma di installazione include anche il codice che viene condiviso tra i due programmi di installazione. Se il codice condiviso è installato in un percorso comune, entrambi i file con estensione msi di installazione installerà il codice condiviso una sola volta. Il programma di installazione secondo incrementa semplicemente un conteggio dei riferimenti del componente. Il conteggio dei riferimenti garantisce che se uno dei package VS viene disinstallato, il codice condiviso resterà per il pacchetto Visual Studio. Se viene disinstallato anche il VSPackage secondo, il codice condiviso che verrà rimossi.  
  
## Scenario 4: Side\-by\-Side VSPackage aggiornamento  
 In questo scenario, il pacchetto Visual Studio per [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] subito una protezione di vulnerabilità ed è necessario eseguire un aggiornamento. Come nello scenario 2, è possibile creare un nuovo file con estensione msi che aggiorna un'installazione esistente per includere la correzione di sicurezza, nonché distribuire le nuove installazioni con la correzione di sicurezza già presenti.  
  
 In questo caso, il package VS è un VSPackage gestito installato nella global assembly cache \(GAC\). Durante la ricompilazione per includere la correzione di sicurezza, è necessario modificare la parte del numero di revisione del numero di versione dell'assembly. Le informazioni di registrazione per il nuovo numero di versione di assembly sovrascrive la versione precedente, causando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per caricare l'assembly predefinito.  
  
 ![Rappresentazione grafica dell'aggiornamento dei prodotti del package VS affiancati](../../extensibility/internals/media/vs_sbys_packageupdate.png "VS\_SbyS\_PackageUpdate")  
Programma di installazione aggiornamento side\-by\-side VSPackage  
  
 **Nota** per ulteriori informazioni sulla distribuzione di assembly side\-by\-side, vedere [Semplificazione della distribuzione e la risoluzione di "DLL hell" con .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## Vedere anche  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)