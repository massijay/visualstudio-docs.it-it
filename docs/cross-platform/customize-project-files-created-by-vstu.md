---
title: "Personalizzare i file di progetto creati con VSTU | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "crdun"
manager: "crdun"
---
# Personalizzare i file di progetto creati con VSTU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio Tools per Unity offre un callback in stile Unity durante la generazione dei file di progetto.  Eseguire la registrazione con l'evento `VisualStudioIntegration.ProjectFileGeneration` per modificare il file di progetto ogni volta che viene rigenerato.  
  
## Dimostrazione  
 Viene illustrato come personalizzare i file di progetto di Visual Studio generati da Visual Studio Tools per Unity.  
  
## Esempio  
  
```c#  
using System;  
using System.IO;  
using System.Linq;  
using System.Text;  
using System.Xml.Linq;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class ProjectFileHook  
{  
    // necessary for XLinq to save the xml project file in utf8  
    class Utf8StringWriter : StringWriter  
    {  
        public override Encoding Encoding  
        {  
            get { return Encoding.UTF8; }  
        }  
    }  
  
    static ProjectFileHook()  
    {  
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>  
        {  
            // parse the document and make some changes  
            var document = XDocument.Parse(content);  
            document.Root.Add(new XComment("FIX ME"));  
  
            // save the changes using the Utf8StringWriter  
            var str = new Utf8StringWriter();  
            document.Save(str);  
  
            return str.ToString();  
        };  
    }  
}  
```  
  
## Vedere anche  
 [Esempio: callback di log](../cross-platform/share-the-unity-log-callback-with-vstu.md)