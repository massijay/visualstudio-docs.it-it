---
title: "WriteCodeFragment Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, WriteCodeFragment task"
  - "WriteCodeFragment task [MSBuild]"
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteCodeFragment Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Genera un file di codice temporaneo dal frammento di codice generato specificato.  Non elimina il file.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `WriteCodeFragment`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AssemblyAttributes`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Descrizione degli attributi da scrivere.  Il valore `Include` dell'elemento è il nome tipo completo dell'attributo, ad esempio, "System.AssemblyVersionAttribute".<br /><br /> Ogni parte di metadati è costituita dalla coppia nome\/valore di un parametro, che deve essere di tipo `String`.  Alcuni attributi consentono solo argomenti del costruttore posizionali.  Tuttavia, è possibile utilizzare tali argomenti in qualsiasi attributo.  Per impostare attributi del costruttore posizionali, utilizzare nomi di metadati simili a "\_Parameter1", "\_Parameter2" e così via.<br /><br /> Impossibile ignorare un indice di parametro.|  
|`Language`|Parametro `String` obbligatorio.<br /><br /> Specifica il linguaggio del codice da generare.<br /><br /> Con `Language` è possibile indicare qualsiasi linguaggio per il quale è disponibile un provider CodeDom, ad esempio, "C\#" o "VisualBasic".  Il file creato avrà l'estensione nome file predefinita per tale linguaggio.|  
|`OutputDirectory`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica la cartella di destinazione per il codice generato, in genere la cartella intermedia.|  
|`OutputFile`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il percorso del file che è stato generato.  Se questo parametro viene impostato utilizzando un nome file, la cartella di destinazione viene anteposta a tale nome.  Se viene impostato tramite una radice, la cartella di destinazione viene ignorata.<br /><br /> Se questo parametro non è impostato, il nome del file di output corrisponde alla cartella di destinazione, a un nome file arbitrario e all'estensione di file predefinita per il linguaggio specificato.|  
  
## Note  
 Oltre a disporre dei parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)