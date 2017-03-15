---
title: Modifica la Shell isolata utilizzando il. File Vsct | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: a20b546c6e8d6d70a17d3d0bae575a5b2898d781
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modifica la Shell isolata utilizzando il. File Vsct
Il progetto dell'interfaccia utente per un progetto di Visual Studio shell isolata contiene un file vsct che consente di specificare quali gruppi di applicazioni e singoli comandi sono disponibili nell'applicazione. Di seguito è riportato un estratto da un file vsct non modificato.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Per impostazione predefinita, la maggior parte dei comandi e i gruppi di comandi sono inclusi. Per escludere un comando o un gruppo di comando, è sufficiente rimuovere tale comando o un gruppo.  
  
 Ad esempio, per rimuovere il riquadro successivo e precedente comandi riquadro, rimuovere il commento di `No_PaneNextPaneCommand` e `No_PanePrevPaneCommand` voci:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Per una più dettagliata di esempio queste personalizzazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>File di riferimento  
 Il file vsct predefinito per un'applicazione fa riferimento ai file seguenti. Questi file si trovano nella sottodirectory \VisualStudioIntegration\Common\Inc\ della directory di installazione di Visual Studio SDK.  
  
|File|Descrizione|  
|----------|-----------------|  
|wbids.h|Identità dell'interfaccia utente per il pacchetto Web Sfoglia.|  
|AppIDCmdUsed.vsct|Tabella di comandi per gli elementi dell'interfaccia utente di Visual Studio primari.|  
|EmulatorCmdUsed.vsct|Tabella di comandi per elementi di interfaccia emulazione editor Emacs e Brief.|  
|Vsdebugguids.h|Definisce i GUID dei comandi, pagina Opzioni e altre funzionalità del debugger di Visual Studio.|  
|VsDbgCmdUsed.vsct|Tabella di comando per il debugger.|  
  
 Il file AppIDCmdUsed.vsct include gli elementi dell'interfaccia utente di Visual Studio in base ai simboli definiti nel file vsct dell'applicazione.  
  
 Per ulteriori informazioni, vedere [la progettazione di tabella comandi XML (. File Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) e [riferimento allo Schema XML VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio isolato Shell](../extensibility/visual-studio-isolated-shell.md)
