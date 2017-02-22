---
title: "Specifica il percorso di File VSPackage alla Shell di Visual Studio | Microsoft Docs"
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
  - "VSPackages gestito, percorso del file"
  - "Package VS, gestito percorso file del pacchetto"
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Specifica il percorso di File VSPackage alla Shell di Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve essere in grado di individuare l'assembly DLL per caricare il VSPackage. È possibile individuarlo in vari modi, come descritto nella tabella seguente.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|Utilizzare la chiave del Registro di sistema di base di codice.|La chiave CodeBase può essere utilizzata per indirizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per caricare l'assembly VSPackage da qualsiasi percorso completo del file. Il valore della chiave deve essere il percorso del file della DLL. Questo è il modo migliore per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Carica l'assembly di pacchetto. Questa tecnica è detta anche "CodeBase e privata installazione directory tecnica." Durante la registrazione viene passato il valore della codebase alle classi di attributo di registrazione tramite un'istanza di <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> tipo.|  
|Posizionare il file DLL nel **PrivateAssemblies** directory.|Collocare l'assembly nel **PrivateAssemblies** sottodirectory di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory. Gli assembly si trovano **PrivateAssemblies** vengono rilevate automaticamente, ma non sono visibili nel **Aggiungi riferimenti** la finestra di dialogo. La differenza tra **PrivateAssemblies** e **PublicAssemblies** è che gli assembly in **PublicAssemblies** vengono enumerati nel **Aggiungi riferimenti** la finestra di dialogo. Se si sceglie di non utilizzare la tecnica "directory di installazione CodeBase e privata", quindi è necessario installare nel **PrivateAssemblies** directory.|  
|Utilizzare un assembly con nome sicuro e la chiave del Registro di sistema di Assembly.|La chiave di Assembly può essere utilizzata per indirizzare in modo esplicito [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per caricare un nome sicuro denominato assembly VSPackage. Il valore della chiave deve essere il nome sicuro dell'assembly.|  
|Posizionare il file DLL nel **PublicAssemblies** directory.|Infine, l'assembly può anche essere inserito nel **PublicAssemblies** sottodirectory. Gli assembly si trovano **PublicAssemblies** vengono rilevate automaticamente e viene visualizzata anche nel **Aggiungi riferimenti** nella finestra di dialogo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Gli assembly VSPackage devono essere posizionati solo nel **PublicAssemblies** directory che contengono i componenti destinati a essere riutilizzato da altri sviluppatori VSPackage gestiti. La maggior parte degli assembly non soddisfano questo criterio.|  
  
> [!NOTE]
>  Utilizzare gli assembly con nome sicuro per tutti gli assembly dipendenti. Questi assembly devono inoltre essere installati nella global assembly cache \(GAC\) o le directory. Ciò consente di evitare conflitti con gli assembly che hanno lo stesso nome di file di base, noto come associazione del nome debole.