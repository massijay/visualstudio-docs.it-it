---
title: "Descendants (propriet&#224; dinamica XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Descendants (propriet&#224; dinamica XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ottiene un indicizzatore utilizzato per recuperare tutti gli elementi discendente dell'elemento corrente che corrispondono al nome espanso specificato.  
  
## Sintassi  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## Valore proprietà\/Valore restituito  
 Indicizzatore del tipo `IEnumerable<XElement> Item(String expandedName)`.Questo indicizzatore accetta il nome espanso degli elementi discendente specificati e restituisce gli elementi figlio corrispondenti in una raccolta <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## Note  
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> della classe <xref:System.Xml.Linq.XContainer>.  
  
 Gli elementi della raccolta restituita sono in ordine del documento dell'origine XML.  
  
 Questa proprietà utilizza l'esecuzione posticipata.  
  
## Vedere anche  
 [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)