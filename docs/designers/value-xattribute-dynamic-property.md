---
title: "Valore (proprietà dinamica XAttribute) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c013001a52e5b894bcbcdaf9a40309505b39140c
ms.lasthandoff: 02/22/2017

---
# <a name="value-xattribute-dynamic-property"></a>Valore (proprietà dinamica XAttribute)
Ottiene o imposta il valore dell'attributo XML.  
  
## <a name="syntax"></a>Sintassi  
  
```  
attrib.Value   
```  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Oggetto <xref:System.String> contenente il valore dell'attributo.  
  
## <a name="exceptions"></a>Eccezioni  
  
|Tipo di eccezione|Condizione|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|Durante l'impostazione, `value` è `null`.|  
  
## <a name="remarks"></a>Note  
 Questa proprietà è equivalente alla proprietà <xref:System.Xml.Linq.XAttribute.Value%2A> della classe <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, ma supporta anche le notifiche di modifica.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Proprietà dinamiche della classe XAttribute](../designers/xattribute-class-dynamic-properties.md)   
 [Attributo](../designers/attribute-xelement-dynamic-property.md)
