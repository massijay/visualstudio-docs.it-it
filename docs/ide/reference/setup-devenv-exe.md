---
title: "-Setup (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "setup (opzione devenv)"
  - "/setup (opzione devenv)"
  - "Devenv, /setup switch"
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Impone a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'unione dei metadati delle risorse che descrivono menu, barre degli strumenti e gruppi di comandi contenuti in tutti i pacchetti VSPackage disponibili.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Note  
 Questa opzione non accetta argomenti. Il comando `devenv /setup` viene in genere eseguito come ultimo passaggio del processo di installazione. L'opzione `/setup` non ha l'effetto di avviare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Per poter usare le opzioni `devenv` e [devenv](../../ide/reference/setup-devenv-exe.md) è necessario eseguire [devenv](../../ide/reference/installvstemplates-devenv-exe.md) come amministratore.  
  
## <a name="example"></a>Esempio  
 Questo esempio illustra l'ultimo passaggio dell'installazione di una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che include pacchetti VSPackage.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)