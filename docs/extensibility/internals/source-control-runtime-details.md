---
title: "Dettagli di Runtime di controllo di origine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo del codice sorgente [Visual Studio SDK], informazioni di runtime"
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Dettagli di Runtime di controllo di origine
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un progetto verrà aggiunto al controllo del codice sorgente quando l'utente aggiunge un file del progetto al controllo del codice sorgente, o tramite un controller di automazione, ad esempio una procedura guidata.  Un progetto non specifica per se stesso incluso nel controllo del codice sorgente, supporta il controllo del codice sorgente, ma deve essere aggiunto a manualmente.  
  
## La registrazione con un pacchetto del controllo del codice sorgente  
 When a file in your project is added to source control, the environment calls <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> to provide you four opaque strings that are used as cookies by the source control system.  Archiviare queste stringhe nel file di progetto.  These strings should be passed to the Source Control Stub \(the Visual Studio component that manages source control packages\) on startup of the project type by calling <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>.  Questa operazione consente a sua volta carica il package appropriato del controllo del codice sorgente e inoltra la chiamata all'implementazione di `IVsSccManager2::RegisterSccProject`.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Supporto di controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)