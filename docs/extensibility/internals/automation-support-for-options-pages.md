---
title: "Supporto di automazione per le pagine di opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Pagine delle opzioni degli strumenti [Visual Studio SDK], supporto di automazione"
  - "automazione [Visual Studio SDK], creazione di pagine di opzioni del menu Strumenti"
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Supporto di automazione per le pagine di opzioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Package VS può fornire personalizzato **Opzioni** delle finestre di dialogo per la **strumenti** menu \(pagine delle opzioni strumenti\) in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e può renderli disponibili per il modello di automazione.  
  
## Pagine delle opzioni strumenti  
 Per creare un **Opzioni degli strumenti** pagina, un VSPackage necessario fornire un'implementazione del controllo utente restituita all'ambiente tramite l'implementazione del VSPackage del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo \(o per codice gestito di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> \(metodo\)\).  
  
 È facoltativo, ma si consiglia, per consentire l'accesso a questa nuova pagina tramite il modello di automazione. È possibile farlo tramite la procedura seguente:  
  
1.  Estendere la <xref:EnvDTE._DTE.Properties%2A> oggetto tramite l'implementazione di un oggetto derivato IDispatch.  
  
2.  Restituiscono un'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo \(o per il codice gestito di <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> \(metodo\)\) per l'oggetto derivato IDispatch.  
  
3.  Quando un consumer di automazione chiama il <xref:EnvDTE._DTE.Properties%2A> metodo su un elemento personalizzato **opzione** pagina delle proprietà, l'ambiente utilizza il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> per ottenere un oggetto personalizzato **Strumenti opzioni** implementazione di automazione della pagina.  
  
4.  L'oggetto di automazione del VSPackage viene quindi utilizzato per fornire ogni <xref:EnvDTE.Property> restituito da <xref:EnvDTE._DTE.Properties%2A>.  
  
 Per un esempio di implementazione di una pagina di opzioni degli strumenti personalizzata, vedere [Esempi di VSSDK](../../misc/vssdk-samples.md).  
  
## Vedere anche  
 [Esposizione di oggetti di progetto](../../extensibility/internals/exposing-project-objects.md)