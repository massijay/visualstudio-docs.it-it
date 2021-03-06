---
title: "Non &#232; possibile selezionare elementi discendenti XML dal tipo &#39;type&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36809"
  - "bc36809"
helpviewer_keywords: 
  - "BC36809"
ms.assetid: 560a3370-f24d-4ca3-93b1-39aabe13c238
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Non &#232; possibile selezionare elementi discendenti XML dal tipo &#39;type&#39;
È stato fatto riferimento a un elemento discendente XML per un oggetto che non è di tipo <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> o `IEnumerable(Of XElement)`. Per altre informazioni, vedere [XML Descendant Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text"...<childElement>  
```  
  
 **ID errore:** BC36809  
  
### Per correggere l'errore  
  
-   Se si fa riferimento a un elemento discendente di un oggetto, quest'ultimo deve essere fortemente tipizzato come <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> o `IEnumerable(Of XElement)`. Di seguito è riportato un esempio:  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem...<child>  
    ```  
  
## Vedere anche  
 [XML Descendant Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)