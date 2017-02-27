---
title: "Element (propriet&#224; dinamica XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Element"
apitype: "Assembly"
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Element (propriet&#224; dinamica XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ottiene un indicizzatore utilizzato per recuperare l'istanza dell'elemento figlio che corrisponde al nome espanso specificato.  
  
## Sintassi  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## Valore proprietà\/Valore restituito  
 Indicizzatore del tipo `XElement Item(String expandedName)`.Questo indicizzatore accetta un parametro del nome espanso e restituisce l'oggetto <xref:System.Xml.Linq.XElement> corrispondente o `null` se non esiste nessun elemento con il nome specificato.  
  
## Note  
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XContainer.Element%2A> della classe <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.  
  
## Vedere anche  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)