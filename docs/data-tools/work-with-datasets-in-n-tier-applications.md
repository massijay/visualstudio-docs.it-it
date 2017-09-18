---
title: "Utilizzo dei dataset nelle applicazioni a pi&#249; livelli | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Basic], applicazioni a più livelli"
  - "DataSet (progetto) [applicazioni a più livelli VS]"
  - "dataset [Visual Basic], applicazioni a più livelli"
  - "applicazioni distribuite [applicazioni a più livelli VS]"
  - "applicazioni a più livelli"
  - "applicazioni database a più livelli"
  - "applicazioni a più livelli"
  - "TableAdapters, applicazioni a più livelli"
  - "livelli, applicazioni a più livelli"
  - "dataset tipizzati, applicazioni a più livelli"
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizzo dei dataset nelle applicazioni a pi&#249; livelli
Le *applicazioni dati a più livelli* sono applicazioni mirate ai dati separate in più *livelli* logici.  In altre parole, un'applicazione dati a più livelli è un'applicazione separata in più progetti, con il livello di accesso ai dati, il livello di logica di business e il livello di presentazione, ciascuno in un progetto distinto.  Per altre informazioni, vedere [Cenni preliminari sull'applicazione dati a più livelli](../data-tools/n-tier-data-applications-overview.md).  
  
 I dataset tipizzati sono stati migliorati in modo da poter generare classi TableAdapter e di dataset in progetti discreti,  consentendo di separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.  
  
 Il supporto di più livelli nei dataset tipizzati consente lo sviluppo iterativo dell'architettura dell'applicazione in una progettazione a più livelli ed elimina la necessità di separare manualmente il codice in più progetti.  Iniziare la progettazione del livello dati usando [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  Prima di applicare l'architettura dell'applicazione in una progettazione a più livelli, impostare la proprietà **DataSet Project** di un dataset per generare la classe di dataset in un progetto separato.  
  
## In questa sezione  
 [Procedura: separare dataset e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Descrive come spostare la classe di dataset generata dal progetto contenente le classi TableAdapter generate in un nuovo progetto.  
  
 [Procedura: aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Descrive come generare una classe parziale in cui aggiungere il codice per una classe TableAdapter a più livelli.  
  
 [Procedura: aggiungere il codice nei dataset di applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Descrive come generare una classe parziale in cui aggiungere il codice per un dataset a più livelli.  
  
 [Procedura: aggiungere la convalida a un dataset a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Descrive dove aggiungere il codice per eseguire la convalida sulla modifica dei dati.  
  
 [Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Fornisce istruzioni dettagliate per la creazione di un dataset tipizzato e la separazione del codice degli elementi TableAdapter e dataset in più progetti.  
  
 [Procedura dettagliata: aggiunta della convalida a un'applicazione dati a più livelli](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)  
 Fornisce istruzioni dettagliate per l'aggiunta della convalida all'applicazione creata nella procedura dettagliata relativa all'applicazione dati a più livelli.  
  
## Riferimenti  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## Sezioni correlate  
 [Cenni preliminari sull'applicazione dati a più livelli](../data-tools/n-tier-data-applications-overview.md)  
  
 [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)  
  
 [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)  
  
 [Applicazioni a più livelli e remote con LINQ to SQL](../Topic/N-Tier%20and%20Remote%20Applications%20with%20LINQ%20to%20SQL.md)