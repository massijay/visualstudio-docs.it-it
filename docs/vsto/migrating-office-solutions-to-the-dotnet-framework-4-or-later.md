---
title: "Migrazione di soluzioni Office a .NET Framework 4 o versioni successive | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.TargetFrameworkWarning"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "progetti di Office [sviluppo per Office in Visual Studio], migrazione a .NET Framework 4"
ms.assetid: 31f6c48b-c086-4362-8629-f644d6083a44
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Migrazione di soluzioni Office a .NET Framework 4 o versioni successive
  Se il framework di destinazione di un progetto di Office viene modificato per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o per versione successiva da una versione precedente di.NET Framework, potrebbero essere necessari alcuni passaggi aggiuntivi per poter continuare a eseguire la soluzione nei computer di sviluppo e degli utenti finali. Per altre informazioni, vedere [Modifiche necessarie per l'esecuzione di progetti di Office migrati a .NET Framework 4 o a .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Inoltre, il progetto potrebbe non venire più compilato. Alcune funzionalità dei progetti di Office dispongono di modelli di programmazione diversi per le diverse versioni di .NET Framework. Quando il framework di destinazione di un progetto di Office viene modificato per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva da una versione precedente di .NET Framework, è necessario apportare le seguenti modifiche al codice del progetto:  
  
-   [Aggiornamento di progetti di Excel e Word di cui si esegue la migrazione a .NET Framework 4 o a .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aggiornamento delle personalizzazioni della barra multifunzione nei progetti di Office di cui si esegue la migrazione a .NET Framework 4 o a .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aggiornamento di aree del modulo in progetti Outlook di cui si esegue la migrazione a .NET Framework 4 o a .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Il framework di destinazione di un progetto di Office cambia quando si aggiorna il progetto da una versione precedente di Visual Studio. Per altre informazioni, vedere [Aggiornamento e migrazione di soluzioni Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Per altre informazioni sul motivo per cui il modello di programmazione di alcune funzionalità di progetti di Office è diverso a seconda che sia destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, vedere [Modifiche alla progettazione dei progetti di Office destinati a .NET Framework 4 o a .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) e [Panoramica di Visual Studio Tools per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## Vedere anche  
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Procedura: destinare una versione di .NET Framework](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)   
 [Risoluzione degli errori nelle soluzioni Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Supporto aggiuntivo per gli errori nelle soluzioni Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  