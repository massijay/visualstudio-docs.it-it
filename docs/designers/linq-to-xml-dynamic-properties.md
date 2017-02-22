---
title: "Propriet&#224; dinamiche di LINQ to XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Propriet&#224; dinamiche di LINQ to XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa sezione vengono fornite informazioni di riferimento relative alle proprietà dinamiche di LINQ to XML.In particolare, queste proprietà vengono esposte dalle classi <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>, incluse nello spazio dei nomi <xref:System.Xml.Linq>.  
  
 Come illustrato nell'argomento [Cenni preliminari sull'associazione dati di WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), ogni proprietà dinamica è equivalente a una proprietà o a un metodo pubblico della stessa classe.Questi membri standard devono essere utilizzati per la maggior parte degli scopi. Le proprietà dinamiche vengono fornite specificamente per gli scenari di associazione dati LINQ to XML.Per ulteriori informazioni sui membri standard di queste classi, vedere gli argomenti di riferimento <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>.  
  
 Relativamente ai valori risolti, le proprietà dinamiche descritte in questa sezione rientrano in due categorie:  
  
-   Proprietà semplici, ad esempio le proprietà `Value` nelle classi <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>, che vengono risolte in un singolo valore.  
  
-   Valori indicizzati, ad esempio le proprietà [Elements](../designers/elements-xelement-dynamic-property.md) e [Descendants](../designers/descendants-xelement-dynamic-property.md) di <xref:System.Xml.Linq.XElement>, che vengono risolti in un tipo di indicizzatore.Affinché i tipi di indicizzatori vengano risolti nel valore o nella raccolta desiderata, è necessario passare un parametro di nome espanso.  
  
 Tutte le proprietà dinamiche che restituiscono un valore indicizzato di tipo <xref:System.Collections.Generic.IEnumerable%601> utilizzano l'esecuzione posticipata.Per ulteriori informazioni sull'esecuzione posticipata, vedere [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## In questa sezione  
  
|Argomento|Descrizione|  
|---------------|-----------------|  
|[Proprietà dinamiche della classe XAttribute](../designers/xattribute-class-dynamic-properties.md)|Vengono forniti dettagli sulle proprietà dinamiche esposte dalla classe <xref:System.Xml.Linq.XAttribute>.|  
|[Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)|Vengono forniti dettagli sulle proprietà dinamiche esposte dalla classe <xref:System.Xml.Linq.XElement>.|  
  
## Riferimento  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## Vedere anche  
 [Associazione dati WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Cenni preliminari sull'associazione dati WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)