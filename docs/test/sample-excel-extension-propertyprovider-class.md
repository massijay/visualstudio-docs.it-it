---
title: "Estensione Excel di esempio: classe PropertyProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Estensione Excel di esempio: classe PropertyProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa classe interna estende la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> e fornisce servizi proprietà per elementi di [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] per registrare e riprodurre test dell'interfaccia utente.  
  
## Metodo GetControlSupportLevel  
 Tramite il metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> viene restituito un numero che indica il livello di supporto che può essere offerto dal provider di proprietà per il controllo fornito.  Quanto più elevato è il valore restituito, tanto più il provider di proprietà sarà in grado di supportare il controllo.  In questo casto, tramite il metodo viene controllato il valore della proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> del controllo fornito.  Se il valore è "Excel" e se la proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> indica che si tratta di un oggetto `CellElement`, verrà restituito il valore massimo dal metodo; in caso contrario, verrà restituito zero, ovvero non verrà fornito alcun supporto.  
  
## Metodo GetPropertyNames  
 Restituisce un dizionario di nomi di proprietà e descrittori di proprietà per le proprietà supportate di un controllo della cella di Excel.  
  
## Metodo GetPropertyDescriptor  
 Questo metodo viene chiamato dal framework di test per ottenere il descrittore di proprietà predefinito per il nome della proprietà fornito.  
  
## Metodi GetPropertyValue e SetPropertyValue  
 Il metodo `GetPropertyValue` consente di utilizzare la classe `Communicator` di questa estensione per restituire il valore della proprietà da Excel.  Il metodo `SetPropertyValue` consente di utilizzare la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> e il componente `Communicator` per impostare il valore della proprietà.  Questi metodi vengono chiamati dal framework di test.  
  
## Metodi di personalizzazione della generazione di codice  
 Questi metodi non sono implementati per questa estensione.  Pertanto, tramite questi ultimi viene restituito `null` o viene generata <xref:System.NotImplementedException>.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)