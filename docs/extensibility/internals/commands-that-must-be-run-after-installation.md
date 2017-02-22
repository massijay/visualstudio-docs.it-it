---
title: "Comandi devono essere eseguiti dopo l&#39;installazione | Microsoft Docs"
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
  - "comandi di post-installazione"
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Comandi devono essere eseguiti dopo l&#39;installazione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Se si distribuisce l'estensione tramite un file con estensione msi, è necessario eseguire `devenv /setup` come parte dell'installazione in modo che Visual Studio individuare le estensioni.  
  
> [!NOTE]
>  Le informazioni contenute in questo argomento si applicano a ricerca DevEnv con Visual Studio 2008 e versioni precedenti. Per informazioni su come individuare DevEnv con le versioni successive di Visual Studio, vedere [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
## Ricerca devenv.exe  
 È possibile individuare ogni versione devenv.exe dal Registro di sistema valori [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] scrivere programmi di installazione, utilizzando la tabella RegLocator e la tabella AppSearch per archiviare i valori del Registro di sistema come proprietà. Per altre informazioni, vedere [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
### Righe della tabella RegLocator individuare devenv.exe da diverse versioni di Visual Studio  
  
|Signature\_|Radice|Chiave|Nome|Tipo|  
|-----------------|------------|------------|----------|----------|  
|RL\_DevenvExe\_2002|2|SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2003|2|SOFTWARE\\Microsoft\\VisualStudio\\7.1\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2005|2|SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2008|2|SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS|EnvironmentPath|2|  
  
### Righe della tabella AppSearch le righe della tabella RegLocator corrispondente  
  
|Proprietà|Signature\_|  
|---------------|-----------------|  
|DEVENV\_EXE\_2002|RL\_DevenvExe\_2002|  
|DEVENV\_EXE\_2003|RL\_DevenvExe\_2003|  
|DEVENV\_EXE\_2005|RL\_DevenvExe\_2005|  
|DEVENV\_EXE\_2008|RL\_DevenvExe\_2008|  
  
 Ad esempio, il programma di installazione di Visual Studio scrive il valore del Registro di sistema di **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS\\EnvironmentPath** come **C:\\VS2008\\Common7\\IDE\\devenv.exe**, un percorso completo del file eseguibile deve essere eseguito il programma di installazione.  
  
 **Nota** perché la colonna di tipo RegLocator è 2, non è necessario specificare ulteriori informazioni sulla versione nella tabella di firma.  
  
## Devenv.exe in esecuzione  
 Dopo aver AppSearch azione standard viene eseguito il programma di installazione, ogni proprietà nella tabella AppSearch ha un valore che punta al file devenv.exe per la versione corrispondente di Visual Studio. Se uno dei valori del Registro di sistema non sono presente, perché non è installata la versione di Visual Studio, la proprietà specificata è impostata su null.  
  
 Windows Installer supporta l'esecuzione di un eseguibile a cui fa riferimento una proprietà tramite un'azione personalizzata digita 50. L'azione personalizzata deve includere le opzioni di esecuzione di script, msidbCustomActionTypeInScript \(1024\) e msidbCustomActionTypeCommit \(512\), per assicurarsi che il package VS è stato installato prima di integrare in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni, vedere tabella CustomAction e opzioni di esecuzione negli Script di azioni personalizzate.  
  
 Azioni personalizzate di tipo 50 specificano la proprietà contenente il file eseguibile come valore della colonna di origine e gli argomenti della riga di comando nella colonna di destinazione.  
  
### Righe della tabella CustomAction eseguire devenv.exe  
  
|Azione|Tipo|Origine|destinazione|  
|------------|----------|-------------|------------------|  
|CA\_RunDevenv2002|1586|DEVENV\_EXE\_2002|\/Setup|  
|CA\_RunDevenv2003|1586|DEVENV\_EXE\_2003|\/Setup|  
|CA\_RunDevenv2005|1586|DEVENV\_EXE\_2005|\/Setup|  
|CA\_RunDevenv2008|1586|DEVENV\_EXE\_2008|\/Setup|  
  
 Azioni personalizzate devono essere create nella tabella InstallExecuteSequence per pianificarli per l'esecuzione durante l'installazione. Utilizzare la proprietà corrispondente in ogni riga della colonna condizione per evitare che l'azione personalizzata viene eseguito se la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non è installato nel sistema.  
  
> [!NOTE]
>  `Null` restituiscono proprietà `False` quando utilizzata in condizioni.  
  
 Il valore della colonna della sequenza per ogni azione personalizzata dipende da altri valori di sequenza nel pacchetto Windows Installer. I valori di sequenza, verificare che le azioni personalizzate devenv.exe runas vicino possibile ai immediatamente prima dell'azione InstallFinalize standard.  
  
### Tabella InstallExecuteSequence per pianificare le azioni personalizzate devenv.exe  
  
|Azione|Condizione|Sequence|  
|------------|----------------|--------------|  
|CA\_RunDevenv2002|DEVENV\_EXE\_2002|6602|  
|CA\_RunDevenv2003|DEVENV\_EXE\_2003|6603|  
|CA\_RunDevenv2005|DEVENV\_EXE\_2005|6605|  
|CA\_RunDevenv2008|DEVENV\_EXE\_2008|6608|  
  
## Vedere anche  
 [L'installazione di VS con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)