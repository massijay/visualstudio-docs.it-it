---
title: "Customizing T4 Text Transformation | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, API"
  - "text templates, custom hosts"
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 28
caps.handback.revision: 28
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Customizing T4 Text Transformation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I modelli di testo sono una funzionalità di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che consente di generare codice programma o altri file di testo tramite un processo di trasformazione.  Tramite l'utilizzo di [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], è possibile estendere il processo di trasformazione del modello predefinito personalizzando il processore di direttiva del modello di testo o l'host del modello di testo.  
  
## In questa sezione  
 [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md)  
 Viene descritto il funzionamento della trasformazione di testo e viene spiegato il ruolo dell'host del modello e dei processori di direttiva.  
  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Il processore di direttiva consente di gestire le direttive nel modello, ad esempio `<#@template#>.`. Viene eseguito durante la compilazione del modello e consente di caricare assembly e altre risorse.  Può inoltre inserire del codice che consentirà il caricamento di risorse in fase di runtime.  La definizione del processore di direttiva permette di ridurre la complessità dei modelli.  
  
 [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Se si scrive un'estensione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], quale un comando di menu o un gestore eventi, l'estensione può utilizzare Text Templating Service per trasformare qualsiasi modello di testo.  È possibile passare i dati dei parametri nel modello tramite l'oggetto Session e ottenere i valori dal modello tramite la direttiva `<#@parameter#>`.  
  
 [Processing Text Templates by using a Custom Host](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Quando il codice del modello di testo viene eseguito, l'host fornisce l'accesso a file esterni e allo stato dell'applicazione.  Ad esempio, l'host nel quale vengono fornite le trasformazioni di testo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] può fornire l'accesso a Esplora soluzioni.  Inoltre, visualizza gli errori nella finestra di messaggio di errore.  Se si desidera eseguire delle trasformazioni di testo in un contesto diverso, è possibile definire un proprio host che fornisca l'accesso ai servizi disponibili in quel contesto.  
  
 Se si scrive un'estensione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], anziché scrivere un proprio host, considerare l'utilizzo del servizio di trasformazione del testo.  Per ulteriori informazioni, vedere [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## Riferimenti  
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)  
  
 Fornisce la sintassi di direttive e blocchi di controllo del modello di testo.