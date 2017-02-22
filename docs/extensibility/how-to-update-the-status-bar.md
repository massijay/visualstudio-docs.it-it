---
title: "Procedura: aggiornare la barra di stato | Microsoft Docs"
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
  - "editor [Visual Studio SDK], legacy - Aggiorna sulla barra di stato"
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: aggiornare la barra di stato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**barra di stato** è una barra di controllo ha individuato nella parte inferiore di molte finestre dell'applicazione che contiene una o più righe o indicatori del testo dello stato.  
  
### Per aggiornare la barra di stato  
  
1.  Utilizzo <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> su ogni singolo oggetto visualizzazione \(DocView\) che l'editor consente, ad esempio una visualizzazione form e una visualizzazione codice.  
  
2.  Quando l'ide chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, aggiornare le informazioni in **barra di stato** chiamando i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  L'ide chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> solo quando la finestra del documento inizialmente viene attivata.  Per il resto del tempo che la finestra del documento è attiva, è necessario aggiornare le informazioni di **barra di stato** come cambia lo stato dell'editor.  
  
## Programmazione efficiente  
 **barra di stato** contiene quattro campi separati:  
  
-   Testo dello stato  
  
-   Indicatore di stato  
  
-   icona animata  
  
-   Informazioni dell'editor  
  
 Per ulteriori informazioni, vedere [Barre di stato](/visual-cpp/mfc/status-bars).  
  
 L'ide automaticamente al metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> dell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> quando la finestra del documento è attivata.  
  
 Il responsabile dell'implementazione di un VSPackage è responsabile dell'aggiornamento il testo dello stato nella barra di stato.  L'ide reimposta questa stringa a " pronto " se il campo di testo dello stato è impostato per svuotare il testo \(""\) in fase di inattività.  
  
## Vedere anche  
 [Barre di stato](/visual-cpp/mfc/status-bars)