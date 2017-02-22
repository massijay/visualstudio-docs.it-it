---
title: "Automazione per la configurazione e oggetti SelectedItem | Microsoft Docs"
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
  - "automazione [Visual Studio SDK], oggetto SelectedItem"
  - "automazione [Visual Studio SDK], compilazioni"
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Automazione per la configurazione e oggetti SelectedItem
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile automatizzare la compilazione e processi selezionati dell'elemento in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Automazione per le compilazioni  
 La compilazione o la configurazione dispone di un modello di automazione fornito quando si distribuisce <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>.  Per ulteriori informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md).  
  
 Se si crea un VSPackage e si desidera controllare le opzioni di configurazione, è necessario utilizzare il modello di automazione.  
  
## automazione per SelectedItem  
 Non è necessario fornire un'implementazione per l'oggetto di `SelectedItem` perché Visual Studio include un'implementazione standard.  Tuttavia, è possibile implementare l'oggetto di `SelectedItem` se si preferisce.  È necessario implementare un oggetto che contiene l'interfaccia di `SelectedItem` e restituire una risposta a una chiamata al metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> con VSITEMID impostato su <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Che contribuiscono al modello di automazione](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md)