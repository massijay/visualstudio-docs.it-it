---
title: "Procedura: utilizzare gli indicatori di testo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], - legacy utilizzando gli indicatori di testo"
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Procedura: utilizzare gli indicatori di testo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I marcatori di testo possono essere applicati per modificare un oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
## Procedure  
  
#### Per applicare i marcatori di testo  
  
1.  Ottenere un'istanza della classe di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> .  
  
    > [!NOTE]
    >  L'editor principale applica automaticamente i marcatori di testo standard a qualsiasi documento che si sta modificando e non deve essere necessario applicare i marcatori di testo standard in modo esplicito.  
  
2.  Ottenere un tipo ID del marcatore del marcatore desiderate chiamando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> con `GUID` del marcatore di testo si desidera utilizzare.  
  
    > [!NOTE]
    >  Non utilizzare `GUID` del package VS o del servizio che fornisce il marcatore di testo.  
  
3.  Utilizzare il tipo ID del marcatore ottenuto chiamando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> come parametro per chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> o il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> per applicare un marcatore di testo in una determinata area di testo.  
  
#### Per aggiungere funzionalità ai marcatori di testo  
  
1.  Può essere utile aggiungere funzionalità aggiuntive a un marcatore di testo, ad esempio le descrizioni comandi, un menu di scelta rapida speciale, o gestore per le condizioni speciali.  a tale scopo:  
  
2.  creare un oggetto che implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
3.  Se la funzionalità aggiuntiva è desiderata, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>e le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> lo stesso oggetto che implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
4.  Passare l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> creati, la chiamata al metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> o al metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> utilizzato per applicare il marcatore di testo in una determinata area di testo.  
  
5.  Quando si aggiunge il supporto del menu di scelta rapida a un'area del marcatore di testo è necessario creare il menu.  
  
     Per ulteriori informazioni su come creare un menu di scelta rapida, [Menu di scelta rapida](../extensibility/context-menus.md)vedere.  
  
6.  L'ambiente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chiama i metodi delle interfacce fornite, ad esempio il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> il metodo, o di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> in base alle necessità.  
  
## Vedere anche  
 [Utilizzando gli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: creare indicatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)