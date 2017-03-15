---
title: "Incorporamento semplificato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visualizzazione semplice personalizzati [Visual Studio SDK], Editor - incorporamento"
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Incorporamento semplificato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Incorporare semplificato viene abilitato in un editor quando il relativo oggetto visualizzazione del documento \(ovvero viene prodotto a un elemento figlio di\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]associati e l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> viene distribuita per mantenere i controlli finestra.  Semplificato incorporare gli editor non è possibile ospitare i controlli attivi.  Gli oggetti utilizzati per creare un editor con incorporare semplificato sono indicati di seguito.  
  
 ![Rappresentazione grafica dell'editor di incorporamento semplificato](../extensibility/media/vssimplifiedembeddingeditor.png "vsSimplifiedEmbeddingEditor")  
editor con incorporare semplificato  
  
> [!NOTE]
>  Gli oggetti in questa illustrazione, solo l'oggetto di `CYourEditorFactory` è necessario creare un editor basato su file standard.  Se si crea un editor personalizzato, non è necessario implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, poiché l'editor probabilmente sarà proprio meccanismo privato di persistenza.  Per gli editor di non personalizzato, tuttavia, è necessario farlo.  
  
 Tutte le interfacce implementate per creare un editor con incorporare semplificato sono contenute nell'oggetto di `CYourEditorDocument` .  Tuttavia, per supportare più visualizzazioni dei dati del documento, suddividere le interfacce sui dati e sugli oggetti visualizzati come indicato nella tabella seguente.  
  
|Interfaccia|Posizione dell'interfaccia|Utilizzare|  
|-----------------|--------------------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Visualizzazione|Fornisce la connessione alla finestra padre.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Visualizzazione|Per gestire i controlli.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Visualizzazione|Abilita gli aggiornamenti della barra di stato.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Visualizzazione|Consente di incorporare gli elementi di **Casella degli strumenti** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dati|Inviare notifiche quando il file viene modificato.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dati|Abilita il funzionalità per un tipo di file.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dati|Abilita la persistenza del documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dati|Consente l'eliminazione degli eventi per le modifiche ai file, ad esempio l'attivazione di ricaricamento.|