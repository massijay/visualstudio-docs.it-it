---
title: "Comando DslTextTransform | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, comandi"
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 30
caps.handback.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Comando DslTextTransform
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DslTextTransform.cmd è uno script che chiama TextTransform.exe e viene eseguito con le opzioni comuni. È possibile utilizzare DslTextTransformation.cmd per automatizzare le compilazioni notturne del [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] progetti. Per ulteriori informazioni, vedere [la generazione di file con l'utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd si trova nella directory seguente:  
  
 **\< percorso di installazione di visual Studio SDK>\VisualStudioIntegration\Tools\Bin**  
  
 Come input per DslTextTransform.cmd, è possibile specificare gli argomenti seguenti:  
  
-   Directory di output del progetto di modello di dominio.  
  
-   Directory di output del progetto di definizione della finestra di progettazione.  
  
-   Il percorso del file di modello di testo.  
  
 DslTextTransform.cmd elabora il file di modello di testo specificato utilizzando i processori di direttive predefinito e gli assembly. Se si creano i processori di direttiva personalizzati, è possibile creare un file batch che chiama TextTransform.exe. In questo file batch, è possibile specificare gli assembly e i processori di direttive personalizzati associati.