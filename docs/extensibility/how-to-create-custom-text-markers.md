---
title: "Procedura: creare indicatori di testo personalizzato | Microsoft Docs"
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
  - "editor [Visual Studio SDK], legacy - indicatori di testo personalizzato"
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: creare indicatori di testo personalizzato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si desidera creare un marcatore di testo personalizzato per evidenziare o organizzare il codice, è necessario eseguire i passaggi seguenti:  
  
-   Registrare il nuovo indicatore di testo, in modo che altri strumenti possono accedervi  
  
-   Fornire un'implementazione predefinita e la configurazione dell'indicatore di testo  
  
-   Creare un servizio che può essere utilizzato da altri processi per rendere utilizzare dell'indicatore di testo  
  
 Per informazioni dettagliate su come applicare un indicatore di testo a un'area di codice, vedere [procedura: utilizzare testo marcatori](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Per registrare un marcatore personalizzato  
  
1.  Creare una voce del Registro di sistema come segue:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< versione>*\Text Editor\External marcatori\\*\< MarkerGUID>*  
  
     *\< MarkerGUID>*è un `GUID` utilizzato per identificare il marcatore da aggiungere  
  
     *\< versione>* è la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ad esempio 8.0  
  
     *\< PackageGUID>* è il GUID del package VS che implementa l'oggetto di automazione.  
  
    > [!NOTE]
    >  Il percorso radice dell'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< versione>* può essere sostituita con una radice alternativa quando viene inizializzata la shell di Visual Studio, per ulteriori informazioni, vedere [Opzioni della riga di comando](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2.  Creare quattro valori in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< versione>*\Text Editor\External marcatori\\*\< MarkerGUID>*  
  
    -   (Predefinito)  
  
    -   Servizio  
  
    -   DisplayName  
  
    -   Pacchetto  
  
    -   `Default` è una voce facoltativa di tipo REG_SZ. Se è impostata, il valore della voce è una stringa contenente alcuni utili informazioni di identificazione, ad esempio "Custom marcatore di testo".  
  
    -   `Service` è una voce di tipo REG_SZ contenente la stringa del GUID del servizio che fornisce il marcatore di testo personalizzato da proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Il formato è {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
    -   `DisplayName` è una voce di tipo REG_SZ contenente l'ID di risorsa del nome dell'indicatore di testo personalizzato. Il formato è #YYYY.  
  
    -   `Package` voce di tipo REG_SZ contenente il `GUID` di package VS che fornisce il servizio elencato in servizio. Il formato è {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Per creare un indicatore di testo personalizzato  
  
1.  Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfaccia.  
  
     L'implementazione di questa interfaccia definisce il comportamento e l'aspetto del tipo di marcatore personalizzata.  
  
     Questa interfaccia viene chiamata quando  
  
    1.  Un utente avvia l'IDE per la prima volta.  
  
    2.  Un utente seleziona il **predefinite** in corrispondenza di **tipi di carattere e colori** pagina delle proprietà nel **ambiente** cartella, nel riquadro a sinistra del **Opzioni** la finestra di dialogo ottenuto dal **strumenti** menu dell'IDE.  
  
2.  Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> (metodo), che specifica quali `IVsPackageDefinedTextMarkerType` implementazione deve essere restituito in base al tipo di marcatore GUID specificato nella chiamata al metodo.  
  
     L'ambiente chiama questa volta il primo metodo viene creato il tipo di marcatore personalizzata e specifica un GUID che identifica il tipo di marcatore personalizzata.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Per indicare il tipo di marcatore come servizio  
  
1.  Chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> metodo per <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> viene restituito.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> (metodo), che specifica il GUID che identifica il servizio di tipo marcatore personalizzata e fornendo un puntatore all'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia. Il <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementazione deve restituire un puntatore all'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interfaccia.  
  
     Un cookie univoco che identifica il servizio viene restituito. È possibile utilizzare il cookie in un secondo momento per revocare il servizio di tipo marcatore personalizzata chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodo il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaccia che specifica il valore del cookie.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzando gli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)   
 [Procedura: utilizzare gli indicatori di testo](../extensibility/how-to-use-text-markers.md)