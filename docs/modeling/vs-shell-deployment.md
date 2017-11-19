---
title: Distribuzione di Visual Studio Shell | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: e7632b99d3fa9d347b5a259cd446edc2f6d9efa8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio
Una shell isolata consente di determinare quali Visual Studio funzionalità necessarie interagire con il linguaggio specifico di dominio e l'aspetto di tale soluzione. Per ulteriori informazioni sulla shell di Visual Studio isolated, vedere [personalizzazione Shell isolata](../extensibility/customizing-the-isolated-shell.md). È possibile trovare ulteriori informazioni su come personalizzare la shell isolata in [personalizzazione Shell isolata](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Per impostare una Shell di Visual Studio come destinazione di distribuzione  
  
1.  Nel **DslPackage** progetto, aprire **source.extension.tt**.  
  
2.  In `<SupportedProducts>` inserire:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Sostituire *MyIsolatedShell* con il nome del pacchetto di shell isolata.