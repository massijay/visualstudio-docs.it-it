---
title: "Procedura: creare oggetti TableAdapter | Microsoft Docs"
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
  - "creazione di TableAdapter"
  - "dati [Visual Studio], creazione di componenti di dati"
  - "dati [Visual Studio], creazione di adattatori di tabella"
  - "dati [Visual Studio], TableAdapters"
  - "adattatori di tabelle, creazione"
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: creare oggetti TableAdapter
Gli oggetti TableAdapter consentono di stabilire una comunicazione tra l'applicazione e un database.  In particolare, un oggetto TableAdapter consente di connettersi a un database e di eseguire query o stored procedure e quindi restituisce una nuova tabella di dati popolata con i dati ottenuti oppure riempie un oggetto <xref:System.Data.DataTable> esistente con i dati ottenuti.  I TableAdapter vengono utilizzati inoltre per inviare i dati aggiornati dall'applicazione al database.  
  
 È possibile creare oggetti TableAdapter effettuando una delle seguenti operazioni:  
  
-   Esecuzione della [TableAdapter \(configurazione guidata\)](../Topic/TableAdapter%20Configuration%20Wizard.md) da [Progettazione DataSet](../data-tools/creating-and-editing-typed-datasets.md).  
  
-   Esecuzione della [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) selezionando il tipo di origine dati **Database** o **Servizio Web**.  
  
-   Trascinamento degli oggetti di database da [Esplora server](../Topic/Server%20Explorer.md) in **Progettazione DataSet**.  
  
 Per un'introduzione agli oggetti TableAdapter, vedere [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Creazione di oggetti TableAdapter con la Configurazione guidata TableAdapter  
 La **Configurazione guidata TableAdapter** crea un oggetto TableAdapter singolo sulla base delle informazioni fornite dall'utente.  
  
#### Per creare un oggetto TableAdapter con la Configurazione guidata TableAdapter  
  
1.  Aprire un dataset in **Progettazione DataSet**.  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Trascinare nell'area di progettazione un oggetto **TableAdapter** dalla scheda **DataSet** della **Casella degli strumenti**.  
  
     Verrà avviata la **Configurazione guidata TableAdapter**.  
  
3.  Al completamento della procedura guidata al dataset verranno aggiunti una tabella dati e un oggetto TableAdapter.  Per ulteriori informazioni, vedere [TableAdapter \(configurazione guidata\)](../Topic/TableAdapter%20Configuration%20Wizard.md).  
  
## Creazione di oggetti TableAdapter con la Configurazione guidata origine dati  
 La **Configurazione guidata origine dati** crea un oggetto TableAdapter per ciascun oggetto di database selezionato durante l'esecuzione della procedura guidata.  Una volta completata la **Configurazione guidata origine dati**, è possibile visualizzare gli oggetti TableAdapter creati aprendo il dataset in **Progettazione DataSet**.  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
#### Per creare un oggetto TableAdapter con la Configurazione guidata origine dati  
  
1.  Selezionare **Aggiungi nuova origine dati** nella [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  Scegliere **Mostra origini dati** dal menu **Dati** per visualizzare la finestra **Origini dati**.  
  
     Verrà avviata la **Configurazione guidata origine dati**.  
  
2.  Completare la procedura guidata selezionando il tipo di origine dati **Database** o **Servizio Web**.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md) o [Procedura: connettersi ai dati di un servizio](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
## Creazione di oggetti TableAdapter dagli oggetti di database di Esplora server  
 Per ciascun oggetto di database trascinato in **Progettazione DataSet** viene creato un solo oggetto TableAdapter.  
  
#### Per creare un oggetto TableAdapter dagli oggetti di database di Esplora server  
  
1.  Aprire un dataset in **Progettazione DataSet**.  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Trascinare un oggetto di database da una connessione dati in [Esplora server](../Topic/Server%20Explorer.md) nell'area **Progettazione DataSet**.  
  
     Al dataset vengono aggiunti una tabella dati e un oggetto TableAdapter.  
  
## Vedere anche  
 [Procedura: aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)