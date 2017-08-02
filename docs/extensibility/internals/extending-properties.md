---
title: "Estensione delle proprietà | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 18
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
ms.openlocfilehash: fec1140bc90d494a0c611ed84786f364f17f6087
ms.lasthandoff: 02/22/2017

---
# <a name="extending-properties"></a>Estensione delle proprietà
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **proprietà** è un visualizzatore proprietà universale per i componenti COM e COM+ e supporta tutti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prodotti. Il **proprietà** finestra funziona con `ITypeInfo` digitare le informazioni e i metadati COM+ per elencare le proprietà in fase di progettazione per l'oggetto attualmente selezionato in tutte le altre finestre nell'ambiente di sviluppo integrato (IDE).  
  
 Il **proprietà** finestra, che può essere aperto premendo F4 sulla tastiera o la selezione di **finestra proprietà** sul **visualizzazione** menu, viene utilizzato per visualizzare e modificare le proprietà indipendenti dalla configurazione, in fase di progettazione e gli eventi degli oggetti selezionati. Proprietà dipendenti dalla configurazione, associata a soluzioni e progetti, vengono visualizzate in [pagine delle proprietà](../../extensibility/internals/property-pages.md). Per ulteriori informazioni, vedere [le proprietà del progetto: NIB](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [opzioni di configurazione Gestione](../../extensibility/internals/managing-configuration-options.md), e [NIB: elemento gestione nei progetti](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Panoramica della finestra proprietà](~/docs/extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Finestra Proprietà  
  
 In questa sezione vengono fornite informazioni dettagliate che riguardano le singole aree di **proprietà** finestra e le interfacce che è necessario implementare e chiamare per popolare la finestra.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Panoramica della finestra proprietà](../../extensibility/internals/properties-window-overview.md)  
 Viene illustrato lo scopo di **proprietà** finestra rispetto alla finestra del documento e la finestra degli strumenti.  
  
 [I criteri dei modelli e la finestra proprietà](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Viene illustrato come un progetto è contenuto in un progetto di modello enterprise e come tale progetto di modello enterprise può imporre criteri.  
  
 [Interfacce e i campi di proprietà finestra](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Illustra la base per la selezione determina quali informazioni vengono visualizzate nel **proprietà** finestra.  
  
 [Elenco di oggetti finestra delle proprietà](../../extensibility/internals/properties-window-object-list.md)  
 Viene descritto lo scopo di **proprietà** elenco di oggetti finestra, che descrivono come, quando un oggetto diverso da questo elenco comporta una chiamata, l'ambiente viene informato che è stato selezionato un nuovo oggetto.  
  
 [Pulsanti della finestra proprietà](../../extensibility/internals/properties-window-buttons.md)  
 Viene illustrato lo scopo dei pulsanti quattro predefiniti visualizzati nel **proprietà** degli strumenti della finestra.  
  
 [Proprietà Visualizza griglia](../../extensibility/internals/properties-display-grid.md)  
 Viene illustrato in cui vengono trovati i nomi di proprietà e campi di valori di proprietà nella griglia.  
  
 [Specifica della traccia della selezione per la finestra Proprietà](../../misc/announcing-property-window-selection-tracking.md)  
 Viene descritto il rilevamento di selezione di **proprietà** finestra.  
  
 [Nascondere le proprietà con proprietà figlio](../../misc/hiding-properties-that-have-child-properties.md)  
 Viene illustrato come nascondere le proprietà che dispongono di proprietà figlio mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>  
  
 [Specifica di una finestra Proprietà personalizzate](../../misc/providing-a-custom-properties-window.md)  
 Vengono fornite istruzioni dettagliate per fornire il proprio visualizzatore proprietà.  
  
 [Descrizioni dei campi dalla finestra Proprietà](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Viene indicato dove trovare l'area di descrizione che visualizza le informazioni correlate al campo della proprietà selezionata.  
  
 [Aggiornamento dei valori della proprietà nella finestra Proprietà](../../misc/updating-property-values-in-the-properties-window.md)  
 Vengono fornite istruzioni dettagliate che illustrano due modi per mantenere la **proprietà** finestra sincronizzato con le modifiche di valore di proprietà.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono illustrati i progetti come i blocchi predefiniti del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Compiling and Building](../../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)  
 Viene descritto come utilizzare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] piattaforma per il test e debug di applicazioni durante la compilazione.  
  
 [Proprietà documento HTML, finestra proprietà](http://msdn.microsoft.com/Library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Vengono fornite istruzioni per la modifica di un documento HTML direttamente dalla finestra delle proprietà e viene fornita una tabella che riporta in dettaglio i campi in un documento HTML nella finestra Proprietà.  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Viene descritto il `IDispatch` interfaccia, prima è stato progettato per supportare l'automazione, fornendo un meccanismo di associazione tardiva per recuperare le informazioni sui metodi e proprietà di un oggetto.  
  
 [NIB: Introduzione a proprietà dinamiche (Visual Studio)](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 Fornisce una panoramica delle proprietà dinamiche che consentono di configurare l'applicazione in modo che i valori delle proprietà vengono archiviati in un file di configurazione esterno anziché il codice dell'applicazione compilata.  
  
 [NIB: progetti come contenitori](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 Viene descritto il ruolo del progetto come un contenitore in una soluzione di gestione, compilazione e debug gli elementi che costituiscono l'applicazione in modo logico.  
  
 [Proprietà NIB: progetto](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Viene descritto come il progetto gestisce le impostazioni che consentono di controllo proprietà che si applicano all'intero progetto e che sono limitate a determinate configurazioni di compilazione del progetto.  
  
 [Solutions and Projects](../../ide/solutions-and-projects-in-visual-studio.md) (Soluzioni e progetti)  
 Viene illustrato come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce in modo efficiente gli elementi quali i riferimenti, connessioni dati, cartelle e file necessari per l'attività di sviluppo tramite soluzioni e progetti.  
  
 [Estensione di altre parti di Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Viene illustrato come utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servizi per creare elementi dell'interfaccia utente che corrispondano al resto del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
