---
title: "Lingue indipendente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - contenuti lingue"
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Lingue indipendente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Le lingue disponibili* sono linguaggi contenuti in altri linguaggi.  Ad esempio, HTML nelle pagine di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] può contenere [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o script di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] .  L'architettura di doppio\-linguaggio è obbligatoria per l'editor di file aspx fornire IntelliSense, la colorazione e altre funzionalità di modifica per sia HTML che il linguaggio di script.  
  
## Implementazione  
 L'interfaccia che più importante è necessario implementare per i linguaggi contenuti rappresenta l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  Questa interfaccia viene implementata da qualsiasi linguaggio che può essere ospitato in un linguaggio primario.  Fornisce l'accesso a colorizer del servizio di linguaggio, al filtro di visualizzazione di testo e all'identificazione del servizio di linguaggio primaria  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> consente di creare un'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  Nei passaggi seguenti viene illustrato come implementare un linguaggio contenuto:  
  
1.  Utilizzare `QueryService()` per ottenere il servizio di linguaggio ID e l'ID dell'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> per creare un'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  passare un'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , un ID elemento \(uno o più di <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>, di <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>, o di <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>\) e un'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> .  
  
3.  L'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> , che rappresenta l'oggetto del responsabile del buffer di testo, fornisce servizi di base che sono obbligatori eseguire il mapping delle posizioni in un file principale nel buffer secondario del linguaggio.  
  
     Ad esempio, in un unico file aspx, il file principale include pagine ASP, HTML e il codice in cui è contenuto.  Tuttavia, il buffer secondario, include solo il codice contenuto, insieme a tutte le definizioni della classe, per convertire il buffer secondario un file di codice valido.  Il responsabile del buffer gestisce il lavoro di coordinare le modifiche da un buffer all'altro.  
  
4.  Il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> , ovvero la lingua primario, indica al responsabile del buffer di testo all'interno del relativo buffer è mappato al testo corrispondente nel buffer secondario.  
  
     Il linguaggio passa una matrice della struttura di <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> , che attualmente includono solo un'ampiezza principale e secondaria.  
  
5.  Il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> e il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> forniscono il mapping da principale del buffer secondario e viceversa.