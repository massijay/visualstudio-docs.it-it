---
title: "Utilit&#224; RegPkg | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regpkg, utilità di registrazione"
  - "registrazione dell'utilità regpkg"
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Utilit&#224; RegPkg
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Il modo migliore per la registrazione di pacchetti in Visual Studio è tramite i file. pkgdef. Ciò consente di distribuire le estensioni senza dover accedere al Registro di sistema, che è un requisito per la distribuzione VSIX. I file pkgdef vengono creati tramite il [Utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Per ulteriori informazioni sulla distribuzione del pacchetto Visual Studio, vedere [Distribuzione di estensioni di Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 L'utilità RegPkg.exe registra un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e prepararlo per la distribuzione. Questa utilità viene utilizzata dietro le quinte durante lo sviluppo di VSPackage. Viene eseguito come parte del processo di compilazione in modo che è possibile compilare ed eseguire un VSPackage nell'hive sperimentale.  
  
 RegPkg può generare gli script del Registro di sistema di sistema in vari formati. È possibile incorporare questi script nei progetti di distribuzione come file con estensione msi progetti o file di set di strumenti di Windows Installer XML.  
  
 RegPkg.exe è in genere si trova in \<*il percorso di installazione di Visual Studio SDK*\> \\VisualStudioIntegration\\Tools\\Bin\\RegPkg.exe. RegPkg segue questa sintassi:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 \/root:root  
 Esegue la registrazione con il nome specificato  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] radice.  
  
 \/regfile:filename  
 Crea un file con estensione reg, anziché aggiornare il Registro di sistema.  Non può essere utilizzato con \/vrgfile o \/rgsfile o \/wixfile.  
  
 \/rgsfile:filename  
 Crea un file con estensione RGS anziché aggiornare il Registro di sistema.  Non può essere utilizzato con \/vrgfile o \/regfile o \/wixfile.  
  
 \/vrgfile:filename  
 Crea un file .vrg anziché aggiornare il Registro di sistema.  Non può essere utilizzato con \/regfile o \/rgsfile o \/wixfile.  
  
 \/rgm  
 Crea un file .rgm oltre al file rgs.  Devono essere combinati con \/rgsfile.  
  
 \/wixfile:filename  
 Crea un file compatibile con il set di strumenti Windows Installer XML anziché aggiornare il Registro di sistema.  Non può essere utilizzato con \/regfile o \/rgsfile o \/vrgfile.  
  
 \/codebase  
 Registrazione di forze con CodeBase anziché come Assembly.  
  
 \/assembly  
 Registrazione di forze con Assembly anziché CodeBase.  
  
 \/unregister  
 Annulla la registrazione di questo pacchetto.  Non può essere utilizzato  
  
 con \/regfile o \/vrgfile o \/rgsfile o \/wixfile.  
  
## Vedere anche  
 [Rilascio di un prodotto](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Registrazione risoluzione dei problemi del pacchetto di RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)