---
title: "Procedura: compilare pi&#249; configurazioni contemporaneamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: compilare pi&#249; configurazioni contemporaneamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mediante la finestra di dialogo **Compilazione batch** è possibile compilare la maggior parte dei tipi di progetti con più, o addirittura, tutte le configurazioni della build contemporaneamente.  Tuttavia, non è possibile compilare i seguenti tipi di progetti in più configurazioni della build contemporaneamente:  
  
1.  App di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] compilata per Windows usando JavaScript.  
  
2.  Tutti i progetti di Visual Basic  
  
 Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
### Per compilare un progetto in più configurazioni della build  
  
1.  Nella barra dei menu scegliere **Compilazione batch**  dal menu **Compilazione**.  
  
2.  Nella colonna **Compila**, selezionare le caselle di controllo per le configurazioni in cui si desidera compilare un progetto.  
  
    > [!TIP]
    >  Per modificare o creare una configurazione della build per una soluzione, scegliere **Compilazione**, **Gestione configurazione** nella barra dei menu per aprire la finestra di dialogo **Gestione configurazione**.  Dopo aver modificato una configurazione della build per una soluzione, scegliere il pulsante **Ricompila** nella finestra di dialogo **Compilazione batch** per aggiornare tutte le configurazioni della build per i progetti nella soluzione.  
  
3.  Scegliere i pulsanti **Compila** o **Ricompila** per compilare il progetto con le configurazioni specificate.  
  
## Vedere anche  
 [Procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)   
 [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)   
 [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)