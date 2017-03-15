---
title: "Scegliere la Directory di installazione per un VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Package VS, directory di installazione"
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Scegliere la Directory di installazione per un VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage e i file di supporto devono essere sul file system di un utente.  Il percorso varia a seconda che il pacchetto VS è gestito o non gestito, la combinazione affiancata del controllo delle versioni e scelta dell'utente.  
  
## Vspackage non gestito  
 Un VSPackage non gestito è un server COM che può essere installato in qualsiasi percorso.  Il valore di informazioni di registrazione riflette accuratamente la posizione.  L'interfaccia utente del programma \(UI\) di installazione deve fornire una posizione predefinita come sottodirectory della proprietà di ProgramFilesFolder Windows Installer.  Di seguito è riportato un esempio:  
  
 \[ProgramFilesFolder\] Miasocietà \\MyVSPackageProduct\\V 1,0 \\  
  
 L'utente deve avere la possibilità di modificare la directory predefinita per gli utenti che conserva una piccola partizione di avvio e preferiscono installare applicazioni e gli strumenti in un altro volume.  
  
 Se la combinazione affiancata utilizza un VSPackage con versione, è possibile utilizzare le sottodirectory per archiviare le versioni diverse.  Di seguito è riportato un esempio:  
  
 \[ProgramFilesFolder\] Miasocietà \\MyVSPackageProduct\\V 1,0 \\ 2002 \\  
  
 \[ProgramFilesFolder\] Miasocietà \\MyVSPackageProduct\\V 1,0 \\ 2003 \\  
  
 \[ProgramFilesFolder\] Miasocietà \\MyVSPackageProduct\\V 1,0 \\ 2005 \\  
  
## Vspackage gestito  
 Vspackage gestito può anche essere installato in qualsiasi percorso.  Tuttavia, è necessario considerare sempre di installarli nella Global \(GAC\) Assembly Cache per ridurre le chiavi di caricamento.  Poiché Vspackage gestito è sempre assembly con nome sicuro, installarle nella GAC indicano che la verifica della firma con nome sicuro accetta solo durante l'installazione.  Gli assembly con nome sicuro installati nel file system è necessario apportare le verificare firme ogni volta che vengono caricati.  Quando si installa Vspackage gestito nella GAC, utilizzare l'opzione di **\/assembly** lo strumento di regpkg per scrivere le voci del Registro di sistema che punta al nome sicuro dell'assembly.  
  
 Se si installa Vspackage gestito in un percorso diverso dalla GAC, seguire il consiglio iniziale fornito per Vspackage non gestito scegliere le gerarchie di directory.  Utilizzare l'opzione di **\/codebase** lo strumento di regpkg per scrivere le voci del Registro di sistema che punta al percorso dell'assembly di un VSPackage.  
  
 Per ulteriori informazioni, vedere [Package VS della registrazione e annullamento della registrazione](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## DLL satellite  
 Per convenzione, le DLL satellite di un VSPackage \- che contengono le risorse per le impostazioni locali particolari \- si trovano in sottodirectory della directory di un VSPackage.  Le sottodirectory corrispondono ai valori ID delle impostazioni locali \(LCID\).  
  
 [La gestione di VSPackage](../../extensibility/managing-vspackages.md) indica che le voci del Registro di sistema controllano in cui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] effettivamente cerca la DLL satellite di un VSPackage.  Tuttavia, tenta di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]per caricare una DLL satellite in una sottodirectory denominata un valore di LCID, nell'ordine seguente:  
  
1.  LCID predefinito \(VS A LCID ad esempio \\1033 for English\)  
  
2.  LCID predefinito con la sottolingua predefinita.  
  
3.  Impostazione predefinita del sistema LCID.  
  
4.  Impostazione predefinita del sistema LCID con la sottolingua predefinita.  
  
5.  Stati Uniti  inglese \(.  \\ 1033 o.  \\ 0x409\).  
  
 Se la DLL di un VSPackage include le risorse e i punti di voci del Registro di sistema di SatelliteDll \\DllName su, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta di caricarle nell'ordine di precedenza.  
  
## Vedere anche  
 [Scelta tra i package VS condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [La gestione di VSPackage](../../extensibility/managing-vspackages.md)   
 [Managed Package Registration](http://msdn.microsoft.com/it-it/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)