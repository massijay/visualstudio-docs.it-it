---
title: "Procedura: aggiungere testo Standard marcatori | Microsoft Docs"
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
  - "editor [Visual Studio SDK], legacy - degli indicatori di testo standard"
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: aggiungere testo Standard marcatori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare la procedura riportata di seguito per creare uno dei tipi predefiniti del marcatore di testo forniti editor di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
### Per creare un marcatore di testo  
  
1.  A seconda se si utilizza uno o un sistema di coordinate bidimensionale, chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> o il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> per creare un nuovo marcatore di testo.  
  
     In questa chiamata al metodo, specificare un tipo del marcatore, un intervallo di testo per creare il marcatore più e un'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  Questo metodo restituisce un puntatore al marcatore di testo appena creato.  I tipi del marcatore derivano dall'enumerazione di <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> .  Specificare un'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> se si desidera essere informati degli eventi del marcatore.  
  
    > [!NOTE]
    >  Creare i marcatori di testo nel thread principale dell'interfaccia utente solo.  The core editor relies on the contents of the text buffer to create text markers and the text buffer is not thread safe.  
  
## Aggiunta di un comando personalizzato  
 Implementare l'interfaccia di `IVsTextMarkerClient` e fornire un puntatore a un marcatore migliorano il comportamento del marcatore in diversi modi.  Innanzitutto, questo consente di fornire suggerimenti per il marcatore e di eseguire comandi.  Ciò consente anche notifiche di eventi di ricezione per i singoli marcatori e creare un menu di scelta rapida personalizzato sul marcatore.  Utilizzare la procedura riportata di seguito per aggiungere un comando al menu di scelta rapida del marcatore.  
  
#### Per aggiungere un comando al menu di scelta rapida  
  
1.  Prima che il menu di scelta rapida visualizzato, l'ambiente chiama il metodo e quelle di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> è un puntatore al marcatore di testo interessata e il numero dell'elemento del comando nel menu di scelta rapida.  
  
     Ad esempio, i controlli punto di interruzione\-specifici scegliere dal menu di scelta rapida sono **rimuovere il punto di interruzione** con **nuovo punto di interruzione**, come visualizzato nell'schermata.  
  
     ![Menu di scelta rapida Marcatore](../extensibility/media/vsmarkercontextmenu.png "vsMarkercontextmenu")  
  
2.  Passare a un testo che identifica il nome del comando personalizzato.  Ad esempio, **rimuovere il punto di interruzione** potrebbe essere un comando personalizzato se l'ambiente non è già una.  Viene passato anche indietro se il comando è supportato, disponibile e attivato e\/o un cambio di passare di accensione.  L'ambiente utilizza queste informazioni per visualizzare il comando personalizzato nel menu di scelta rapida in modo corretto.  
  
3.  Per eseguire il comando, le chiamate al metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> , passando un puntatore al marcatore di testo e il numero di comando scegliere dal menu di scelta rapida.  
  
     Utilizzare queste informazioni dalla chiamata per eseguire eventuali azioni del marcatore di testo del comando personalizzato definisce.  
  
## Vedere anche  
 [Utilizzando gli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)   
 [Procedura: creare indicatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: utilizzare gli indicatori di testo](../extensibility/how-to-use-text-markers.md)