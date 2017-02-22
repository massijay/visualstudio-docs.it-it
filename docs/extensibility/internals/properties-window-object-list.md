---
title: "Elenco di oggetti finestra delle propriet&#224; | Microsoft Docs"
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
  - "Finestra Proprietà, elenco di oggetti"
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Elenco di oggetti finestra delle propriet&#224;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'elenco di oggetti nella finestra di **Proprietà** è un elenco a discesa che consente di modificare la selezione ad altri oggetti disponibili in uno o più finestre selezionate.  Selecting a different object from within this list triggers a call to <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> to inform the environment that a new object has been selected.  Le informazioni visualizzate nella finestra di **Proprietà** quindi vengono modificate per visualizzare le proprietà associate all'oggetto appena selezionato.  
  
## L'elenco di oggetti  
 L'elenco di oggetti è costituito da due campi: il nome dell'oggetto viene visualizzato in grassetto\) e il tipo di oggetto.  
  
 Il nome dell'oggetto viene visualizzata a sinistra del tipo di oggetto in grassetto viene recuperato dall'oggetto stesso utilizzando la proprietà di `Name` fornita dall'interfaccia di <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> .  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, l'unico metodo su <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, restituisce <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> della coclasse dell'interfaccia.  La finestra di **Proprietà** utilizza <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> per ottenere il nome della coclasse, visualizzata come nome dell'oggetto nell'elenco a discesa.  
  
 Se l'oggetto non ha una proprietà di `Name` , un nome non viene visualizzato nell'area nome dell'elenco di oggetti.  È possibile aggiungere una proprietà name all'oggetto se si desidera che il nome visualizzato nell'elenco di oggetti.  
  
 Se l'oggetto COM non implementa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, la finestra di **Proprietà** visualizzare il nome dell'interfaccia anziché il nome dell'oggetto sul lato sinistro dell'elenco.  
  
## Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)