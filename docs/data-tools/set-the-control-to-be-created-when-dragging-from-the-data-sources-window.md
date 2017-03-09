---
title: "Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "Finestra Origini dati, selezione controlli"
  - "Windows Form, visualizzazione dati"
  - "dati [Visual Studio], visualizzazione in Windows Form"
  - "dati [Visual Studio], finestra Origini dati"
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 31
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati
È possibile creare controlli associati a dati tramite trascinamento di elementi dalla finestra **Origini dati** in Progettazione WPF o Progettazione Windows Form.  Ogni elemento nella finestra **Origini dati** è dotato di un controllo predefinito che viene creato quando viene trascinato nella finestra di progettazione.  È tuttavia possibile scegliere di creare un controllo diverso.  
  
## Impostazione dei controlli da creare per oggetti e tabelle dati  
 Prima di trascinare elementi che rappresentano oggetti o tabelle dati dalla finestra **Origini dati**, è possibile scegliere di visualizzare tutti i dati in un unico controllo o visualizzare ogni colonna o proprietà in un controllo separato.  
  
 In questo contesto il termine *oggetto* si riferisce a un oggetto business personalizzato, un'entità \(in un Entity Data Model\) o un oggetto restituito da un servizio.  
  
#### Per impostare i controlli da creare per gli oggetti o le tabelle dati  
  
1.  Verificare che Progettazione WPF o Progettazione Windows Form sia aperto.  
  
2.  Nella finestra **Origini dati** selezionare l'elemento che rappresenta l'oggetto o la tabella dati che si desidera impostare.  
  
3.  Fare clic sul menu a discesa per l'elemento, quindi scegliere uno degli elementi seguenti nel menu:  
  
    -   Per visualizzare ogni campo dati in un controllo separato, fare clic su **Dettagli**.  Quando si trascina l'elemento dati nella finestra di progettazione, viene creato un controllo associato a dati diverso per ogni colonna o proprietà dell'oggetto o della tabella dati padre, insieme a etichette per ogni controllo.  
  
    -   Per visualizzare tutti i dati in un solo controllo, selezionare un controllo diverso nell'elenco, ad esempio **DataGrid** oppure **List** in un'applicazione WPF oppure **DataGridView** in un'applicazione Windows Form.  
  
     L'elenco dei controlli disponibili dipende dalla finestra di progettazione aperta, dalla versione di .NET Framework cui è destinato il progetto e dall'eventuale aggiunta nella **Casella degli strumenti** di controlli personalizzati che supportano l'associazione a dati.  Se il controllo che si desidera creare è presente nell'elenco dei controlli disponibili, è possibile aggiungerlo all'elenco.  Per ulteriori informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Per informazioni sulla creazione di un controllo Windows Form personalizzato che può essere aggiunto all'elenco dei controlli per oggetti o tabelle dati nella finestra **Origini dati**, vedere [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati complessa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).  
  
## Impostazione dei controlli da creare per proprietà o colonne di dati  
 Prima di trascinare un elemento che rappresenta una colonna o una proprietà di un oggetto dalla finestra **Origini dati** alla finestra di progettazione, è possibile impostare il controllo da creare.  
  
#### Per impostare i controlli da creare per proprietà o colonne  
  
1.  Verificare che Progettazione WPF o Progettazione Windows Form sia aperto.  
  
2.  Nella finestra **Origini dati** espandere la tabella o l'oggetto desiderato per visualizzare le rispettive colonne o proprietà.  
  
3.  Selezionare ogni colonna o proprietà per cui si desidera impostare il controllo da creare.  
  
4.  Fare clic sul menu a discesa per la colonna o la proprietà, quindi selezionare il controllo che si desidera creare quando l'elemento viene trascinato nella finestra di progettazione.  
  
     L'elenco dei controlli disponibili dipende dalla finestra di progettazione aperta, dalla versione di .NET Framework cui è destinato il progetto e dai controlli personalizzati che supportano l'associazione a dati aggiunti nella **Casella degli strumenti**.  Se il controllo che si desidera creare è presente nell'elenco dei controlli disponibili, è possibile aggiungerlo all'elenco.  Per ulteriori informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Per informazioni sulla creazione di un controllo personalizzato che può essere aggiunto all'elenco dei controlli per colonne o proprietà nella finestra **Origini dati**, vedere [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     Selezionare **Nessuno** nel menu a discesa se non si desidera creare un controllo per la colonna o la proprietà.  Ciò si rivela utile se si desidera trascinare l'oggetto o la tabella padre nella finestra di progettazione, ma non si desidera includere la colonna o la proprietà specifica.  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md)   
 [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md)