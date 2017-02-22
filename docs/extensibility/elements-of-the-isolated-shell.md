---
title: "Elementi della Shell isolata | Microsoft Docs"
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
  - "Visual Studio shell, modalità isolata"
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Elementi della Shell isolata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile modificare le impostazioni del Registro di sistema, le impostazioni di runtime e punto di ingresso dell'applicazione dell'applicazione shell isolata e il relativo vsct,. pkgdef, and.pkgundef file.  
  
## Impostazioni del Registro di sistema  
 I. pkgdef sia i file .pkgundef modificano le impostazioni del Registro di sistema per l'applicazione shell isolata. Quando l'applicazione viene eseguita, le impostazioni del Registro di sistema sono definite nella sequenza seguente:  
  
 Quando l'applicazione viene eseguita, le impostazioni del Registro di sistema sono definite nella sequenza seguente:  
  
1.  La chiave del Registro di sistema per l'applicazione viene creata.  
  
2.  Il Registro di sistema viene aggiornato dal file. pkgdef dell'applicazione mediante la definizione di voci e chiavi specificate.  
  
3.  Per ogni pacchetto che fa parte dell'applicazione, il Registro di sistema viene aggiornato dal file. pkgdef di tale pacchetto. Ogni pacchetto è definito nel file. pkgdef dell'applicazione per la \\Packages\\$ $RootKey {*vsPackageGuid*} chiave per il pacchetto.  
  
4.  Il Registro di sistema viene aggiornato dal AppEnvConfig.pkgdef e BaseConfig.pkgdef nel *il percorso di installazione di Visual Studio SDK*\\Common7\\IDE\\ShellExtensions\\Platform directory. Questi file sono parte di Visual Studio e far parte del pacchetto ridistribuibile Visual Studio Shell \(modalità isolata\).  
  
5.  Il Registro di sistema viene aggiornato dal file .pkgundef dell'applicazione tramite la rimozione di voci e chiavi specificate.  
  
## Impostazioni di runtime  
 Quando un utente avvia l'applicazione shell isolata, chiama il punto di ingresso di avvio della shell di Visual Studio. Le impostazioni dell'applicazione sono definite all'avvio dell'applicazione, come indicato di seguito:  
  
1.  La shell di Visual Studio controlla il Registro di sistema di applicazioni per chiavi specifiche. Se l'impostazione di una chiave viene specificato nella chiamata al punto di ingresso di avvio, tale valore sostituisce il valore del Registro di sistema.  
  
2.  Se il Registro di sistema né la voce del punto parametro specifica il valore di un'impostazione, quindi viene utilizzato il valore predefinito per l'impostazione.  
  
 Quando un utente avvia l'applicazione dalla riga di comando, tutte le opzioni della riga di comando vengono passate alla shell di Visual Studio, che li considera nello stesso modo che vengono effettuate. Per ulteriori informazioni sulle opzioni di Devenv, vedere [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md) e [Opzioni della riga di comando devenv per lo sviluppo di VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Per ulteriori informazioni su come si registra un pacchetto per opzioni della riga di comando, vedere [Aggiunta della riga di comando](../extensibility/adding-command-line-switches.md).  
  
## Il punto di ingresso di avvio  
 Il file Appenvstub.dll contiene punti di ingresso per accedere alla shell isolata. All'avvio dell'applicazione, viene chiamato punto di ingresso iniziale di Appenvstub.dll.  
  
 È possibile modificare il comportamento dell'applicazione modificando il valore dell'ultimo parametro passato al punto di ingresso iniziale. Per altre informazioni, vedere [Parametri punto di ingresso Shell isolata \(C\+\+\)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## Il file con estensione File Vsct  
 Il file vsct consente di specificare quali elementi dell'interfaccia utente di Visual Studio standard sono disponibili nell'applicazione. Per altre informazioni, vedere [. File Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## Il file con estensione File Pkgundef  
 Quando l'applicazione viene installata in un computer in cui è già installato Visual Studio, viene creata una copia delle voci del Registro di sistema di Visual Studio per l'applicazione. Per impostazione predefinita, l'applicazione utilizza i package VS che sono già installati nel computer. Il file .pkgundef consente di escludere le voci del Registro di sistema per rimuovere elementi specifici della shell di Visual Studio o estensioni dall'applicazione. Per altre informazioni, vedere [. File Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Il file .pkgundef consente di escludere le voci del Registro di sistema per rimuovere elementi specifici della shell di Visual Studio o estensioni dall'applicazione. Per altre informazioni, vedere [. File Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Il set di GUID che è possibile escludere pacchetto sono elencati [GUID del pacchetto di funzionalità di Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## Il file con estensione File pkgdef  
 Il file. pkgdef consente di definire le voci del Registro di sistema per l'applicazione che vengono impostate durante l'installazione dell'applicazione. Per una descrizione del file. pkgdef e un elenco di voci del Registro di sistema che utilizza la shell di Visual Studio, vedere [. File pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## Stringhe di sostituzione  
 Nella sono elencate le stringhe di sostituzione utilizzate nei file. pkgdef e .pkgundef [Utilizzato stringhe di sostituzione. Pkgdef e. File Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## Altre impostazioni  
 Se l'applicazione shell isolata dipende Microsoft.VisualStudio.GraphModel.dll, è necessario aggiungere il reindirizzamento di associazione seguente al file. config dell'applicazione Shell isolata:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```