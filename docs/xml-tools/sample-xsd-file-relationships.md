---
title: 'File XSD di esempio: Relazioni | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60126510-b7dd-4cb4-92d3-9883590b92f2
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5f747a6fd05d19d56ce94f368cb89a18ff83a8b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="sample-xsd-file-relationships"></a>File XSD di esempio: relazioni
Il file XSD seguente viene usato in vari esempi nella documentazione relativa alla progettazione di schemi XSD. Questo file è uno schema di ordine di acquisto con annotazioni e documentazione.  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <xs:element name="pet" type="PetType"/>  
  
  <xs:attributeGroup name="NameAgeAttributes">  
    <xs:attribute name="age" type="xs:integer" use="required"/>  
    <xs:attribute name="name" type="xs:string" use="required"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="PetType">  
    <xs:attributeGroup ref="NameAgeAttributes"/>  
  </xs:complexType>  
  
  <xs:element name="cat" substitutionGroup="pet">  
    <xs:complexType>  
      <xs:complexContent>  
        <xs:extension base="PetType">  
          <xs:sequence>  
            <xs:element name="weight" type="xs:integer"/>  
            <xs:element name="color" type="xs:string"/>  
            <xs:element name="breed" type="xs:integer"/>  
          </xs:sequence>  
        </xs:extension>  
      </xs:complexContent>  
    </xs:complexType>  
  </xs:element>  
  
  <xs:element name="dog" substitutionGroup="pet">  
    <xs:complexType>  
      <xs:complexContent>  
        <xs:extension base="PetType">  
          <xs:sequence>  
            <xs:element name="weight" type="xs:integer"/>  
            <xs:element name="color" type="xs:string"/>  
            <xs:element name="breed" type="xs:integer"/>  
          </xs:sequence>  
        </xs:extension>  
      </xs:complexContent>  
    </xs:complexType>  
  </xs:element>  
  
</xs:schema>  
```