---
title: "Xml (propriet&#224; dinamica XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Xml"
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Xml (propriet&#224; dinamica XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ottiene il contenuto XML non formattato dell'elemento.  
  
## Sintassi  
  
```  
elem.Xml  
```  
  
## Valore proprietà\/Valore restituito  
 Oggetto <xref:System.String> che rappresenta il contenuto XML non formattato dell'elemento.  
  
## Note  
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> della classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con il parametro `SaveOptions` impostato su <xref:System.Xml.Linq.SaveOptions>.  
  
## Vedere anche  
 [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Value](../designers/value-xelement-dynamic-property.md)