---
title: "Creazione di tipi di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipi di progetto, nuovo"
  - "progetti [Visual Studio SDK], nuovi tipi di progetto"
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Creazione di tipi di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile estendere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creando un nuovo tipo di progetto. Per creare un nuovo tipo di progetto, è necessario comprendere alcuni concetti e completare una serie di passaggi. Gli argomenti seguenti forniscono una panoramica di come creare tipi di progetto.  
  
## In questa sezione  
 [Decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md)  
 Viene illustrato l'elemento, la persistenza del file di progetto e le decisioni di progettazione meccanico impegno che è necessario eseguire prima di creare un nuovo tipo di progetto.  
  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Viene fornita una panoramica dei passaggi da seguire per creare un nuovo tipo di progetto che supporta attività di programmazione come la modifica del codice e la compilazione, creazione, debug e distribuzione di applicazioni nel progetto.  
  
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Vengono fornite informazioni su come fornire e utilizzare una factory del progetto per creare istanze di un nuovo progetto.  
  
 [Registrazione di un tipo di progetto](../../extensibility/internals/registering-a-project-type.md)  
 Vengono forniti esempi di codice di istruzioni dal Registro di sistema che forniscono dati e i percorsi predefiniti e una tabella che contengono voci dallo script del Registro di sistema per ogni istruzione.  
  
 [Persistenza del progetto](../../extensibility/internals/project-persistence.md)  
 Viene illustrato l'utilizzo di `IPersistFileFormat` in modo permanente i file e gli oggetti non basate su file di progetto.  
  
 [Utilizzo di MSBuild](../../extensibility/internals/using-msbuild.md)  
 Viene descritto come utilizzare il tipo di progetto di [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] per consentire agli utenti di compilare dal motore di compilazione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e nella riga di comando.  
  
## Sezioni correlate  
 [Supporto di strumenti di esplorazione di simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Viene illustrata l'architettura di strumenti per la visualizzazione, ad esempio di codice il **Visualizzatore oggetti** e **Visualizzazione classi** finestra. Descrive le interfacce e metodi utilizzati per implementare l'esplorazione degli oggetti in un VSPackage.  
  
 [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Viene descritto il significato di riprodurre i progetti per determinare quale editor viene utilizzato quando si apre un elemento di progetto e come risorse del progetto possono essere modificate.  
  
 [L'installazione di VS con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Viene illustrato come fornire la propria identità univoca il pacchetto Visual Studio e come eseguire il wrapping delle DLL VSPackage e altre informazioni in un pacchetto Windows Installer \(. File con estensione MSI\) per la distribuzione ai clienti.  
  
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Viene descritto come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerarchie viste e gli indirizzi.  
  
 [Package VS](../../extensibility/internals/vspackages.md)  
 Viene fornita una panoramica di un package VS, un oggetto COM installabile che estende il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente e viene illustrato come implementare il proprio VSPackage.  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Viene illustrato come utilizzare i progetti per modificare il codice, compilare e compilare il codice, eseguire e il debug del codice e vengono forniti collegamenti ad argomenti dettagliati su come creare tipi di progetto.