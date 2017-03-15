---
title: "Progetto (sottotipi) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti [Visual Studio SDK], sottotipi"
  - "sottotipi di progetto [Visual Studio SDK]"
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Progetto (sottotipi)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sottotipi di progetto consentono di personalizzare o flavor il comportamento dei sistemi di progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Le personalizzazioni includono il salvataggio di dati aggiuntivi nel file di progetto, aggiungendo o filtrando gli elementi di **Aggiungi nuovo elemento** nella finestra di dialogo controllo dell'assembly come eseguire il debug e distribuito e l'estensione del progetto **pagine delle proprietà** la finestra di dialogo. Package VS implementare sottotipi di progetto mediante aggregazione COM.  
  
> [!NOTE]
>  Il sistema di progetto Visual C\+\+ non supporta i sottotipi di progetto.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sottotipi di progetto stesso utilizzato per implementare progetti Smart Device e SQL Server.  
  
## In questa sezione  
 [Sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)  
 Viene descritto il concetto di sottotipi di progetto.  
  
 [Sequenza di inizializzazione dei sottotipi di progetto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Viene descritta la sequenza di inizializzazione sottotipo di progetto a livello di codice da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.  
  
 [Proprietà e metodi estesi dai sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Vengono fornite descrizioni dettagliate delle funzionalità e metodi estesi più di frequente usando sottotipi di progetto.  
  
 [Rendere persistenti i dati nel File di progetto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Viene descritto come rendere persistenti i dati in un file di progetto e come utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> per gestire i dati nel file di progetto tra i livelli di aggregazione sottotipo di progetto.  
  
 [Interfaccia utente di proprietà del progetto](../../extensibility/internals/project-property-user-interface.md)  
 Descrive come sottotipi di progetto possono modificare il progetto **pagine delle proprietà** la finestra di dialogo.  
  
 [Estendere il modello a oggetti del progetto di Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Fornisce informazioni su come sottotipi di progetto possono utilizzare le estensioni di automazione per estendere il modello oggetto di automazione.  
  
 [Che contribuiscono a di dialogo Aggiungi nuovo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Viene descritto come aggiungere elementi per il **Aggiungi nuovo elemento** la finestra di dialogo.  
  
 [Salvataggio di dati nei file di progetto](../../extensibility/saving-data-in-project-files.md)  
 Viene illustrato un sottotipo di progetto può salvare e recuperare i dati specifici del sottotipo nel file di progetto utilizzando il Framework di pacchetto gestito \(MPF\).  
  
 [Gestione specializzato distribuzione](../../extensibility/internals/handling-specialized-deployment.md)  
 Viene spiegato come sottotipi di progetto possono fornire il comportamento della distribuzione specializzato mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaccia.  
  
 [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)  
 Viene aggiunta e rimozione di pagine delle proprietà in Progettazione progetti.  
  
## Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti collegamenti ad argomenti che descrivono dettagliatamente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti.