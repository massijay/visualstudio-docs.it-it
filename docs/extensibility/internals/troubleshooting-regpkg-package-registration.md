---
title: "Registrazione risoluzione dei problemi del pacchetto di RegPkg | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RegPkg"
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrazione risoluzione dei problemi del pacchetto di RegPkg
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Il modo migliore per la registrazione di pacchetti in Visual Studio è tramite i file. pkgdef. Ciò consente di distribuire le estensioni senza dover accedere al Registro di sistema. I file pkgdef vengono creati tramite il [Utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Per registrare un pacchetto utilizzando RegPkg in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è necessario utilizzare la versione di RegPkg appropriata per il pacchetto.  
  
## Versioni RegPkg relativi a versioni di pacchetto  
 Esistono due versioni di RegPkg. Una versione è incluso in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Utilizzare questa versione per registrare pacchetti compilati utilizzando uno degli assembly seguenti:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 È possibile registrare pacchetti compilati utilizzando l'assembly shell precedenti.  
  
 La versione precedente di RegPkg possibile registrare pacchetti compilati utilizzando l'assembly di shell. Tuttavia, non è registrato per i pacchetti creati con versioni successive di tale assembly.  
  
## Vedere anche  
 [Rilascio di un prodotto](../../misc/releasing-a-visual-studio-integration-product.md)