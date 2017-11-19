---
title: "Utilizzare i set di dati nelle applicazioni a più livelli | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 85062fe6ea82a73fbc2d64e1d1ce9136d16831cf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Utilizzare i set di dati nelle applicazioni a più livelli
*Applicazioni dati a più livelli* sono applicazioni mirate ai dati separate in più livelli logici (o *livelli*). In altre parole, un'applicazione dati a più livelli è un'applicazione separata in più progetti, con il livello di accesso ai dati, il livello di logica di business e il livello di presentazione, ciascuno in un progetto distinto. Per ulteriori informazioni, vedere [panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md).  
  
I dataset tipizzati sono stati migliorati in modo da poter generare classi TableAdapter e di dataset in progetti discreti, consentendo di separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.  
  
Supporto di più livelli nei dataset tipizzati consente lo sviluppo iterativo dell'architettura dell'applicazione in una progettazione a più livelli. Rimuove inoltre la necessità di separare manualmente il codice in più di un progetto. Avviare la progettazione del livello dati utilizzando il **Progettazione Dataset**. Quando è pronti per eseguire l'architettura dell'applicazione a una progettazione a n livelli, impostare il **progetto DataSet** proprietà di un set di dati per generare la classe di dataset in un progetto separato.  
  
## <a name="reference"></a>Riferimento  
<xref:System.Data.DataSet>  
<xref:System.Data.TypedTableBase%601>  
  
## <a name="see-also"></a>Vedere anche
[Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)  
[Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
[Aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[Aggiungere il codice nei set di dati di applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
[Aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md)  
[Separare set di dati e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
[Aggiornamento gerarchico](../data-tools/hierarchical-update.md)  
[Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
[Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
[Creare e configurare gli oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)  
[A più livelli e applicazioni Remote con LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)