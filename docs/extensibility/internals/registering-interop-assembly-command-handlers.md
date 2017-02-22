---
title: "Registrazione dei gestori di comando di Assembly di interoperabilit&#224; | Microsoft Docs"
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
  - "assembly di interoperabilità, gestori di comandi"
  - "comandi (gestione) con gli assembly di interoperabilità, la registrazione"
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrazione dei gestori di comando di Assembly di interoperabilit&#224;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È necessario registrare un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modo che l'ambiente di sviluppo integrato \(IDE\) consente di indirizzare i comandi correttamente.  
  
 Il Registro di sistema può essere aggiornato mediante la modifica manuale o tramite un file di registro \(con estensione RGS\). Per altre informazioni, vedere [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
 Il Framework di pacchetto gestito \(MPF\) fornisce questa funzionalità tramite la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> classe.  
  
 [Command Table Format Reference](http://msdn.microsoft.com/it-it/09e9c6ef-9863-48de-9483-d45b7b7c798f) risorse si trovano nelle DLL dell'interfaccia utente di satellite non gestita.  
  
## Registrazione del gestore comandi di un package VS  
 Un package VS che agisce come un gestore per l'interfaccia utente \(UI\)\-i comandi di base richiede una voce del Registro di sistema denominata dopo il package VS `GUID`. Questa voce del Registro di sistema specifica il percorso del file di risorse dell'interfaccia utente del VSPackage e della risorsa di menu all'interno del file. La voce del Registro di sistema stesso si trova in HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\*\< versione \>*\\Menus, dove *\< versione \>* è la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ad esempio 9.0.  
  
> [!NOTE]
>  Il percorso radice dell'HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< versione \>* può essere sottoposto a override con un'alternativa principale quando il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell viene inizializzata. Per ulteriori informazioni sul percorso radice, vedere [L'installazione di VS con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### La voce del Registro di sistema di risorse CTMENU  
 La struttura della voce del Registro di sistema è:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\ Menus\ <GUID> = <Resource Information>  
```  
  
 \<*GUID*\> è il `GUID` del VSPackage nel formato {XXXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXX}.  
  
 *\< informazioni sulle risorse \>* è costituito da tre elementi, separati da virgole. Questi elementi sono, nell'ordine:  
  
 \<*Percorso DLL risorse*\>, \<*ID risorsa Menu*\>, \<*Menu versione*\>  
  
 Nella tabella seguente vengono descritti i campi di \<*informazioni sulle risorse*\>.  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|\<*Percorso DLL risorse*\>|Questo è il percorso completo per la DLL che contiene la risorsa menu risorse o questo viene lasciato vuoto, che indica che la risorsa del VSPackage DLL viene utilizzato \(come specificato nella sottochiave pacchetti in cui è registrato il package VS stesso\).<br /><br /> È consuetudine lasciare vuoto questo campo.|  
|\<*ID risorsa menu*\>|Questo è l'ID della risorsa di `CTMENU` risorse che contiene tutti gli elementi dell'interfaccia utente per il package VS compilate da un [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) file.|  
|\<*Menu versione*\>|Questo è un numero utilizzato come una versione per il `CTMENU` risorse.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizza questo valore per determinare se è necessario unire di nuovo il contenuto di `CTMENU` risorsa con la cache di tutti `CTMENU` risorse. Eseguendo il comando setup devenv viene attivato un unire di nuovo.<br /><br /> Questo valore dovrebbe essere inizialmente impostato su 1 e incrementato dopo ogni modifica di `CTMENU` risorse e prima di unire di nuovo.|  
  
### Esempio  
 Di seguito è riportato un esempio di un paio di voci di risorsa:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\ Menus\ {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10 {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandi e menu che utilizzano gli assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)