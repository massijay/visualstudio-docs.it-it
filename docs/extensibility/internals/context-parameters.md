---
title: Parametri di contesto | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 143a8738f2eb6517c1642eafd2b9629e0fa8f84d
ms.lasthandoff: 02/22/2017

---
# <a name="context-parameters"></a>Parametri di contesto
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE), è possibile aggiungere le procedure guidate per la **nuovo progetto**, **Aggiungi nuovo elemento**, o **aggiungere sottoprogetto** finestre di dialogo. Sono disponibili su procedure guidate di aggiunta di **File** menu o facendo clic su un progetto in **Esplora soluzioni**. L'IDE passa i parametri di contesto per l'implementazione della procedura guidata. Parametri di contesto di definiscono lo stato del progetto quando l'IDE chiama la procedura guidata.  
  
 Procedure guidate di avvio dell'IDE, impostando il <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>flag nella chiamata dell'IDE per la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>metodo per il progetto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> </xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> Se è impostata, è necessario che il progetto di `IVsExtensibility::RunWizardFile` metodo da eseguire utilizzando il nome della procedura guidata registrato o GUID e altri parametri di contesto che l'IDE passa a esso.  
  
## <a name="context-parameters-for-new-project"></a>Parametri di contesto per nuovo progetto  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`WizardType`|Creazione guidata tipo di registrazione (<xref:EnvDTE.Constants.vsWizardNewProject>) o il GUID che indica il tipo di procedura guidata.</xref:EnvDTE.Constants.vsWizardNewProject> Nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementazione, il GUID per la procedura guidata è {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Stringa che è univoco [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nome del progetto.|  
|`LocalDirectory`|Percorso locale dell'utilizzo di file di progetto.|  
|`InstallationDirectory`|Percorso della directory di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è l'installazione.|  
|`FExclusive`|Flag booleano che indica che il progetto deve chiudere soluzioni aperte.|  
|`SolutionName`|Nome del file di soluzione senza la parte di directory o l'estensione. sln. Il nome del file con estensione suo viene anche creato utilizzando `SolutionName`. Se questo argomento non è una stringa vuota, verranno utilizzati <xref:EnvDTE._Solution.Create%2A>prima di aggiungere il progetto con <xref:EnvDTE._Solution.AddFromTemplate%2A>.</xref:EnvDTE._Solution.AddFromTemplate%2A> </xref:EnvDTE._Solution.Create%2A> Se questo nome è una stringa vuota, utilizzare <xref:EnvDTE._Solution.AddFromTemplate%2A>senza chiamare <xref:EnvDTE._Solution.Create%2A>.</xref:EnvDTE._Solution.Create%2A> </xref:EnvDTE._Solution.AddFromTemplate%2A>|  
|`Silent`|Valore booleano che indica se la procedura guidata deve essere eseguito automaticamente come se **fine** selezionate (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Parametri di contesto per aggiungono nuovo elemento  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`WizardType`|Creazione guidata tipo di registrazione (<xref:EnvDTE.Constants.vsWizardAddItem>) o il GUID che indica il tipo di procedura guidata.</xref:EnvDTE.Constants.vsWizardAddItem> Nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementazione, il GUID per la procedura guidata è {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Stringa che è univoco [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nome del progetto.|  
|`ProjectItems`|Percorso locale che contiene i file di progetto di lavoro.|  
|`ItemName`|Nome dell'elemento che deve essere aggiunto. Questo nome è il nome file predefinito o il nome del file che l'utente digita dal **Aggiungi elementi** la finestra di dialogo. Il nome è basato sul flag impostati nel file VSDIR. Il nome può essere un valore null.|  
|`InstallationDirectory`|Percorso della directory di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è l'installazione.|  
|`Silent`|Valore booleano che indica se la procedura guidata deve essere eseguito automaticamente come se **fine** selezionate (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Parametri di contesto per l'aggiunta del progetto Sub  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`WizardType`|Creazione guidata tipo di registrazione (<xref:EnvDTE.Constants.vsWizardAddSubProject>) o il GUID che indica il tipo di procedura guidata.</xref:EnvDTE.Constants.vsWizardAddSubProject> Nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementazione, il GUID per la procedura guidata è {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Stringa che è univoco [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nome del progetto.|  
|`ProjectItems`|Puntatore al `ProjectItems` raccolta su cui opera la procedura guidata. Questo puntatore viene passato alla procedura guidata in base alla selezione di gerarchia del progetto. Un utente seleziona in genere una cartella in cui inserire l'elemento e quindi chiama il progetto **Aggiungi elemento** la finestra di dialogo.|  
|`LocalDirectory`|Percorso locale dell'utilizzo di file di progetto.|  
|`ItemName`|Nome dell'elemento che deve essere aggiunto. Questo nome è il nome file predefinito o il nome del file che l'utente digita dal **Aggiungi elementi** la finestra di dialogo. Il nome è basato sul flag impostati nel file VSDIR. Il nome può essere un valore null.|  
|`InstallationDirectory`|Percorso della directory di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è l'installazione.|  
|`Silent`|Valore booleano che indica se la procedura guidata deve essere eseguito automaticamente come se **fine** selezionate (`TRUE`).|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [Procedura guidata (. File vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Parametri di contesto per l'avvio di procedure guidate](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
