---
title: "Elemento VisibilityItem | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento VisibilityItem (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, VisibilityItem"
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Elemento VisibilityItem
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il `VisibilityItem` elemento determina la visibilità statica di comandi e barre degli strumenti. Ogni voce identifica un comando o menu e un contesto dell'interfaccia utente di comando associato. Visual Studio rileva comandi, menu e barre degli strumenti e la visibilità, senza caricare il package VS che li definiscono. L'IDE utilizza il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo per determinare se un contesto dell'interfaccia utente del comando è attivo.  
  
 Dopo il caricamento di VSPackage Visual Studio si presuppone la visibilità di comando per essere determinato dal VSPackage anziché `VisibilityItem`. Per determinare la visibilità del comando, è possibile implementare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore eventi o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \(metodo\), a seconda di come è stato implementato il comando.  
  
 Un comando o un menu con un `VisibilityItem` elemento viene visualizzato solo quando il contesto associato è attivo. È possibile associare un singolo comando, menu o sulla barra degli strumenti con uno o più contesti dell'interfaccia utente di comando mediante l'inclusione di una voce per ogni combinazione di comandi del contesto. Se un comando o un menu è associato a più contesti dell'interfaccia utente di comando, quindi il comando o un menu è visibile quando è attivo uno qualsiasi dei contesti dell'interfaccia utente comando associato.  
  
 Il `VisibilityItem` elemento si applica solo ai comandi, menu e barre degli strumenti, non ai gruppi. Un elemento che non dispone di un processo di `VisibilityItem` elemento è visibile ogni volta che il relativo menu padre è attivo.  
  
## Sintassi  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|GUID|Obbligatorio. GUID dell'identificatore di comando\/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando\/ID GUID.|  
|contesto|Obbligatorio. Il contesto dell'interfaccia utente in cui il comando è visibile.|  
|Condizione|Facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementi figlio  
 Nessuna  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Il `VisibilityConstraints` elemento determina la visibilità statica dei gruppi di comandi e barre degli strumenti.|  
  
## Note  
 I contesti dell'interfaccia utente di Visual Studio standard definiti nel *il percorso di installazione di Visual Studio SDK*\\VisualStudioIntegration\\Common\\Inc\\vsshlids.h file nonché come il <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> e <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classi. Un set più completo dei contesti dell'interfaccia utente è definito nel <xref:Microsoft.VisualStudio.VSConstants> \(classe\).  
  
## Esempio  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)