---
title: Le interfacce legacy nell&quot;Editor | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 10
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e6f4c118ac9306bc533ba7cf62037a8255e9c42f
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-interfaces-in-the-editor"></a>Interfacce legacy nell'Editor
Editor di Visual Studio è possibile accedere da interfacce legacy. Visual Studio SDK include schede di rete come *shim*, che consentono di interagire con il nuovo editor di queste interfacce. Tuttavia, è consigliabile aggiornare il codice per utilizzare il nuovo editor API legacy. Il codice offre prestazioni migliori ed è possibile utilizzare nuove tecnologie quali Windows Presentation Foundation (WPF) e Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Adattamento del codice Legacy nell'editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Viene illustrato come adattare il codice per il nuovo editor.|  
|[Comportamento nuovo o modificato con schede dell'Editor](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Viene illustrato come il comportamento delle schede di editor è diverso da quello delle versioni precedenti dell'editor.|  
|[Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)|Vengono descritti i diversi componenti di versioni precedenti dell'editor.|  
|[Creazione di Editor di componenti di base tramite l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|In questo articolo viene spiegato come utilizzare l'API legacy per creare un'istanza di editor principale.|  
|[Factory editor](../extensibility/editor-factories.md)|Viene illustrato come utilizzare factory editor con l'API legacy.|  
|[Procedura: registrare i tipi di File dell'Editor](../extensibility/how-to-register-editor-file-types.md)|Viene descritto come collegare un'estensione nome file dell'editor.|  
|[Procedura dettagliata: Creazione di un Editor di componenti di base e la registrazione di un tipo di File dell'Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Viene illustrato come creare un core editor e collegare un'estensione nome file.|  
|[Procedura: fornire il contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md)|Viene illustrato come fornire il contesto per l'editor.|  
|[Servizi per linguaggi e l'Editor di componenti di base](../extensibility/language-services-and-the-core-editor.md)|Vengono illustrate le interazioni tra un servizio di linguaggio e un editor.|  
|[Accesso ai Buffer di testo tramite l'API Legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Viene illustrato come accedere al buffer di testo tramite l'API legacy.|  
|[Accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Viene illustrato come accedere alla visualizzazione di testo tramite l'API legacy.|  
|[Personalizzazione di Windows di codice tramite l'API Legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Viene descritto come personalizzare finestre del codice tramite l'API legacy.|  
|[L'accesso ai livelli di testo tramite l'API Legacy](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Viene illustrato come accedere a diversi livelli di testo utilizzando l'API legacy.|  
|[Utilizzando gli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)|Viene illustrato come aggiungere indicatori di testo tramite l'API legacy.|  
|[Personalizzazione di menu e controlli di Editor utilizzando l'API Legacy](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Viene illustrato come personalizzare i controlli di editor tramite l'API legacy.|  
|[La gestione di annullamento e ripristino mediante l'API Legacy](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Viene illustrato come gestire l'annullamento e ripristino mediante l'API legacy.|  
|[Procedura: implementare Trova e Sostituisci meccanismo](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Viene illustrato come gestire Trova e Sostituisci tramite l'API legacy.|  
|[Procedura: eliminare le notifiche di modifica File](../extensibility/how-to-suppress-file-change-notifications.md)|Viene illustrato come eliminare le notifiche di modifica di file mediante l'API legacy.|  
|[Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Viene illustrato come creare finestre di progettazione ed editor personalizzati.|  
|[Sviluppo di un servizio di linguaggio Legacy](../extensibility/internals/developing-a-legacy-language-service.md)|Vengono forniti collegamenti a documenti sulle funzionalità che forniscono funzionalità di personalizzazione per la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale aggiungendo il supporto per un servizio di linguaggio.|  
|[Utilizzando i tipi di carattere e colori](../extensibility/using-fonts-and-colors.md)|Viene illustrato come utilizzare i tipi di carattere e colori con le interfacce legacy.|
