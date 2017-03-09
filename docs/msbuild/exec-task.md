---
title: "Exec Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Exec"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Exec task [MSBuild]"
  - "MSBuild, Exec task"
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Exec Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Consente di eseguire il programma o il comando specificato con utilizzando gli argomenti specificati.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `Exec`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Command`|Parametro `String` obbligatorio.<br /><br /> Comando\/comandi da eseguire.  Possono essere comandi di sistema, ad esempio attrib, o un file eseguibile, ad esempio program.exe, runprogram.bat o setup.msi.<br /><br /> Questo parametro può contenere più righe di comandi.  In alternativa, è possibile includere più comandi in un file batch ed eseguirlo tramite questo parametro.|  
|`CustomErrorRegularExpression`|Parametro `String` facoltativo.<br /><br /> Specifica un'espressione regolare utilizzata per individuare le righe di errore nell'output dello strumento.  Si tratta di un'espressione utile per gli strumenti tramite i quali viene prodotto output con formattazione insolita.|  
|`CustomWarningRegularExpression`|Parametro `String` facoltativo.<br /><br /> Specifica un'espressione regolare utilizzata per individuare le righe di avviso nell'output dello strumento.  Si tratta di un'espressione utile per gli strumenti tramite i quali viene prodotto output con formattazione insolita.|  
|`ExitCode`|Parametro di output di sola lettura `Int32` facoltativo.<br /><br /> Specifica il codice di uscita fornito dal comando eseguito.|  
|`IgnoreExitCode`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il codice di uscita fornito dal comando eseguito viene ignorato dall'attività.  In caso contrario, viene restituito `false` se il comando eseguito restituisce un codice di uscita diverso da zero.|  
|`IgnoreStandardErrorWarningFormat`|Parametro `Boolean` facoltativo.<br /><br /> Se `false`, le righe dell'output che corrispondono al formato di errore\/avviso standard vengono selezionate e registrate come errori\/avvisi.  Se `true`, disabilitare questo comportamento.|  
|`Outputs`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi di output dell'elemento.  L'attività `Exec` non imposta questi elementi autonomamente.  È invece possibile fornirli come se fossero stati impostati dall'attività, in modo che possano essere utilizzati in una fase successiva del progetto.|  
|`StdErrEncoding`|Parametro di output `String` facoltativo.<br /><br /> Specifica la codifica del flusso di errore standard acquisito per l'attività.  Il valore predefinito è la codifica dell'output della console corrente.|  
|`StdOutEncoding`|Parametro di output `String` facoltativo.<br /><br /> Specifica la codifica del flusso di output standard acquisito per l'attività.  Il valore predefinito è la codifica dell'output della console corrente.|  
|`WorkingDirectory`|Parametro `String` facoltativo.<br /><br /> Specifica la directory in cui verrà eseguito il comando.|  
  
## Note  
 Questa attività risulta utile se non è disponibile un'attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] specifica per l'operazione che si desidera eseguire.  Tuttavia, tramite l'attività `Exec`, a differenza di un'attività più specifica, non è possibile raccogliere informazioni di output dallo strumento o dal comando eseguito.  
  
 Anziché richiamare direttamente un processo, l'attività `Exec` chiama cmd.exe.  
  
 Oltre ai parametri elencati in questo documento, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `Exec` viene utilizzata per eseguire un comando.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)