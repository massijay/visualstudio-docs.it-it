---
title: "Xml (proprietà dinamica XElement) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ed9aaee4e227627cf9ef5030863701445671444b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="xml-xelement-dynamic-property"></a>Xml (proprietà dinamica XElement)
Ottiene il contenuto XML non formattato dell'elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Oggetto <xref:System.String> che rappresenta il contenuto XML non formattato dell'elemento.  
  
## <a name="remarks"></a>Note  
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> della classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con il parametro `SaveOptions` impostato su <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valore](../designers/value-xelement-dynamic-property.md)