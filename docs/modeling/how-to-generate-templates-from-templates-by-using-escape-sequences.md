---
title: "How to: Generate Templates from Templates By Using Escape Sequences | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, generating templates from templates"
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 35
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 35
---
# How to: Generate Templates from Templates By Using Escape Sequences
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile creare un modello di testo che crea un altro modello di testo come proprio output di testo generato.  A questo scopo, è necessario utilizzare sequenze di escape per delineare i tag del modello di testo.  Se non si utilizzano sequenze di escape, il modello di testo generato avrà un significato predefinito.  Per ulteriori informazioni sull'utilizzo di sequenze di escape nei modelli di testo, vedere [Using Escape Sequences in Text Templates](../modeling/using-escape-sequences-in-text-templates.md).  
  
### Per generare un modello di testo dall'interno di un modello di testo  
  
-   Utilizzare la barra rovesciata \(\\\) come carattere di escape per produrre i tag di markup necessari all'interno del modello di testo per direttive, istruzioni, espressioni e funzionalità di classe in un file modello di testo separato.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## Esempio  
 Nell'esempio seguente vengono utilizzati dei caratteri di escape per produrre un modello di testo da un modello di testo.  La direttiva `output` imposta il tipo del file di destinazione sul tipo del file modello di testo \(.tt\).  
  
```c#  
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