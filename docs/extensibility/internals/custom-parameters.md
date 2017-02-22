---
title: "Parametri personalizzati | Microsoft Docs"
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
  - "procedure guidate, parametri personalizzati"
  - "parametri personalizzati"
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Parametri personalizzati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

I parametri personalizzati che controllano l'operazione di una procedura guidata al termine di una procedura guidata ha avviato.  Un file correlato VSZ viene fornita una matrice di parametri definiti dall'utente che verranno compressi dall'ambiente di sviluppo integrato \(IDE\) \(IDE\) e passati alla procedura guidata come matrice di stringhe all'avvio della procedura guidata.  La procedura guidata quindi analizza la matrice di stringhe e utilizza le informazioni per controllare effettiva passaggi della procedura guidata.  In questo modo, una procedura guidata può personalizzare la funzionalità in base al contenuto del file VSZ.  
  
 I parametri di contesto, di altra parte, definire lo stato del progetto all'avvio della procedura guidata.  Per ulteriori informazioni, vedere [Parametri di contesto](../../extensibility/internals/context-parameters.md).  
  
 Di seguito è riportato un esempio di un file VSZ con i parametri personalizzati:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 L'autore del file VSZ aggiunge i valori dei parametri.  Quando un utente seleziona **nuovo progetto** o **Aggiungi nuovo elemento** il menu File oppure fare clic con il pulsante destro del mouse su un progetto in **Esplora soluzioni**, l'ide raccoglie questi valori in una matrice di stringhe.  The IDE then calls the project's <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> method with the <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag set, and the project calls the <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> method that is responsible for running the wizard and returning the result.  
  
 La procedura guidata è responsabile dell'analisi la matrice di stringhe e di operazioni sulle stringhe in modo appropriato.  In questo modo, l'implementazione dei parametri personalizzati è possibile creare una procedura guidata che esegue una varietà di funzioni.  Ovvero una procedura guidata può avere tre diversi file VSZ.  Ogni file passa set di parametri personalizzati per controllare il comportamento della procedura guidata in diverse situazioni.  
  
 Per ulteriori informazioni, vedere [Procedura guidata \(. File vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [Procedura guidata \(. File vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)