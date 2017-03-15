---
title: "Procedura: supportare la struttura in un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], comprimere al comando definizioni"
  - "servizi Language, supporto Comprimi al comando definizioni"
  - "testo nascosto, Comprimi al comando definizioni"
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: supportare la struttura in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La struttura viene utilizzata per espandere o comprimere aree diverse del testo. Viene utilizzata la struttura possono essere definiti in modo diverso in lingue diverse. Per altre informazioni, vedere [Struttura](../../ide/outlining.md).  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni sulla nuova modalità per implementare la struttura, vedere [Procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 Di seguito viene illustrato come supportare questo comando per il servizio di linguaggio.  
  
### Per supportare la struttura  
  
1.  Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> sull'oggetto servizio del linguaggio.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> sull'oggetto sessione per aggiungere nuove aree della struttura corrente della struttura.  
  
## Programmazione efficiente  
 Quando un utente seleziona **Comprimi alle definizioni** sul **struttura** menu, le chiamate IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> del servizio di linguaggio.  
  
 Quando questo metodo viene chiamato, l'IDE passa un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> puntatore \(un puntatore a un buffer di testo\) e un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> \(un puntatore alla sessione della struttura corrente\).  
  
 È possibile chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> metodo per più aree della struttura, specificando in queste aree di `rgOutlnReg` parametro. Il `rgOutlnReg` parametro è un <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> struttura. Questo processo consente di specificare le caratteristiche diverse dell'area di nascosto, ad esempio se una determinata area è espanso o compresso.  
  
> [!NOTE]
>  Prestare attenzione su come nascondere i caratteri di nuova riga. Testo nascosto deve estendere dall'inizio della prima riga e l'ultimo carattere dell'ultima riga in una sezione, lasciando visibili il carattere di nuova riga finale.  
  
## Vedere anche  
 [Procedura: fornire supporto per il testo nascosto in un servizio di linguaggio Legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Procedura: fornire il supporto esteso della struttura in un servizio di linguaggio Legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)