---
title: "Oggetto VSCodeWindow | Microsoft Docs"
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
  - "VSCodeWindow"
helpviewer_keywords: 
  - "visualizzazioni [Visual Studio SDK], oggetto VSCodeWindow"
  - "Oggetto VsCodeWindow"
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Oggetto VSCodeWindow
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una finestra del codice è una finestra del documento specializzato che può includere uno o più visualizzazioni di testo, in genere il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.  
  
 Un'architettura, la finestra del codice è una finestra del documento che si trova all'interno di una cornice di finestra. A livello funzionale, la finestra del codice è semplicemente una finestra del documento con funzionalità aggiuntive. Nella modalità di interfaccia a documenti multipli \(MDI\), la finestra del codice è la cornice figlio MDI. Per altre informazioni, vedere [Personalizzazione di Windows di codice tramite l'API Legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Nella tabella seguente sono incluse le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> oggetto.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornisce un meccanismo di accesso generici per individuare un servizio che identifica un identificatore univoco globale \(GUID\).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Rappresenta un elemento figlio MDI \(interfaccia\) di documento più contenente una o più visualizzazioni di codice.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Riempie una cornice di finestra.|  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Figures Edit](http://msdn.microsoft.com/it-it/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)