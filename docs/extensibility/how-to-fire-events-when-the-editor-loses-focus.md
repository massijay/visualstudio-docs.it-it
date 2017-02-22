---
title: "Procedura: generare eventi quando l&#39;Editor non &#232; attivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - generano eventi perde lo stato attivo"
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: generare eventi quando l&#39;Editor non &#232; attivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È talvolta necessario sapere quando un editor perde lo stato attivo sulla struttura della finestra.  Ad esempio, potrebbe essere necessario aggiornare la versione di estrarre il codice da una finestra del codice dopo che l'editor non è più attivo su.  La procedura riportata di seguito vengono illustrate le operazioni necessarie per utilizzare per ricevere la notifica dello stato attivo perdente dell'editor.  
  
### Per generare un evento in risposta allo stato attivo perdente dell'editor  
  
1.  Eventi di selezione del monitor per ottenere un oggetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> da <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Call <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> and provide it your <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> object.  
  
3.  Nella chiamata all'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged\(System.UInt32, System.Object  
  
4.  Verificare il parametro di `varValueNew` per due fattori:  
  
    1.  La struttura della finestra da cercare.  
  
    2.  Il punto in cui il programma perde la selezione a tale struttura della finestra.