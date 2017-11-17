---
title: Direttiva T4 CleanUpBehavior | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: f60151ba4563c07cd9f6f6619982d8e6a8657ead
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="t4-cleanupbehavior-directive"></a>Direttiva T4 CleanUpBehavior
Per eliminare l'appDomain dopo l'elaborazione un modello di testo, includere la riga seguente:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 I modelli di testo vengono elaborati in un appDomain separato dal processo host. Nella maggior parte dei casi, quando un modello di testo è stato elaborato, l'appdomain viene utilizzato nuovamente per elaborare il modello seguente. Se tuttavia si specifica CleanupBehavior, l'appDomain viene eliminato e il modello seguente verrà elaborato in un nuovo appDomain.  
  
 Ciò rallenta l'elaborazione del testo, ma può essere utile per assicurarsi che le risorse vengano eliminate.  
  
 Questa direttiva viene eseguita solo nell'host di Visual Studio.