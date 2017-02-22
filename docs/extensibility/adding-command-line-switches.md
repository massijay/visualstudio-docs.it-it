---
title: "Aggiunta della riga di comando | Microsoft Docs"
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
  - "opzioni della riga di comando, aggiunta"
  - "opzioni della riga di comando, recupero"
  - "Metodo IVsAppCommandLine::GetOption"
  - "riga di comando, opzioni"
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Aggiunta della riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile aggiungere parametri della riga di comando che riguardano il VSPackage quando devenv.exe viene eseguita. Utilizzare <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> per dichiarare il nome dell'opzione e le relative proprietà. In questo esempio viene aggiunta l'opzione MySwitch per una sottoclasse di VSPackage denominato **AddCommandSwitchPackage** senza argomenti e con VSPackage caricati automaticamente.  
  
```c#  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Nella tabella seguente vengono visualizzati i parametri denominati  
  
 Argomenti  
 Il numero di argomenti per il commutatore. Può essere "\*", o un elenco di argomenti.  
  
 DemandLoad  
 Caricare il package VS automaticamente se è impostato su 1, altrimenti è impostato su 0.  
  
 HelpString  
 L'ID della Guida stringa o una risorsa della stringa da visualizzare con **devenv \/?**.  
  
 Nome  
 Questo parametro.  
  
 PackageGuid  
 Il GUID del pacchetto.  
  
 Il primo valore degli argomenti è in genere 0 o 1. Un valore speciale ' \*' può essere utilizzato per indicare che tutto il resto della riga di comando è costituito dall'argomento. Questo può essere utile per scenari in cui un utente deve passare una stringa di comando del debugger di debug.  
  
 Il valore DemandLoad è `true` \(1\) o `false` \(0\) indica che il package VS devono essere caricati automaticamente.  
  
 Il valore HelpString è l'ID risorsa della stringa che viene visualizzato di devenv \/? Visualizzazione della Guida. Questo valore deve essere nel formato "\#nnn" dove nnn rappresenta un numero intero. Il valore di stringa nel file di risorse deve terminare con un carattere di nuova riga.  
  
 Il valore del nome è il nome del commutatore.  
  
 Il valore PackageGuid è il GUID del pacchetto che implementa questa opzione è attivata. L'IDE utilizza questo GUID per trovare il package VS nel Registro di sistema a cui si applica l'opzione della riga di comando.  
  
## Recupero della riga di comando  
 Quando viene caricato il pacchetto, è possibile recuperare i parametri della riga di comando, completare i passaggi seguenti.  
  
1.  Nel VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementazione, chiamata `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> per ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfaccia.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> per recuperare i parametri della riga di comando immessi dall'utente.  
  
 Il codice seguente viene illustrato come scoprire se l'opzione della riga di comando MySwitch immessa dall'utente:  
  
```c#  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine)); int isPresent = 0; string optionValue = ""; cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 È responsabilità dell'utente per cercare le opzioni della riga di comando ogni volta che viene caricato il pacchetto.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)   
 [Utilità CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [. File pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)