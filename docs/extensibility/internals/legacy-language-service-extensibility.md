---
title: "Estensibilit&#224; del servizio di linguaggio legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizi di linguaggio"
  - "Visual Studio, servizi di linguaggio"
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 42
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 42
---
# Estensibilit&#224; del servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servizio di linguaggio fornisce supporto specifico della lingua per la modifica del codice sorgente nell'IDE.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni sulla nuova modalità per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
 Questa sezione illustra la struttura e l'implementazione di un servizio di linguaggio legacy.  
  
## In questa sezione  
 [La migrazione di un servizio di linguaggio Legacy](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Viene illustrato come aggiornare un servizio di linguaggio da Visual Studio 2008 per la versione più recente.  
  
 [Funzionalità fondamentali del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-essentials.md)  
 Fornisce importanti informazioni su come sviluppare servizi linguistici per integrare un linguaggio di programmazione in Visual Studio.  
  
 [Lo sviluppo di un servizio di linguaggio](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Vengono forniti collegamenti ad argomenti che consentono di creare un servizio di linguaggio.  
  
 [In un servizio di linguaggio Legacy colorazione della sintassi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Fornisce informazioni sul supporto di evidenziazione della sintassi in un servizio di linguaggio.  
  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fornisce informazioni su come utilizzare il framework di pacchetto gestito \(MPF\) per implementare un servizio di linguaggio completo nel codice gestito.  
  
 [Supporto di strumenti di esplorazione di simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Descrive le librerie e strumenti che consentono di esplorare le visualizzazioni di struttura ad albero di simboli nell'IDE.  
  
## Sezioni correlate  
 [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md)  
 Viene fornita una panoramica dell'editor di Visual Studio.  
  
 [Supporto del servizio del linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)  
 Fornisce informazioni e un collegamento a Visual Studio Debugging SDK, che contiene le informazioni necessarie per creare e personalizzare i componenti del debugger per eseguire il debug di programmi.