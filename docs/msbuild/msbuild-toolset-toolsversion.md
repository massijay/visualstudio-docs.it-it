---
title: "MSBuild Toolset (ToolsVersion) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, multitargeting"
  - "targeting a specific .NET framework [MSBuild]"
  - "MSBuild, targeting a specific .NET framework"
  - "multitargeting [MSBuild]"
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# MSBuild Toolset (ToolsVersion)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per lo sviluppo di un'applicazione, MSBuild usa un set di strumenti che comprende attività, destinazioni e strumenti.  In genere, un set di strumenti di MSBuild include un file microsoft.common.tasks, un file microsoft.common.targets e compilatori come csc.exe e vbc.exe.  La maggior parte dei set di strumenti può essere usata per compilare applicazioni in più versioni di .NET Framework e in più piattaforme di sistema.  Tuttavia, il set di strumenti di MSBuild 2.0 consente di scegliere come destinazione soltanto .NET Framework 2.0.  
  
## Attributo ToolsVersion  
 Specificare il set di strumenti nell'attributo `ToolsVersion` per l'elemento [Project](../msbuild/project-element-msbuild.md) nel file di progetto.  L'esempio seguente specifica che il progetto deve essere compilato con il set di strumenti di MSBuild 12.0.  
  
```  
<Project ToolsVersion="12.0" ... </Project>  
```  
  
## Funzionamento dell'attributo ToolsVersion  
 Quando si crea un progetto in Visual Studio oppure si aggiorna un progetto esistente, nel file di progetto viene incluso automaticamente un attributo denominato `ToolsVersion` e il relativo valore corrisponde alla versione di MSBuild inclusa nell'edizione di Visual Studio.  Per altre informazioni, vedere [Sviluppo per una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Quando in un file di progetto viene definito un valore dell'attributo `ToolsVersion`, MSBuild usa tale valore per determinare i valori delle proprietà del set di strumenti disponibili per il progetto.  Una delle proprietà del set di strumenti è `$(MSBuildToolsPath)`, che specifica il percorso degli strumenti di .NET Framework.  Solo tale proprietà del set di strumenti \(o `$(MSBuildBinPath)`\) è necessaria.  
  
 A partire da Visual Studio 2013, la versione del set di strumenti di MSBuild corrisponde al numero di versione di Visual Studio.  Per impostazione predefinita, MSBuild usa questo set di strumenti all'interno di Visual Studio e sulla riga di comando, indipendentemente dalla versione del set di strumenti specificato nel file di progetto.  È possibile eseguire l'override di questo comportamento usando il flag \/ToolsVersion.  Per altre informazioni, vedere [Override delle impostazioni ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 Nell'esempio seguente, MSBuild trova il file Microsoft.CSharp.targets usando la proprietà riservata `MSBuildToolsPath`.  
  
```  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 È possibile modificare il valore di `MSBuildToolsPath` definendo un set di strumenti personalizzato.  Per altre informazioni, vedere [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md).  
  
 Quando si compila una soluzione dalla riga di comando e si specifica un attributo `ToolsVersion` per msbuild.exe, tutti i progetti e le dipendenze tra progetti vengono compilati secondo tale attributo `ToolsVersion`, anche se ogni progetto della soluzione contiene un attributo `ToolsVersion` specifico.  Per definire il valore di `ToolsVersion` a livello di singolo progetto, vedere [Overriding ToolsVersion Settings](../msbuild/overriding-toolsversion-settings.md).  
  
 L'attributo `ToolsVersion` viene usato anche per la migrazione del progetto.  Ad esempio, se si apre un progetto di Visual Studio 2008 in Visual Studio 2010, il file di progetto viene aggiornato per includere ToolsVersion\="4.0".  Se in seguito si tenta di aprire tale progetto in Visual Studio 2008, l'attributo `ToolsVersion` aggiornato non verrà riconosciuto e pertanto il progetto verrà compilato come se l'attributo fosse ancora impostato su 3.5.  
  
 Sia Visual Studio 2010 che Visual Studio 2012 usano l'attributo ToolsVersion impostato su 4.0.  Visual Studio 2013 usa l'attributo ToolsVersion impostato su 12.0.  In molti casi è possibile aprire il progetto in tutte e tre le versioni di Visual Studio senza modifiche.  Visual Studio usa sempre il set di strumenti corretto, ma si riceverà una notifica se la versione usata non corrisponde alla versione del file di progetto.  In quasi tutti i casi, questo avviso non è grave perché i set di strumenti sono compatibili nella maggior parte dei casi.  
  
 I subset di strumenti, che saranno descritti più avanti in questo argomento, consentono a MSBuild di cambiare automaticamente il set di strumenti da usare in base al contesto in cui viene eseguita la compilazione.  Ad esempio, MSBuild usa un set di strumenti più recente quando viene eseguito in Visual Studio 2012 rispetto a quando viene eseguito in Visual Studio 2010, senza che sia necessario modificare in modo esplicito il file di progetto.  Per altre informazioni, vedere [Impostazione del riconoscimento della versione per i progetti personalizzati](../misc/making-custom-projects-version-aware.md).  
  
## Implementazione del set di strumenti  
 Per implementare un set di strumenti, selezionare i percorsi dei vari strumenti, destinazioni e attività che costituiscono il set di strumenti.  Gli strumenti del set definito da MSBuild provengono dalle seguenti origini:  
  
-   Cartella di .NET Framework  
  
-   Altri strumenti gestiti  
  
 Gli strumenti gestiti includono ResGen.exe e TlbImp.exe.  
  
 MSBuild consente di accedere al set di strumenti in due modi:  
  
-   Con le proprietà del set di strumenti  
  
-   Con i metodi <xref:Microsoft.Build.Utilities.ToolLocationHelper>  
  
 Le proprietà del set di strumenti specificano i percorsi degli strumenti.  MSBuild usa il valore dell'attributo `ToolsVersion` nel file di progetto per individuare la chiave corrispondente del Registro di sistema e quindi usa le informazioni della chiave del Registro di sistema per impostare le proprietà del set di strumenti.  Ad esempio, se `ToolsVersion` ha il valore `12.0`, MSBuild imposterà le proprietà del set di strumenti in base alla chiave del Registro di sistema HKLM\\Software\\Microsoft\\MSBuild\\ToolsVersions\\12.0.  
  
 Le proprietà del set di strumenti sono:  
  
-   `MSBuildToolsPath` specifica il percorso dei file binari di MSBuild.  
  
-   `SDK40ToolsPath` specifica il percorso di altri strumenti gestiti per MSBuild 4.x, ovvero 4.0 o 4.5.  
  
-   `SDK35ToolsPath` specifica il percorso di altri strumenti gestiti per MSBuild 3.5.  
  
 In alternativa, è possibile determinare il set di strumenti a livello di codice chiamando i metodi della classe <xref:Microsoft.Build.Utilities.ToolLocationHelper>.  La classe include i seguenti metodi:  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> restituisce il percorso della cartella di .NET Framework.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> restituisce il percorso di un file nella cartella di .NET Framework.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> restituisce il percorso della cartella degli strumenti gestiti.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> restituisce il percorso di un file, che in genere si trova nella cartella degli strumenti gestiti.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToBuildTools%2A> restituisce il percorso degli strumenti di compilazione.  
  
### Subset di strumenti  
 Come descritto precedentemente in questo argomento, MSBuild usa una chiave del Registro di sistema per specificare il percorso degli strumenti di base.  Se la chiave ha una sottochiave, MSBuild la usa per specificare il percorso di un subset di strumenti che contiene ulteriori strumenti.  In questo caso, il set di strumenti viene definito combinando le definizioni delle proprietà definite in entrambe le chiavi.  
  
> [!NOTE]
>  Se i nomi delle proprietà del set di strumenti sono in conflitto, il valore definito per il percorso della sottochiave ha la precedenza sul valore definito per il percorso della chiave radice.  
  
 I subset di strumenti diventano attivi in presenza della proprietà di compilazione `VisualStudioVersion`.  Questa proprietà può accettare uno dei valori seguenti:  
  
-   "10.0" indica i subset di strumenti di .NET Framework 4  
  
-   "11.0" indica i subset di strumenti di .NET Framework 4.5  
  
-   "12.0" indica i subset di strumenti di .NET Framework 4.5.1  
  
 Con ToolsVersion 4.0 usare i subset di strumenti 10.0 e 11.0.  Nelle versioni successive, la versione del subset di strumenti e ToolsVersion corrisponderanno.  
  
 Durante la compilazione MSBuild determina automaticamente un valore predefinito per la proprietà `VisualStudioVersion` e lo imposta, se tale proprietà non è stata già definita.  
  
 MSBuild fornisce gli overload dei metodi `ToolLocationHelper` che aggiungono come parametro un valore enumerato `VisualStudioVersion`.  
  
 I subset di strumenti sono stati introdotti in .NET Framework 4.5.  
  
## Vedere anche  
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)