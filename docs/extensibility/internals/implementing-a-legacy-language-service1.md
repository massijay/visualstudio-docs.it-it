---
title: "Implementazione di un servizio di linguaggio Legacy | Microsoft Docs"
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
  - "servizi di linguaggio, gestiti"
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementazione di un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile utilizzare le classi di framework pacchetto gestito \(MPF\) per implementare un servizio di linguaggio legacy che supporta un'ampia gamma di funzionalità, quali l'evidenziazione della sintassi, corrispondenza parentesi graffe e completamento IntelliSense.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni sulla nuova modalità per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## In questa sezione  
 [Cenni preliminari sul servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)  
 Panoramica delle funzionalità del servizio del linguaggio che sono supportati in MPF.  
  
 [Implementazione di un servizio di linguaggio](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Viene descritto ciò che è necessario implementare un servizio di linguaggio tramite MPF.  
  
 [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Vengono descritti i passaggi necessari per registrare un servizio di linguaggio basato su MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Scanner e Parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Descrive i due parser necessari per implementare tutte le funzionalità di un servizio di linguaggio tramite il MPF.  
  
 [Procedura dettagliata: Creazione di un servizio di linguaggio Legacy](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Fornisce i passaggi di base necessari per implementare un servizio di linguaggio MPF in un VSPackage.  
  
 [Procedura dettagliata: Ottenere un elenco di frammenti di codice installato \(implementazione Legacy\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Vengono illustrate le tecniche di recupero di un elenco di frammenti di codice installati.  
  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)  
 Vengono forniti collegamenti ad argomenti che illustrano in dettaglio le operazioni necessarie per implementare tutte le funzionalità di un servizio di linguaggio tramite MPF.