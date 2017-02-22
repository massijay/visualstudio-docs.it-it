---
title: "Lo sviluppo di un servizio di linguaggio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.vsip.LangServWiz.langtoks"
  - "vs.vsip.LangServWiz.welcome"
  - "vs.vsip.LangServWiz.langSpec"
  - "vs.vsip.LangServWiz.langInfo"
  - "vs.vsip.LangServWiz.langServOpts"
helpviewer_keywords: 
  - "servizi di linguaggio, lo sviluppo"
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Lo sviluppo di un servizio di linguaggio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa sezione sono riportati i collegamenti ad argomenti che consentono di creare un servizio di linguaggio legacy.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni sulla nuova modalità per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## In questa sezione  
 [Modello di un servizio di linguaggio Legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Fornisce un modello di un servizio di linguaggio minimo per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor principale. È possibile utilizzare questo modello come guida per la creazione di un proprio servizio di linguaggio.  
  
 [Interfacce di servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Vengono illustrati gli oggetti necessari per implementare un servizio di linguaggio e fornisce un elenco di oggetti aggiuntivi che è possibile utilizzare per fornire l'evidenziazione della sintassi, i dati di metodo e altre funzionalità.  
  
 [Intercettazione di comandi del servizio di linguaggio Legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Viene descritto come inserire un filtro al servizio di linguaggio per intercetta comandi che consentono di gestire in altro modo la visualizzazione di testo.  
  
 [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Fornisce informazioni su come registrare il servizio di linguaggio tramite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Supporto del servizio del linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)  
 Viene descritto come un servizio di linguaggio può fornire funzionalità per supportare un debugger.  
  
 [Elenco di controllo: Creazione di un servizio di linguaggio Legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Vengono fornite istruzioni dettagliate per la creazione e l'integrazione di un servizio di linguaggio per l'editor di componenti di base.  
  
## Sezioni correlate  
 [In un servizio di linguaggio Legacy colorazione della sintassi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Viene illustrato come implementare l'evidenziazione della sintassi del servizio di linguaggio.  
  
 [Completamento delle istruzioni in un servizio di linguaggio Legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Viene illustrato il completamento, il processo mediante il quale un servizio di linguaggio consente agli utenti di completare una parola chiave del linguaggio o un elemento che siano avviati digitando.  
  
 [Informazioni sui parametri in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Viene descritto come fornire suggerimenti di metodo per metodi e funzioni in overload.  
  
 [Procedura: fornire supporto per il testo nascosto in un servizio di linguaggio Legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Viene illustrato lo scopo di un'area di testo nascosto e vengono fornite istruzioni su come implementare un'area di testo nascosto.  
  
 [Procedura: fornire il supporto esteso della struttura in un servizio di linguaggio Legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Vengono illustrate le due opzioni che estendono il supporto della struttura per il linguaggio oltre, supportando il *Comprimi alle definizioni* comando.