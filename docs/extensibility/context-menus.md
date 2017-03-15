---
title: "Menu di scelta rapida | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - menu di scelta rapida"
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Menu di scelta rapida
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I menu di scelta rapida viene visualizzato quando un utente fa clic con il pulsante destro del mouse in un'area attiva l'area client e alla cancellazione quando il pulsante destro del mouse viene rilasciato.  
  
## Menu di scelta rapida dell'editor  
 Intercettando `ECMD_SHOWCONTEXTMENU`, il servizio di linguaggio possibile controllare i menu di scelta rapida che viene visualizzato nell'editor.  To display your own context menu, handle this command when it is passed into your <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> by calling <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>.  Se non si gestisce questo comando, quindi l'ide visualizza un menu di scelta rapida standard fornito per l'editor.  È inoltre possibile controllare il contenuto del menu di scelta rapida in base al per\-marcatore.  Per ulteriori informazioni, vedere [Utilizzando gli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md) e [Intercettazione di comandi del servizio di linguaggio Legacy](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## Vedere anche  
 [Lo sviluppo di un servizio di linguaggio](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Estensione menu e comandi](../extensibility/extending-menus-and-commands.md)