---
title: Fornisce supporto per le finestre di progettazione per l&quot;annullamento | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 17
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
ms.openlocfilehash: 95e6873d0a3b254fa8f34144253a44c0a8cab60d
ms.lasthandoff: 02/22/2017

---
# <a name="supplying-undo-support-to-designers"></a>Fornisce il supporto di annullamento a finestre di progettazione
Finestre di progettazione, come editor di immagini, in genere necessario supportare le operazioni di annullamento in modo che gli utenti possono invertire le modifiche recenti quando si modifica un elemento di codice.  
  
 La maggior parte delle finestre di progettazione implementate in Visual Studio hanno il supporto di annullamento fornito automaticamente dall'ambiente.  
  
 Implementazioni della finestra di progettazione che forniscono il supporto per la funzionalità di annullamento è necessario:  
  
-   Gestione dell'annullamento implementando la classe base astratta<xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>  
  
-   Supportare la persistenza forniture e CodeDOM implementando il <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>e <xref:System.ComponentModel.Design.IComponentChangeService>classi.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Per ulteriori informazioni sulla scrittura di finestre di progettazione utilizzando [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], vedere [estensione supporto Design-Time](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce un'infrastruttura di annullamento predefinito per:  
  
-   Fornendo annullare le implementazioni di gestione tramite il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>e <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>classi.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Fornisce la persistenza e il supporto CodeDOM tramite il valore predefinito <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>e <xref:System.ComponentModel.Design.IComponentChangeService>implementazioni.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
## <a name="obtaining-undo-support-automatically"></a>Supporto dell'annullamento automaticamente  
 Qualsiasi finestra di progettazione creato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con supporto per l'annullamento automatico e completo se la finestra di progettazione:  
  
-   Si avvale di un <xref:System.Windows.Forms.Control>classe per l'interfaccia utente basata su.</xref:System.Windows.Forms.Control>  
  
-   Utilizza la generazione di codice standard basato su CodeDOM e sistema di analisi per la persistenza e la generazione di codice.  
  
     Per ulteriori informazioni sull'utilizzo di supporto di Visual Studio CodeDOM, vedere [dinamica la generazione del codice sorgente e compilazione](http://msdn.microsoft.com/Library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quando utilizzare il supporto di annullamento della finestra di progettazione esplicita  
 Finestre di progettazione è necessario fornire i propri management Annulla se utilizzano un'interfaccia utente grafica, definita come un adattatore di visualizzazione, diverso da quello fornito da <xref:System.Windows.Forms.Control>.</xref:System.Windows.Forms.Control>  
  
 Un esempio potrebbe essere creazione di un prodotto con un'interfaccia di progettazione grafica basata su web piuttosto che un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] basato su interfaccia grafica.  
  
 In questi casi, uno necessario registrare l'adapter di visualizzazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizzando <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>e fornire la gestione esplicita undo.</xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>  
  
 Finestre di progettazione devono fornire il supporto CodeDOM e persistenza se non vengono utilizzati il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modello di generazione del codice fornito nel <xref:System.CodeDom>spazio dei nomi.</xref:System.CodeDom>  
  
## <a name="undo-support-features-of-the-designer"></a>Annullare le funzionalità di supporto della finestra di progettazione  
 il SDK di ambiente fornisce le implementazioni predefinite di interfacce necessarie per fornire supporto che può essere utilizzato dai progettisti non si utilizza per l'annullamento <xref:System.Windows.Forms.Control>basato su classi per le proprie interfacce utente o il modello standard di persistenza e CodeDOM.</xref:System.Windows.Forms.Control>  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>classe deriva dal [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine>classe utilizzando un'implementazione della <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>classe per gestire operazioni di annullamento.</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> </xref:System.ComponentModel.Design.UndoEngine> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
 Visual Studio fornisce la funzionalità di rollback della finestra di progettazione seguente:  
  
-   Funzionalità di annullamento collegato tra più finestre di progettazione.  
  
-   Unità figlio all'interno di una finestra di progettazione può interagire con i relativi elementi padre mediante l'implementazione <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>  
  
 il SDK di ambiente fornisce supporto CodeDOM e persistenza fornendo:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>come un implementazioni del<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
 Oggetto <xref:System.ComponentModel.Design.IComponentChangeService>fornito dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' host di progettazione.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Tramite la funzionalità dell'ambiente di SDK per fornire il supporto di annullamento  
 Per ottenere il supporto di annullamento, è necessario un oggetto che implementa una finestra di progettazione:  
  
-   Creare un'istanza e inizializzare un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>classe con un oggetto valido <xref:System.IServiceProvider>implementazione.</xref:System.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Questo <xref:System.IServiceProvider>classe deve fornire i seguenti servizi:</xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.</xref:System.ComponentModel.Design.IDesignerHost>  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Finestre di progettazione utilizzando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la serializzazione CodeDOM può scegliere di utilizzare <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>fornito con il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] come implementazione di <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
         In questo caso, la <xref:System.IServiceProvider>classe fornita per il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>costruttore deve restituire l'oggetto come un'implementazione della <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>classe.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> </xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Finestre di progettazione utilizzando il valore predefinito <xref:System.ComponentModel.Design.DesignSurface>fornito dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] host di progettazione sono necessariamente un'implementazione predefinita della <xref:System.ComponentModel.Design.IComponentChangeService>classe</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.DesignSurface>  
  
 Finestre di progettazione che implementa un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>meccanismo di annullamento in base rileva automaticamente le modifiche se:</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Le modifiche alle proprietà vengono effettuate tramite il <xref:System.ComponentModel.TypeDescriptor>oggetto.</xref:System.ComponentModel.TypeDescriptor>  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>gli eventi vengono generati manualmente quando un modifiche annullabili viene eseguito il commit.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
-   Modifica della finestra di progettazione è stata creata all'interno del contesto di un <xref:System.ComponentModel.Design.DesignerTransaction>.</xref:System.ComponentModel.Design.DesignerTransaction>  
  
-   La finestra di progettazione sceglie di creare in modo esplicito le unità di annullamento tramite l'unità di annullamento standard fornito da un'implementazione di <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>Visual Studio specifica implementazione <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>che deriva da <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>e fornisce inoltre un'implementazione di entrambi <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit>  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Estensione del supporto in fase di progettazione](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
