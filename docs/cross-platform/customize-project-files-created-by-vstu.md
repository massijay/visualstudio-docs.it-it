---
title: Personalizzare i file di progetto creati con VSTU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: "2"
author: conceptdev
ms.author: crdun
manager: crdun
ms.openlocfilehash: 2fb9315caccd7a6e761b8c82df6f6c3bc874c004
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/29/2017
---
# <a name="customize-project-files-created-by-vstu"></a>Personalizzare i file di progetto creati con VSTU
Visual Studio Tools per Unity offre un callback in stile Unity durante la generazione dei file di progetto. Eseguire la registrazione con l'evento `VisualStudioIntegration.ProjectFileGeneration` per modificare il file di progetto ogni volta che viene rigenerato.  

## <a name="demonstrates"></a>Dimostrazione  
 Viene illustrato come personalizzare i file di progetto di Visual Studio generati da Visual Studio Tools per Unity.  

## <a name="example"></a>Esempio  

```csharp  
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

## <a name="see-also"></a>Vedere anche  
 [Esempio: callback di log](../cross-platform/share-the-unity-log-callback-with-vstu.md)
