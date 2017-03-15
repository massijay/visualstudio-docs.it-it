---
title: "MT Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCManifestTool.ResourceOutputFileName"
  - "VC.Project.VCManifestTool.SuppressDependencyElement"
  - "VC.Project.VCManifestTool.ManifestFromManagedAssembly"
  - "VC.Project.VCManifestTool.GenerateCategoryTags"
  - "VC.Project.VCManifestTool.EnableDPIAwareness"
  - "vc.task.mt"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBUILD (Visual C++), MT task"
  - "MT task (MSBuild (Visual C++))"
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# MT Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esegue il wrapping dello strumento Manifesto di Microsoft, mt.exe.  Per ulteriori informazioni, vedere "Mt.exe" sul sito Web di [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività **MT**.  La maggior parte dei parametri dell'attività e alcuni set di parametri, corrispondere a un'opzione della riga di comando.  
  
> [!NOTE]
>  La documentazione mt.exe utilizza un trattino \(**\-**\) come prefisso per le opzioni della riga di comando, ma questo argomento utilizza una barra \(**\/**\).  Il prefisso è accettabile.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Parametro **String\[\]** facoltativo.<br /><br /> Specifica il nome di uno o più file manifesto.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/manifest** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Elenco di opzioni della riga di comando.  Ad esempio, " \/option1 \/option2 \/opzione \#".  Utilizzare questo parametro per specificare opzioni della riga di comando che non sono rappresentate da qualsiasi altro parametro dell'attività **MT**.<br /><br /> Per ulteriori informazioni, vedere "Mt.exe" sul sito Web di [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**AssemblyIdentity**|Parametro **String** facoltativo.<br /><br /> Specifica i valori dell'attributo dell'elemento **assemblyIdentity** del manifesto.  Specificare un elenco delimitato da virgole, dove il primo componente è il valore dell'attributo `name`, seguito da uno o più coppie nome\/valore che hanno il formato, *\<attribute name\>\=\<attribute\_value\>*.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/identity** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ComponentFileName**|Parametro **String** facoltativo.<br /><br /> Specifica il nome di DLL che si intende compilare dai file rgs o tlb.  Questo parametro è obbligatorio se si specifica **RegistrarScriptFile** o i parametri dell'attività MT **TypeLibraryFile**.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/dll** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**DependencyInformationFile**|Parametro **String** facoltativo.<br /><br /> Specifica il file di informazioni sulle dipendenze che verrà utilizzato da Visual Studio per tenere traccia delle informazioni sulle dipendenze della compilazione per lo strumento Manifesto.|  
|**EmbedManifest**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, incorpora un file manifesto nell'assembly.  Se `false`, crea come un file manifesto autonomo.|  
|**EnableDPIAwareness**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, aggiunge alle informazioni manifeste che contrassegnano l'applicazione come compatibili con Dpi.  La scrittura di un'applicazione compatibile con Dpi rende costantemente buono l'aspetto dell'interfaccia utente attraverso un'ampia varietà di impostazioni di visualizzazione dpi elevate.<br /><br /> Per ulteriori informazioni, vedere "High DPI" sul sito Web di [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**GenerateCatalogFiles**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, genera file di definizione del catalogo \(cdf\).<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/makecdfs** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**GenerateCategoryTags**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, consente di generare i tag di categoria.  Se questo parametro è `true`, è necessario specificare anche il parametro dell'attività **ManifestFromManagedAssembly MT**.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/category** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**InputResourceManifests**|Parametro **String** facoltativo.<br /><br /> Immettere il manifesto da una risorsa di tipo RT\_MANIFEST che ha l'identificativo specificato.  Specificare una risorsa nel formato, *\<file\>\[***;** *\[***\#** *\] \<resource\_id\>\]*, dove il parametro facoltativo `resource_id` è un numero non negativo a 16 bit.<br /><br /> Se `resource_id` viene specificato, il valore predefinito \(1\) CREATEPROCESS\_MANIFEST\_RESOURCE viene utilizzato.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/inputresource** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ManifestFromManagedAssembly**|Parametro **String** facoltativo.<br /><br /> Genera un manifesto dall'assembly gestito specificato.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/managedassemblyname** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ManifestToIgnore**|Parametro **String** facoltativo.<br /><br /> Non utilizzato.|  
|**OutputManifestFile**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del manifesto di output.  Se viene omesso questo parametro e solo un manifesto viene eseguito, quel manifesto viene modificato in sua vece.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/out** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**OutputResourceManifests**|Parametro **String** facoltativo.<br /><br /> Restituire il manifesto come output a una risorsa di tipo RT\_MANIFEST che ha l'identificativo specificato.  La risorsa è del formato *\<file\> \[***;** *\[***\#** *\]\<resource\_id\>\]*, dove il parametro facoltativo `resource_id` è un numero non negativo a 16 bit.<br /><br /> Se `resource_id` viene specificato, il valore predefinito \(1\) CREATEPROCESS\_MANIFEST\_RESOURCE viene utilizzato.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/outputresource** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**RegistrarScriptFile**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del file dello script di registrazione \(rgs\) che verrà utilizzato per il supporto del manifesto COM senza registrazione.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/rgs** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ReplacementsFile**|Parametro **String** facoltativo.<br /><br /> Specifica il file che contiene valori per le stringhe sostituibili nel file di script di registrazione \(con estensione rgs\).<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/replacements** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ResourceOutputFileName**|Parametro **String** facoltativo.<br /><br /> Specifica il file di risorse di output utilizzati per incorporare il manifesto nell'output del progetto.|  
|**Sources**|Parametro `ITaskItem[]` facoltativo.<br /><br /> Specifica un elenco di file di origine manifesti separati dagli spazi.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/manifest** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**SuppressDependencyElement**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, genera un manifesto senza elementi di dipendenza.  Se questo parametro è `true`, specificare anche il parametro dell'attività **ManifestFromManagedAssembly MT**.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/nodependency** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**SuppressStartupBanner**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del copyright e il messaggio del numero di versione quando l'attività inizia.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/nologo** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**TrackerLogDirectory**|Parametro `String` facoltativo.<br /><br /> Specifica la directory intermedia dove vengono archiviati log di rilevamento per questa attività.|  
|**TypeLibraryFile**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del file della libreria dei tipi \(tlb\).  Se si specifica questo parametro, specificare anche il parametro dell'attività **ComponentFileName MT** .<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/tlb** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**UpdateFileHashes**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, calcola il valore hash dei file nel percorso specificato dal parametro dell'attività  **UpdateFileHashesSearchPath MT** e quindi aggiorna il valore dell'attributo **hash** dell'elemento **file** del manifesto utilizzando il valore calcolato.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/hashupdate** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  Vedere anche il parametro **UpdateFileHashesSearchPath** in questa tabella.|  
|**UpdateFileHashesSearchPath**|Parametro `String` facoltativo.<br /><br /> Specifica il percorso di ricerca da utilizzare quando vengono aggiornati gli hash del file.  È possibile utilizzare questo parametro con il parametro dell'attività **UpdateFileHashes MT**.<br /><br /> Per ulteriori informazioni, vedere il parametro **UpdateFileHashes** in questa tabella.|  
|**VerboseOutput**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, visualizza informazioni sul debug in modalità dettagliata.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/verbose** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## Note  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)