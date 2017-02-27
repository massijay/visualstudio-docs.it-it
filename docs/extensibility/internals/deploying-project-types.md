---
title: "Tipi di progetto di distribuzione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti [Visual Studio SDK], codice gestito"
  - "aggregatore di progetti [Visual Studio SDK]"
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Tipi di progetto di distribuzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Installa un nuovo aggregatore di tipi di progetto \(ProjectAggregator2. dll\) e anche un pacchetto Windows Installer per la ridistribuzione \(ProjectAggregator2.msi\). È necessario utilizzare l'aggregatore di nuovo per tipi di progetto di codice gestito. ProjectAggregator2 funziona limitazioni alternative di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto aggregatore per evitare che i tipi di progetto di codice gestito funziona correttamente. I passaggi seguenti descrivono come modificare il pacchetto Visual Studio per utilizzare l'aggregatore di nuovo.  
  
1.  Rimuovere il progetto NativeHierarchyWrapper dalla soluzione.  
  
2.  Rimuovere tutti i file binari NativeHierarchyWrapper dall'installazione.  
  
3.  Aggiungere ProjectAggregator2.msi alla propria configurazione.