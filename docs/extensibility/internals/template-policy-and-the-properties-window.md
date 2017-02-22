---
title: "I criteri dei modelli e la finestra propriet&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Finestra Proprietà, i criteri dei modelli"
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# I criteri dei modelli e la finestra propriet&#224;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando un progetto è contenuto in un progetto di modello Enterprise, tale progetto di modello Enterprise possibile applicare i criteri di sicurezza.  I criteri del modello costituiscono un sistema vincolante che può essere utilizzato per impostare i valori predefiniti per le proprietà, nascondere le proprietà, aggiungere le proprietà, e così via.  
  
 Utilizzando criteri del modello controllare la visualizzazione di informazioni nella finestra di **Proprietà** è diversa dalla distribuzione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>.  l'handle di<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> oggetto le proprietà a livello componente, mentre i criteri del modello possono essere utilizzati per limitare le proprietà della soluzione o a livello di progetto.  in altre parole  
  
-   Implementare i metodi in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> per determinare le schermate visualizzate nella finestra di **Proprietà** per gli oggetti specifici  
  
-   Utilizzare i criteri del modello alla soluzione e di progetto per determinare le schermate visualizzate nella finestra di **Proprietà** per gli oggetti precedentemente specificati  
  
 Utilizzando criteri del modello vincolare in modo selettivo le proprietà specifiche nella finestra di **Proprietà** quando un elemento di progetto di un tipo specificato sia selezionato in **Esplora soluzioni** può essere utile a tutti i membri del team di sviluppo in esecuzione in un progetto.  Ad esempio, utilizzando criteri del modello, è possibile impostare tutte le informazioni della stringa di connessione in un database per gli sviluppatori e rendere la stringa di connessione di sola lettura.  In tal modo, è possibile fornire un modo semplice per assicurarsi che ogni sviluppatore utilizza il percorso corretto per l'accesso ai dati.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)