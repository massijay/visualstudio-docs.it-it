---
title: "L&#39;istanza sperimentale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "compilazioni sperimentale"
  - "Package VS, compilazioni sperimentale"
  - "VSIP, compilazioni sperimentale"
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# L&#39;istanza sperimentale
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per proteggere l'ambiente di sviluppo di Visual Studio da applicazioni non verificate che è possibile modificarlo, VSSDK fornisce uno spazio sperimentale che è possibile utilizzare per sperimentare. Sviluppare nuove applicazioni utilizzando Visual Studio come di consueto, ma vengono eseguiti utilizzando l'istanza sperimentale.  
  
 Ogni applicazione che dispone di un pacchetto VSIX Avvia istanza sperimentale di Visual Studio in modalità debug.  
  
 Se si desidera avviare l'istanza sperimentale di Visual Studio all'esterno di una soluzione specifica, eseguire il comando seguente nella finestra di comando:  
  
 "*\< percorso di installazione di visual studio \>*\\Common7\\IDE\\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  L'istanza sperimentale viene scritto nel Registro di sistema sotto la `<version number>Exp` e `<version number>Exp_Config` nodi. È ad esempio l'area del Registro di sistema sperimentale di Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 È consigliabile eseguire l'estensione nell'istanza sperimentale durante lo sviluppo. Quando si distribuisce l'estensione, viene eseguito nell'istanza di sviluppo. Per ulteriori informazioni sulla registrazione di applicazioni, vedere [Registrazione di VSPackage](../extensibility/internals/registering-vspackages.md).