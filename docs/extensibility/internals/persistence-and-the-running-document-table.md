---
title: "Persistenza e la tabella del documento in esecuzione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistenza, la gestione"
  - "Interfaccia IVsPersistHierarchyItem, implementazione"
  - "architettura, persistenza"
  - "tabella di documento in esecuzione (RDT), architettura"
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Persistenza e la tabella del documento in esecuzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, i progetti sono completamente responsabili della gestione della persistenza di elementi di progetto, che portano a termine utilizzando il servizio, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. I documenti sono l'unità fondamentale di persistenza nell'ambiente di Visual Studio. Progetti di coordinano l'apertura, salvataggio e ridenominazione di documenti con la tabella in esecuzione documento \(RDT\), una risorsa che tiene traccia dello stato di tutti i documenti aperti.  
  
## La gestione di persistenza  
 Progetti consentono di controllare il servizio di persistenza dell'ambiente mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfaccia. Mentre l'ambiente richiesto mai direttamente un documento persistente, verrà chiesto il progetto proprietario \(o gerarchia\) per salvare il documento. Questo rende possibile per il progetto salvare i dati di elemento di progetto in file locali, i file remoti, un database, un repository o altro supporto.  
  
 Ambiente globale mantiene il RDT. L'ambiente mantiene le voci per tutte le finestre e documenti in RDT, il che rende possibile per poter ricevano notifiche speciali, ad esempio quando una soluzione è chiusa. Inoltre, il RDT rende possibile per l'ambiente rilevare i nodi corrispondenti nel **Esplora**. Il RDT gestisce un record per ogni oggetto aperto, persistente, inclusi i file di progetto e documenti di elemento di progetto.  
  
## Vedere anche  
 [Tabella Document in esecuzione](../../extensibility/internals/running-document-table.md)   
 [Selezione e la valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)