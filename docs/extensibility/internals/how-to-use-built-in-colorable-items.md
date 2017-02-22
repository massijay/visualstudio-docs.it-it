---
title: "Procedura: utilizzare gli elementi di colori predefiniti | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "colori"
  - "servizi di linguaggio, agli elementi incorporati e colori"
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: utilizzare gli elementi di colori predefiniti
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Prima di utilizzare gli elementi colorabili incorporati, è innanzitutto necessario segnalare all'ambiente \(IDE\) di sviluppo integrato che non è fornire degli elementi colorabili personalizzati, che in questo caso sono oggetti di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> .  A tale scopo una voce del Registro di sistema per il servizio di linguaggio.  
  
### Per utilizzare gli elementi colorabili incorporati  
  
1.  Sotto HKEY\_LOCAL\_MACHINE \\VisualStudio \\*X.Y*\\Languages\\Language Services \\*Nome della lingua*, dove *X.Y* è una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e *Nome della lingua* è il nome del linguaggio, creare un valore di voci del Registro di sistema DWORD `RequestStockColors`chiamato.  
  
2.  Impostare il valore di voci del Registro di sistema di `RequestStockColors` a 1.  
  
     After you create the registry entry, your colorizer's <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> method can use the members of the <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumeration to fill in the array of color attributes for use by the editor.  
  
    > [!NOTE]
    >  Non impostare questa voce del Registro di sistema se si immette gli elementi colorabili personalizzati.  Per ulteriori informazioni, vedere [Elementi di colori personalizzati](../../extensibility/internals/custom-colorable-items.md).  
  
## Vedere anche  
 [Colorazione in editor personalizzati della sintassi](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [In un servizio di linguaggio Legacy colorazione della sintassi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementazione di colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Elementi di colori personalizzati](../../extensibility/internals/custom-colorable-items.md)   
 [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)