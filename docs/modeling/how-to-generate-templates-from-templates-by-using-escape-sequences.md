---
title: 'Procedura: generare modelli da modelli utilizzando sequenze di Escape | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: "35"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 421b8a8bde2bb383889bcb58915fa8a3acb027cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Procedura: generare modelli da modelli utilizzando sequenze di escape
È possibile creare un modello di testo che consente di creare un altro modello di testo come output testo generato. A tale scopo, è necessario utilizzare sequenze di escape per delineare i tag di modello di testo. Se non si utilizzano le sequenze di escape, il modello di testo generato avrà un significato predefinito. Per ulteriori informazioni sull'utilizzo di sequenze di escape nei modelli di testo, vedere [utilizzando le sequenze di Escape nei modelli di testo](../modeling/using-escape-sequences-in-text-templates.md).  
  
### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Per generare un modello di testo all'interno di un modello di testo  
  
-   Utilizzare la barra rovesciata (\\) come carattere di escape per produrre il tag di markup necessari all'interno del modello di testo per le direttive, istruzioni, espressioni e classe funzionalità in un file di modello di testo.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente Usa caratteri di escape per produrre un modello di testo da un modello di testo. Il `output` direttiva imposta il tipo di file di destinazione per il tipo di file di modello di testo (con estensione TT).  
  
```csharp  
\<#@ output extension=".tt" \#>  
\<#@ assembly name="System.Xml.dll" \#>  
\<#@ import namespace="System.Xml" \#>  
\<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {\#>  
           \<#= attr.Name \#>  
       \<#}  
     }  
\#>  
```  
  
 L'output di testo generato è un modello di testo.  
  
```  
<#@ output extension=".tt" #>  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {#>  
           <#= attr.Name #>  
       <#}  
     }  
#>  
```