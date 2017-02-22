---
title: "Distribuzione della shell di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Distribuzione della shell di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una shell isolato consente di determinare quale funzionalità di Visual Studio sono necessarie per interagire con il linguaggio specifico di dominio e come tale soluzione deve essere visualizzato.  Per ulteriori informazioni su Visual Studio la shell isolato, vedere [Personalizzazione Shell isolata](../extensibility/customizing-the-isolated-shell.md).  È possibile trovare ulteriori informazioni su come personalizzare la shell isolato in [Personalizzare la Shell Isolated](http://msdn.microsoft.com/it-it/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### Per impostare una shell di Visual Studio come destinazione di distribuzione  
  
1.  in **DslPackage** progetto, aprire  **source.extension.tt**.  
  
2.  In `<SupportedProducts>` inserimento:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     di sostituzione *MyIsolatedShell* con il nome del pacchetto della shell isolato.