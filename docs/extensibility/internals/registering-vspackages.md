---
title: "Registrazione di VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages gestito, la registrazione"
  - "registrazione, VSPackages gestito"
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Registrazione di VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si basa sui file .pkgdef per descrivere e individuare un VSPackage.  Un file .pkgdef contiene tutte le informazioni di registrazione che è aggiungerebbero in caso contrario al Registro di sistema.  Vspackage gestito viene registrato aggiungendo gli attributi al codice sorgente e quindi esegue [Utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) l'assembly risultante per generare un file .pkgdef.  
  
## In questa sezione  
 [Specifica il percorso di File VSPackage alla Shell di Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Viene descritto il percorso di caricamento per Vspackage.  
  
 [Package VS della registrazione e annullamento della registrazione](../../extensibility/registering-and-unregistering-vspackages.md)  
 Viene spiegato come registrare un VSPackage.  
  
 [Uso di un attributo di registrazione personalizzato per registrare un'estensione](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension)  
 Viene descritto come creare un manifesto di registrazione che può essere utilizzato per implementare un VSPackage gestito.