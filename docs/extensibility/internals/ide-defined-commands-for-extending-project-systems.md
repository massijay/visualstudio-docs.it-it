---
title: I comandi definiti dall&quot;IDE per l&quot;estensione di sistemi di progetto | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 19
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8ef8f9d3bd75057708f7e1d380da83a38d7efb4b
ms.lasthandoff: 02/22/2017

---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandi definiti dall'IDE per l'estensione di sistemi di progetto
Quando si desidera estendere sistemi di progetto, è possibile utilizzare i comandi e comando forniti da gruppi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Nelle sezioni seguenti vengono elencano gli elementi di comando che risultano particolarmente utili per l'estensione di sistemi di progetto.  
  
## <a name="command-menus"></a>Menu dei comandi  
 Nella tabella seguente viene illustrato i menu comando utile posizioni in cui inserire i comandi di alto livello che richiamano un'estensione di progetto.  
  
|Menu dei comandi|Descrizione|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|Il **progetto** menu di primo livello.|  
|IDM_VS_TOOL_PROJWIN|Il **Esplora** barra degli strumenti.|  
  
## <a name="shortcut-menus"></a>Menu di scelta rapida  
 Nella tabella seguente viene illustrato i menu di scelta rapida che si applicano quando si seleziona un nodo singolo nel **Esplora soluzioni**, o quando sono presenti più selezioni omogenee nel **Esplora soluzioni**, ovvero quando tutti i nodi selezionati sono dello stesso tipo.  
  
|Menu di scelta rapida|Descrizione|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Si applica quando si seleziona il nodo del progetto.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Si applica quando si seleziona un file.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Si applica quando si seleziona una cartella.|  
|IDM_VS_CTXT_WEBREFFOLDER|Si applica quando si seleziona la cartella riferimenti Web.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Si applica quando è selezionato il nodo radice riferimenti chiamato "Riferimenti".|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Si applica quando vengono selezionati nodi di riferimento; tra cui assembly, COM e solo i riferimenti di progetto. Non include riferimenti Web.|  
  
 Nella tabella seguente viene illustrato i menu di scelta rapida che vengono applicate quando la selezione nella **Esplora** si estende su più gerarchie,  
  
|Menu di scelta rapida|Descrizione|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Si applica quando la selezione corrente contiene il nodo della soluzione e i nodi di progetto principale.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Si applica quando la selezione corrente contiene gli elementi di soluzione del progetto e del nodo.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Si applica quando la selezione corrente è costituito da più radice progetto solo i nodi.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Si applica quando la selezione corrente contiene una combinazione di nodi radice del progetto ed elementi del progetto. Inoltre, la selezione può contenere il nodo della soluzione.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Si applica quando la selezione corrente contiene elementi di progetto da più progetti nella soluzione o quando vengono selezionati elementi di tipi diversi nello stesso progetto.|  
  
## <a name="command-groups"></a>Gruppi di comandi  
 Nella tabella seguente mostra i gruppi di comando che è possibile utilizzare quando si estendono progetti e che è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>menu di scelta rapida.</xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>  
  
|Gruppo di comandi|Descrizione|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Comandi per la compilazione, ricompilazione e la distribuzione del progetto.|  
|IDG_VS_CTXT_COMPILELINK|Comandi per la compilazione e collegamento del progetto.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Comandi che impostare la configurazione di progetto e sull'ordine di compilazione.|  
|IDG_VS_CTXT_PROJECT_ADD|Comandi che aggiungere elementi al progetto.|  
|IDG_VS_CTXT_PROJECT_START|Comandi per l'impostazione del progetto di avvio associato con il tasto F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Comandi per il salvataggio di elementi di progetto.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Comandi per il debug.|  
|IDG_VS_CTXT_PROJECT_SCC|Comandi per controllo del codice sorgente.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandi per tagliare, copiare e incollare le operazioni.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|I comandi che consentono l'accesso per il **le proprietà del progetto** la finestra di dialogo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Confronto tra oggetti MenuCommand e OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md)
