---
title: "Direttiva T4 CleanUpBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Direttiva T4 CleanUpBehavior
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per eliminare l'appDomain dopo l'elaborazione un modello di testo, includere la riga seguente:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 I modelli di testo vengono elaborati in un appDomain separato dal processo host.  Nella maggior parte dei casi, quando un modello di testo è stato elaborato, l'appdomain viene utilizzato nuovamente per elaborare il modello seguente.  Se tuttavia si specifica CleanupBehavior, l'appDomain viene eliminato e il modello seguente verrà elaborato in un nuovo appDomain.  
  
 Ciò rallenta l'elaborazione del testo, ma può essere utile per assicurarsi che le risorse vengano eliminate.  
  
 Questa direttiva viene eseguita solo nell'host di Visual Studio.