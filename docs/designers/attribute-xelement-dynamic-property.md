---
title: "Attribute (propriet&#224; dinamica XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Attribute (propriet&#224; dinamica XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ottiene un indicizzatore utilizzato per recuperare l'istanza dell'attributo che corrisponde al nome espanso specificato.  
  
## Sintassi  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## Valore proprietà\/Valore restituito  
 Indicizzatore del tipo `XAttribute Item(String expandedName)`.Questo indicizzatore accetta il nome espanso dell'attributo specificato e restituisce l'oggetto <xref:System.Xml.Linq.XAttribute> corrispondente o `null` se non esiste nessun attributo con il nome specificato.  
  
## Note  
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XElement.Attribute%2A> della classe <xref:System.Xml.Linq.XElement?displayProperty=fullName>.  
  
## Vedere anche  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Value](../designers/value-xattribute-dynamic-property.md)