---
title: "Aggiunta di progetto e i modelli di progetto | Microsoft Docs"
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
  - "progetti [Visual Studio SDK], aggiunta"
  - "elementi di progetto [Visual Studio], aggiunta"
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Aggiunta di progetto e i modelli di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando si creano dei tipi di progetto, è necessario fornire il supporto per aggiungere nuovi progetti ed elementi di progetto utilizzando le finestre di dialogo standard dell'ambiente di \(IDE\) sviluppo integrato di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Negli argomenti seguenti vengono illustrate le tecniche differenti per l'aggiunta di progetti e di elementi di progetto.  
  
## In questa sezione  
 [Contesto del progetto](../../extensibility/internals/project-context.md)  
 Viene descritto che il progetto fornisce la maggior parte delle informazioni sul contesto per quanto trasparisce nell'ambiente.  
  
 [Priorità di progetto](../../extensibility/internals/project-priority.md)  
 Viene creato un elemento di progetto è in genere un membro di un progetto evitare l'ambiguità su cui il progetto viene utilizzato aprirlo.  
  
 [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md)  
 Vengono fornite informazioni sui due tipi di editor che possono essere utilizzati per aprire i file in un progetto e il ruolo del progetto viene riprodotto nella determinazione dell'editor da utilizzare quando un elemento di progetto viene aperto.  
  
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)  
 Viene spiegato cosa accade quando un progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene creato.  
  
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Viene illustrato il processo di aggiunta di elementi alla finestra di dialogo di **Aggiungi nuovo elemento** .  
  
 [Aggiunta di directory per la finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Viene fornito un esempio di registrare una nuova directory contenente i modelli personalizzati resi disponibili da un VSPackage.  
  
 [Aggiunta di directory per il dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Fornisce un esempio di registrazione di un nuovo set di directory per la finestra di dialogo di **Aggiungi nuovo elemento** .  
  
 [Comandi definiti dall'IDE per l'estensione di sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Vengono elencati i diversi tipi di elementi di comando utilizzati per l'estensione dei sistemi di progetto.  
  
 [CATID per gli oggetti che vengono in genere utilizzati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Elenca i CATID per gli oggetti utilizzati per estendere [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]e i sistemi di progetto di[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  
  
## Sezioni correlate  
 [Procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)  
 Vengono fornite istruzioni dettagliate per aprire un elemento intrinsecamente associati a un editor specifico per un progetto.  
  
 [Procedura: aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md)  
 Vengono fornite istruzioni dettagliate per aprire un editor standard.  
  
 [Progetto \(sottotipi\)](../../extensibility/internals/project-subtypes.md)  
 Vengono forniti collegamenti ad argomenti concettuali sottotipo di progetto.  I sottotipi di progetto estendono [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] esistente e i progetti[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti collegamenti ad argomenti supplementari che offrono informazioni su come progettare i nuovi tipi di progetto.