---
title: "Che contribuiscono al modello di automazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "automazione [Visual Studio SDK]"
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Che contribuiscono al modello di automazione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio fornisce un set di interfacce di automazione per la personalizzazione dell'ambiente. Il modello di automazione è il modello a oggetti che consente agli utenti di creare estensioni e componenti aggiuntivi di Visual Studio.  
  
 Inoltre, è appropriata, gli sviluppatori VSPackage contribuire al modello di automazione. In questo modo consente agli utenti finali del pacchetto Visual Studio per creare componenti aggiuntivi e in genere forniscono un'esperienza di modello utente coerente quando utilizzano il pacchetto Visual Studio in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Per rendere l'utente finale esperienza coerente, è possibile seguire una serie di linee guida quando si progetta il pacchetto Visual Studio in modo che il modello di automazione per il pacchetto Visual Studio segue le idee in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## In questa sezione  
 [Cenni preliminari sul modello di automazione](../../extensibility/internals/automation-model-overview.md)  
 Definisce il modello di automazione come un gruppi di oggetti che controllano i principali aspetti dell'ambiente comune correlati. Questo set di oggetti è raffigurato in un diagramma del modello di automazione.  
  
 [Fornisce l'automazione per i package VS](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Vengono illustrati i due modi per consentire l'automazione per il pacchetto Visual Studio.  
  
 [Esposizione di oggetti di progetto](../../extensibility/internals/exposing-project-objects.md)  
 Vengono fornite istruzioni dettagliate per la creazione di oggetti specifici di VSPackage.  
  
 [Modello di progetto](../../extensibility/internals/project-modeling.md)  
 Vengono illustrati gli oggetti di progetto standard necessari per creare un'automazione per il nuovo tipo di progetto e viene illustrato il percorso che segue automazione dei progetti. In questo argomento vengono anche forniti elenchi di dichiarazioni e implementazioni per le classi.  
  
 [Esposizione di eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Vengono fornite istruzioni dettagliate per la creazione di eventi per il modello di automazione.  
  
 [Supporto di automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md)  
 Viene descritto come restituire un oggetto di automazione per il supporto delle proprietà di un package VS personalizzato del **Opzioni** della finestra di dialogo di **strumento** menu estendendo il `DTE.Properties` oggetto.  
  
 [Fornisce l'automazione per il codice](../../extensibility/internals/providing-automation-for-code.md)  
 Viene illustrato che la creazione di un modello di automazione per il codice non è necessaria. Tuttavia, in questo argomento che fornisce informazioni accurate nei modelli di codice viene fornito un collegamento.  
  
 [Procedura: consentire l'automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Viene spiegato che fornisce l'automazione è una buona idea ogni volta che si desidera rendere disponibili gli oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione predefiniti. Viene illustrata l'automazione per le finestre e finestre di documento.  
  
 [Utilizzando il modello di automazione](../../extensibility/internals/using-the-automation-model.md)  
 Fornisce due esempi di codice che illustrano come un consumer di automazione Ottiene il progetto iniziale gli oggetti di automazione.  
  
 [Automazione per la configurazione e oggetti SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Vengono fornite informazioni sull'automazione per le opzioni di configurazione e l'automazione per gli elementi selezionati.  
  
## Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fornisce un esempio di codice che illustra come un VSPackage fa parte del modello oggetto di automazione DTE. Elenca i parametri, valori restituiti e selezionato la sezione Osservazioni.  
  
## Sezioni correlate