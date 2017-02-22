---
title: "Procedura: implementare Trova e Sostituisci meccanismo | Microsoft Docs"
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
  - "editor [Visual Studio SDK], legacy - Trova e Sostituisci"
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: implementare Trova e Sostituisci meccanismo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio fornisce due modalità di implementazione della ricerca e sostituzione.  Un modo consiste un'immagine del testo alla shell e lo ha lasciato gestire la ricerca, evidenziando e sostituire il testo.  Ciò consente agli utenti di specificare gli intervalli di testo.  In alternativa, il package VS possibile controllare questa funzionalità stessa.  In entrambi i casi è necessario notificare alla shell sulla destinazione corrente e destinazioni per tutti i documenti aperti.  
  
### Per implementare il comando trova\/sostituire  
  
1.  Implementare l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> su uno degli oggetti restituiti dalle proprietà <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>frame.  Se si crea un editor personalizzato, è necessario implementare questa interfaccia come parte di una classe di editor personalizzato.  
  
2.  Utilizzare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> per specificare le opzioni che supporta dell'editor e indicare se implementano la ricerca di immagine di testo.  
  
     If your editor supports text image searching, implement <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     In caso contrario, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> e implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Se si distribuisce l'entity\_M:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find\(System.String, System.UInt32, System.Int32, Microsoft.VisualStudio.TextManager.Interop.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>