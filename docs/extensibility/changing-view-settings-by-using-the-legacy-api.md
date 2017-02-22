---
title: "Modifica delle impostazioni di visualizzazione tramite l&#39;API Legacy | Microsoft Docs"
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
  - "editor [Visual Studio SDK], legacy - modifica delle impostazioni di visualizzazione"
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Modifica delle impostazioni di visualizzazione tramite l&#39;API Legacy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le impostazioni per le funzionalità principali dell'editor, ad esempio a capo automatico, margine della selezione e spazio virtuale, può essere modificato dall'utente tramite la finestra di dialogo di **opzioni** .  Tuttavia, è anche possibile modificare queste impostazioni a livello di codice.  
  
## Modificando le impostazioni utilizzando le API legacy  
 L'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> espone un insieme di proprietà dell'editor di testo.  La visualizzazione di testo contiene una categoria di proprietà \(GUID\_EditPropCategory\_View\_MasterSettings\) che rappresenta il gruppo di impostazioni a livello di codice modificate per la visualizzazione di testo.  Le impostazioni una volta di visualizzazione sono state modificate in questo modo, non è possibile modificare nella finestra di dialogo di **opzioni** fino a reimpostarle esso.  
  
 Segue il processo tipico per modificare le impostazioni di visualizzazione per un'istanza dell'editor principale.  
  
1.  Chiamata `QueryInterface` su \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>\) per l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> .  
  
2.  Chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> , specificando un valore di GUID\_EditPropCategory\_View\_MasterSettings per il parametro di `rguidCategory` .  
  
     Utilizzando questo restituisce un puntatore all'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> , che contiene l'insieme di proprietà si forza per la visualizzazione.  Le impostazioni in questo gruppo in modo permanente sono si forza.  Se un'impostazione non è in questo gruppo, quindi seguirà le opzioni specificate nella finestra di dialogo di **opzioni** o nei controlli utente.  
  
3.  Chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> , specificando il valore appropriato delle impostazioni nel parametro di `idprop` .  
  
     Ad esempio, imporre a capo automatico, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> di chiamata e specificare un valore di VSEDITPROPID\_ViewLangOpt\_WordWrap, `vt` per il parametro di `idprop` .  In questa chiamata, `vt` è un VARIANT di tipo VT\_BOOL e `vt.boolVal` è VARIANT\_TRUE.  
  
## Reimpostare le impostazioni di visualizzazione di modifica  
 Per reimpostare qualsiasi impostazione di visualizzazione viene modificata per un'istanza dell'editor principale, chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> e specificare il valore appropriato impostazione del parametro di `idprop` .  
  
 For example, to allow word wrap to float freely, you would remove it from the property category by calling <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> and specifying a value of VSEDITPROPID\_ViewLangOpt\_WordWrap for the `idprop` parameter.  
  
 Per rimuovere tutte le impostazioni modificate nell'editor principale immediatamente, specificare il valore di VSEDITPROPID\_ViewComposite\_AllCodeWindowDefaults, VT per il parametro di `idprop` .  In questa chiamata, il VT è un VARIANT di tipo VT\_BOOL e vt.boolVal è VARIANT\_TRUE.  
  
## Vedere anche  
 [Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)   
 [Accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md)