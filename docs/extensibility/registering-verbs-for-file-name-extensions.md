---
title: "La registrazione di verbi di estensioni di File | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "verbi di registrazione"
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# La registrazione di verbi di estensioni di File
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'associazione di un'estensione nome file con un'applicazione è in genere un'azione preferita che si verifica quando un utente fa doppio clic su un file. Questo preferibile utilizzare l'azione è collegata a un verbo, ad esempio aprire, che corrisponde all'azione.  
  
 È possibile registrare i verbi associati a un identificatore programmatico \(ProgID\) per un'estensione con la chiave Shell si trova in HKEY\_CLASSES\_ROOT\\*progid*\\shell. Per ulteriori informazioni, vedere [tipi di File](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## Registrazione di verbi Standard  
 Il sistema operativo riconosce i verbi standard seguenti:  
  
-   Apri  
  
-   Modifica  
  
-   Esegui  
  
-   Print  
  
-   Anteprima  
  
 Quando possibile, registrare un verbo standard. La scelta più comune è il verbo Open. Utilizzare il verbo di modifica solo se esiste una netta differenza tra l'apertura del file e la modifica del file. Ad esempio, aprire un file. htm visualizza nel browser, mentre la modifica di un file. htm viene avviato un editor HTML. Verbi standard sono localizzati con le impostazioni locali del sistema operativo.  
  
> [!NOTE]
>  Quando si registrano i verbi standard, non impostare il valore predefinito per la chiave aperta. Il valore predefinito contiene la stringa di visualizzazione del menu. Il sistema operativo fornisce questa stringa per i verbi standard.  
  
 File di progetto devono essere registrati per avviare una nuova istanza della [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quando un utente apre il file. Nell'esempio seguente viene illustrata una registrazione verbi standard per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] progetto.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Per aprire un file in un'istanza esistente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], registrare una chiave DDEEXEC. Nell'esempio seguente viene illustrata una registrazione verbi standard per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] file con estensione cs.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## Impostare il verbo predefinito  
 Il verbo predefinito è l'azione da eseguita quando un utente fa doppio clic su un file in Esplora risorse. Il verbo predefinito è il verbo specificato come valore predefinito per il HKEY\_CLASSES\_ROOT\\*progid*\\Shell chiave. Se viene specificato alcun valore, il verbo predefinito è il primo verbo specificato il HKEY\_CLASSES\_ROOT\\*progid*\\Shell elenco di chiavi.  
  
> [!NOTE]
>  Se si prevede di modificare il verbo predefinito per un'estensione in una distribuzione side\-by\-side, valutare l'impatto sull'installazione e rimozione. Durante l'installazione viene sovrascritto il valore predefinito originale.  
  
## Vedere anche  
 [Creating a File Association](_win32_file_associations)   
 [La gestione delle associazioni di File Side\-by\-Side](../extensibility/managing-side-by-side-file-associations.md)