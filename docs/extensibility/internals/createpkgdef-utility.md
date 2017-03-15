---
title: "Utilit&#224; CreatePkgDef | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "definizione di pacchetto"
  - "creare pkgdef"
  - "pkgdef"
  - "Createpkgdef"
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Utilit&#224; CreatePkgDef
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Accetta un file DLL per un'estensione di Visual Studio come un parametro e crea un file. pkgdef che accompagnano il file DLL. Il file. pkgdef contiene tutte le informazioni che verrebbe scritto nel Registro di sistema in caso contrario è installata l'estensione.  
  
> [!NOTE]
>  La maggior parte dei modelli di progetto che sono inclusi automaticamente in Visual Studio SDK creare file. pkgdef come parte del processo di compilazione. In questo documento è destinato a coloro che desiderano creare manualmente i pacchetti o convertire i pacchetti esistenti per l'utilizzo di distribuzione. pkgdef.  
  
## Sintassi  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## Argomenti  
 out \=`FileName`  
 Obbligatorio. Imposta il nome del file di output. pkgdef per```FileName`.  
  
 \/codebase  
 Facoltativo. Registrazione di forze con l'utilità della CodeBase.  
  
 \/assembly  
 Registrazione di forze con l'utilità di Assembly.  
  
 `AssemblyPath`  
 Il percorso del file DLL da cui si desidera generare il. pkgdef.  
  
## Note  
 Distribuzione dell'estensione di file. pkgdef sostituisce i requisiti del Registro di sistema le versioni precedenti di Visual Studio.  
  
 I file. pkgdef devono essere installati in una delle seguenti posizioni: %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ o % vsinstalldir%\\Common7\\IDE\\Extensions\\. Se la cartella di installazione è %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\, l'estensione verrà riconosciuto da Visual Studio, ma verrà disabilitata per impostazione predefinita. L'utente può abilitare l'estensione tramite **estensioni e aggiornamenti**. Se la cartella di installazione è % vsinstalldir%\\Common7\\IDE\\Extensions\\, l'estensione è abilitata per impostazione predefinita.  
  
> [!NOTE]
>  Il **estensioni e aggiornamenti** strumento non può essere utilizzato per accedere a un'estensione a meno che non viene installato come parte di un pacchetto VSIX.  
  
## Vedere anche  
 [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)