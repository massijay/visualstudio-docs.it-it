---
title: "Estensione Excel di esempio: classi Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Estensione Excel di esempio: classi Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'estensione utilizza classi derivate da <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> e rappresenta i controlli di cella e di foglio di lavoro in [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
 L'elemento base per questa estensione è `ExcelElement`.  La classe `ExcelWorksheetElement` e la classe `ExcelCellElement` ereditano entrambe da tale elemento.  
  
## Classi Element ed ElementInformation  
 La classe `Element` è la classe base per tutti gli elementi dell'interfaccia utente per l'estensione di Excel ed eredita dalla classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>.  In questo esempio, `ElementInformation` è la classe base per le classi delle informazioni sugli elementi e non dispone di membri.  
  
#### Proprietà e metodi semplici  
 Questi membri restituiscono valori semplici, ad esempio il valore della proprietà `Name` o il valore della proprietà `ClassName` e il codice risulta semplice e di facile lettura.  Alcuni valori vengono restituiti tramite la classe `Utility`, illustrata più avanti.  Altri restituiscono `null` poiché non sono attinenti in questa estensione di esempio.  Due membri sono più interessanti degli altri: la proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> e il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>.  
  
#### Proprietà QueryId  
 Questa proprietà restituisce una condizione formata da coppie nome\/valore della proprietà che identificano in modo univoco il controllo durante la riproduzione.  Per ogni classe del controllo derivata, lo sviluppatore deve eseguire l'override di questa proprietà per restituire un oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> che il framework possa utilizzare per trovare il controllo nell'Interfaccia utente.  
  
#### Metodo CacheProperties  
 Questo metodo viene chiamato dal framework di test durante il processo di registrazione per fare in modo che l'elemento salvi uno snapshot delle proprietà importanti.  Ciò consente di mantenere le proprietà disponibili anche quando il controllo effettivo dell'interfaccia utente non è più sullo schermo.  
  
## Classi WorksheetElement e WorksheetInformation  
 La classe `WorksheetElement` rappresenta un foglio di lavoro di Excel nel framework di test ed eredita dalla classe base `Element`.  Viene eseguito l'override di tre proprietà per fornire informazioni specifiche sull'oggetto foglio di lavoro di Excel: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A>e <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 L'oggetto <xref:System.Runtime.InteropServices.ComVisibleAttribute> viene applicato anche a questa classe per renderlo visibile a COM.  
  
 La classe `WorksheetInformation` rappresenta le informazioni su un foglio di lavoro di Excel.  Dispone di solo un membro, la proprietà `SheetName` che è sufficiente ai fini di questo esempio.  
  
## Classi CellElement e CellInformation  
 La classe `CellElement` rappresenta una cella di Excel ed eredita dalla classe base `Element`.  L'unico membro ignorato è la proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> che restituisce un oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> che utilizza le proprietà `RowIndex` e `ColumnIndex` per identificare la cella.  
  
## Classi Utilities e ExcelUtilities  
 La classe `ExcelUtilities` interna fornisce alcuni valori costanti, quali il nome di tecnologia e un metodo che determina se l'handle della finestra fornito rappresenta un foglio di lavoro di Excel.  
  
 La classe `Utilities` dispone di metodi di supporto che restituiscono una varietà di informazioni sull'interfaccia utente.  Alcuni metodi utilizzano chiamate dirette in DLL di sistema esterne, quali **USER32.DLL** e **OLEACC.DLL**, per ottenere handle della finestra dall'interfaccia utente**.**  
  
## Vedere anche  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)