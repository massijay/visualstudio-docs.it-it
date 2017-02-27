---
title: "Priorit&#224; di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti [Visual Studio SDK], apertura elementi"
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Priorit&#224; di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un elemento di progetto in genere è un membro di un solo progetto nella soluzione.  Di conseguenza, l'ide consente di determinare quale progetto viene utilizzato aprirlo.  Tuttavia, se un elemento è un membro di più di un progetto, l'ide utilizza una combinazione di priorità per determinare il migliore progetto per aprirlo.  
  
 Nell'elenco seguente vengono illustrati la combinazione di priorità di progetto:  
  
-   L'ide chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> per ogni progetto nella soluzione determinare se il documento è un membro di tale progetto.  
  
-   Se il documento è un membro del progetto, il progetto risponde con una priorità del progetto assegna a seconda della relativa gestione del documento.  Ad esempio, un progetto di linguaggio conforme con un con priorità alta per i file di origine IDL ma risponde con una priorità più bassa per un tipo di file non riconosciuto non utilizzato come parte del processo di compilazione.  
  
-   I progetti che forniscono agli editor personalizzati e specifici del progetto o ai progettisti di un documento anche ricevono un con priorità alta.  
  
-   L'enumerazione di <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> fornisce valori di priorità del documento.  
  
-   Il progetto che specifica la priorità più elevata viene fornito il contesto per aprire il documento.  Se due progetti restituiscono valori di priorità uguali, il progetto viene preferito.  Se nessun progetto nella soluzione soddisfi che può aprire il documento, l'ide inserisce il documento nel progetto file esterni.  Per ulteriori informazioni, vedere [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md).  
  
## Vedere anche  
 [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md)   
 [Procedura: aprire gli editor di documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)