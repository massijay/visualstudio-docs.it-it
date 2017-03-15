---
title: "Aggiornamento gerarchico | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "dati [Visual Basic], aggiornamento gerarchico"
  - "dataset [Visual Basic], aggiornamento gerarchico"
  - "aggiornamento gerarchico"
  - "dati modificati (salvataggio)"
  - "tabelle correlate, salvataggio"
  - "salvataggio di dati, dati modificati"
  - "salvataggio di dati, aggiornamento gerarchico"
  - "salvataggio di dati aggiornati"
  - "dati aggiornati (salvataggio)"
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 26
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Aggiornamento gerarchico
Per *aggiornamento gerarchico* si intende il processo con il quale i dati aggiornati da un dataset con due o più tabelle correlate vengono salvati in un database rispettando allo stesso tempo le regole di integrità referenziale.  Con *integrità referenziale* si fa riferimento alle regole di coerenza fornite dai vincoli all'interno di un database che controllano il comportamento delle operazioni di inserimento, aggiornamento ed eliminazione dei record correlati.  Ad esempio, l'integrità referenziale fa in modo che il record di un cliente venga creato prima degli ordini di tale cliente.  
  
 Il salvataggio dei dati modificati dalle tabelle dati correlate è più complesso del salvataggio dei dati da una singola tabella,  poiché i comandi di aggiornamento, inserimento ed eliminazione per ogni tabella correlata devono essere eseguiti in un ordine specifico per evitare di violare i vincoli dell'integrità referenziale.  Si consideri ad esempio un'applicazione di immissione ordini in cui è possibile gestire clienti e ordini sia nuovi che esistenti.  Per eliminare un record del cliente esistente, è necessario prima eliminare tutti gli ordini del cliente.  Per aggiungere un nuovo cliente con un ordine, è necessario prima inserire il nuovo record del cliente e successivamente gli ordini del cliente a causa dei vincoli di chiave esterna presenti nelle tabelle.  Come illustrato negli esempi seguenti, è necessario estrarre i sottoinsiemi di dati specifici e inviare gli aggiornamenti \(comandi di inserimento, aggiornamento ed eliminazione\) nell'ordine corretto allo scopo di mantenere l'integrità referenziale.  
  
 La funzionalità di aggiornamento gerarchico utilizza un `TableAdapterManager` per gestire i `TableAdapter` all'interno di un dataset tipizzato.  Il componente `TableAdapterManager` è un componente generato di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], pertanto non fa parte di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Per informazioni dettagliate sulla classe `TableAdapterManager`, vedere la sezione Riferimento di TableAdapterManager di [Panoramica di TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
 Se l'applicazione utilizza dataset tipizzati e consente agli utenti di modificare i dati nelle tabelle dati correlate \(tabelle dati in una relazione uno\-a\-molti come Customers e Orders\), è possibile utilizzare l'aggiornamento gerarchico.  
  
## In questa sezione  
 [Cenni preliminari sull'aggiornamento gerarchico](../Topic/Hierarchical%20Update%20Overview.md)  
 Vengono illustrati l'aggiornamento gerarchico e la relativa implementazione.  
  
 [Panoramica di TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)  
 Vengono illustrati il componente `TableAdapterManager` e il codice di `TableAdapterManager` generato da Progettazione DataSet.  
  
 [Procedura: abilitare e disabilitare l'aggiornamento gerarchico](../Topic/How%20to:%20Enable%20and%20Disable%20Hierarchical%20Update.md)  
 Viene illustrato come impostare la proprietà `Hierarchical Update` di un dataset tipizzato per generare il codice per salvare le tabelle correlate.  
  
 [Procedura: configurare i vincoli di chiave esterna in un dataset](../Topic/How%20to:%20Configure%20Foreign-Key%20Constraints%20in%20a%20Dataset.md)  
 Viene illustrato come configurare i vincoli in un dataset.  
  
 [Procedura: eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
 Viene illustrato come interrompere tutte le modifiche in corso nei controlli con associazione a dati in un form per preparare il salvataggio dell'origine dati.  
  
 [Procedura: impostare l'ordine per l'esecuzione di un aggiornamento gerarchico](../Topic/How%20to:%20Set%20the%20Order%20When%20Performing%20a%20Hierarchical%20Update.md)  
 Viene illustrato come impostare la proprietà `UpdateOrder` di un `TableAdapterManager` per controllare l'ordine di esecuzione dei comandi di inserimento, aggiornamento ed eliminazione.  
  
 [Procedura: implementare l'aggiornamento gerarchico in progetti di Visual Studio esistenti](../Topic/How%20to:%20Implement%20Hierarchical%20Update%20in%20Existing%20Visual%20Studio%20Projects.md)  
 Viene illustrato come aggiornare un'applicazione contenente tabelle dati correlate per salvare i dati mediante `TableAdapterManager`.  
  
 [Procedura dettagliata: salvataggio dei dati dalle tabelle dati correlate \(aggiornamento gerarchico\)](../Topic/Walkthrough:%20Saving%20Data%20from%20Related%20Data%20Tables%20\(Hierarchical%20Update\).md)  
 Vengono fornite istruzioni dettagliate per la creazione di un'applicazione contenente tabelle dati correlate e il salvataggio dei dati mediante `TableAdapterManager`.  
  
## Riferimenti  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.DataTable>  
  
## Sezioni correlate  
 [Utilizzo dei dataset nelle applicazioni a più livelli](../data-tools/work-with-datasets-in-n-tier-applications.md)  
  
 [Salvataggio di dati](../data-tools/saving-data.md)  
  
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)  
  
 [TableAdapters](../Topic/TableAdapters.md)  
  
 [DataSet, DataTable e DataView](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)  
  
 [DataTable](../Topic/DataTables.md)  
  
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)