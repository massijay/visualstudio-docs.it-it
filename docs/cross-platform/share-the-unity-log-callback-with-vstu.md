---
title: "Condividere il callback di log di Unity con VSTU | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 2
---
# Condividere il callback di log di Unity con VSTU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio Tools per Unity registra un callback di log con Unity in modo da poter eseguire la console di Unity in Visual Studio.  Se anche gli script di editor registrano un callback di log con Unity, il callback di VSTU potrebbe interferire con questo.  Per evitare questa eventualità, usare l'evento `VisualStudioIntegration.LogCallback` per cooperare con VSTU.  
  
## Dimostrazione  
 Viene illustrato come condividere il callback di log Unity creato da Visual Studio Tools per Unity.  
  
## Esempio  
  
```c#  
using System;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class LogCallbackHook  
{  
    static LogCallbackHook()  
    {  
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>  
        {  
            // place code that implements your log callback here  
        };  
    }  
}  
```  
  
## Vedere anche  
 [Esempio: generazione di file di progetto](../cross-platform/customize-project-files-created-by-vstu.md)