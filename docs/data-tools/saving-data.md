---
title: "Salvataggio di dati | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataRow.RowState"
  - "DataSet.GetChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], salvataggio"
  - "dati [Visual Studio], aggiornamento"
  - "database, aggiornamento"
  - "DBDirect (metodi)"
  - "salvataggio di dati"
  - "metodi DBDirect di TableAdapter"
  - "TableAdapter.Update (metodo)"
  - "aggiornamento di dati"
  - "aggiornamento di database"
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Salvataggio di dati
Il salvataggio dei dati è il processo mediante il quale i dati modificati in un modello dati di un'applicazione vengono salvati in modo permanente nell'archivio dati originale, in genere un database relazionale come SQL Server.  
  
 L'aggiornamento di un'origine dati mediante un modello dati è in genere un processo in due fasi.  La prima fase consiste nell'aggiornare il modello dati con nuove informazioni, ovvero nuovi record, record modificati o record eliminati.  La seconda consiste nel salvare le modifiche apportate al modello dati nel database.  
  
 Negli argomenti seguenti vengono illustrati concetti e attività relativi al salvataggio dei dati.  
  
## Argomenti correlati  
 [Salvataggio dei dati nei dataset](../data-tools/save-data-back-to-the-database.md)  
 Vengono fornite indicazioni generali sulle modalità con cui vengono apportate modifiche a un dataset e su come il dataset tiene traccia delle informazioni relative alle modifiche per salvarle in un database.  
  
 [Salvataggio di dati di entità](../data-tools/saving-entity-data.md)  
 Viene descritto come salvare le modifiche nelle applicazioni [ADO.NET Entity Framework](../Topic/ADO.NET%20Entity%20Framework.md) e [WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md).