---
title: "Procedura dettagliata: creare un&#39;attivit&#224; personalizzata per un flusso di lavoro del sito"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "attività di flusso di lavoro personalizzate [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, attività di flusso di lavoro personalizzate"
  - "sviluppo per SharePoint in Visual Studio, flussi di lavoro di sito"
  - "flussi di lavoro del sito [sviluppo per SharePoint in Visual Studio]"
  - "attività di flusso di lavoro [sviluppo per SharePoint in Visual Studio]"
ms.assetid: 8219a779-c27b-4186-92c9-5bda03328aa9
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Procedura dettagliata: creare un&#39;attivit&#224; personalizzata per un flusso di lavoro del sito
  In questa procedura dettagliata viene illustrato come creare un'attività personalizzata per un flusso di lavoro a livello di sito utilizzando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. I flussi di lavoro a livello di sito si applicano a tutto il sito, non solo a un relativo elenco. L'attività personalizzata consente di creare un elenco Annunci di backup e successivamente di copiarvi il contenuto dell'elenco originale.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un flusso di lavoro a livello di sito.  
  
-   Creazione di un'attività di flusso di lavoro personalizzata.  
  
-   Creazione ed eliminazione di un elenco di SharePoint.  
  
-   Copia di elementi da un elenco a un altro.  
  
-   Visualizzazione di un elenco nella barra Avvio veloce.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Creazione di un progetto di attività personalizzata per un flusso di lavoro del sito  
 Creare un progetto per gestire e testare l'attività personalizzata per un flusso di lavoro.  
  
#### Per creare un progetto di attività personalizzata per un flusso di lavoro del sito  
  
1.  Sulla barra dei menu scegliere **File**, **Nuovo**, **Progetto** per visualizzare la finestra di dialogo **Nuovo progetto**.  
  
2.  Espandere il nodo **SharePoint** sotto **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **2010**.  
  
3.  Nel riquadro **Modelli**, scegliere il modello **Progetto SharePoint 2010**.  
  
4.  Nella casella di testo **Nome** inserire AnnouncementBackup, quindi selezionare il pulsante **OK**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
5.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug**, scegliere l'opzione del pulsante **Distribuisci come soluzione farm**, quindi selezionare il pulsante **Finish** per accettare il livello di affidabilità e il sito predefinito.  
  
     Questo passaggio consente di impostare il livello di attendibilità per la soluzione come soluzione della farm, ovvero l'unica opzione disponibile per i progetti flusso di lavoro.  
  
6.  In **Esplora soluzioni** scegliere il nodo del progetto, quindi, nella barra dei menu scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
7.  Sotto **Visual C\#** o **Visual Basic**, espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
8.  Nel riquadro **Modelli**, scegliere il modello **Flusso di lavoro sequenziale \(solo soluzione farm\)** quindi scegliere il pulsante **Aggiungi**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
9. Nella pagina **Specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito \(AnnouncementBackup \- Workflow1\).  Modificare il tipo di modello di flusso di lavoro in **Flusso di lavoro**, quindi scegliere il pulsante **Avanti**.  
  
10. Selezionare il pulsante **Fine** per accettare i valori predefiniti impostati.  
  
## Aggiunta di una classe di attività personalizzata per un flusso di lavoro  
 Aggiungere al progetto una classe in cui sarà contenuto il codice per l'attività personalizzata del flusso di lavoro.  
  
#### Per aggiungere una classe di attività personalizzata per un flusso di lavoro  
  
1.  Nella barra dei menu, scegliere **Progetto**, **Aggiungi nuovo elemento** per visualizzare la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Nella visualizzazione struttura ad albero **Modelli installati** selezionare il nodo **Codice**, quindi selezionare il modello **Classe** nell'elenco di modelli degli elementi di progetto.  Utilizzare il nome predefinito Class1.  Scegliere il pulsante **Aggiungi**.  
  
3.  Sostituire tutto il codice in Class1 con quanto riportato di seguito:  
  
     [!code-csharp[SP_AnnBackup#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_annbackup/cs/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_annbackup/vb/class1.vb#1)]  
  
4.  Salvare il progetto, quindi, nel barra dei menu, scegliere **Compila**, **Compila soluzione**.  
  
     Class1 viene visualizzato come azione personalizzata nella **Casella degli strumenti** nella scheda **Componenti AnnouncementBackup**.  
  
## Aggiunta dell'attività personalizzata al flusso di lavoro del sito  
 Aggiungere al flusso di lavoro un'attività in cui sarà contenuto il codice personalizzato.  
  
#### Per aggiungere un'attività personalizzata al flusso di lavoro del sito  
  
1.  Aprire Workflow1 in Progettazione flussi di lavoro nella visualizzazione Progettazione.  
  
2.  Trascinare Class1 da **Casella degli strumenti** affinché venga visualizzata nell'attività `onWorkflowActivated1`, o aprire il menu di scelta rapida per Class1, scegliere **Copia**, aprire il menu di scelta rapida per la riga all'attività `onWorkflowActivated1` quindi scegliere **Incolla**.  
  
3.  Salvare il progetto.  
  
## Test dell'attività personalizzata per un flusso di lavoro del sito  
 Eseguire il progetto e avviare il flusso di lavoro del sito.  L'attività personalizzata consente di creare un elenco Annunci di backup e di copiarvi il contenuto dell'elenco originale.  Il codice permette inoltre di controllare se è già presente un elenco di backup prima di creare uno;  in tal caso l'elenco viene eliminato.  Il codice consente anche di aggiungere un collegamento al nuovo elenco nella barra Avvio veloce del sito di SharePoint.  
  
#### Per testare l'attività personalizzata per un flusso di lavoro del sito  
  
1.  Premere il tasto F5 per eseguire e distribuire il progetto in SharePoint.  
  
2.  Nella barra Avvio veloce selezionare il collegamento **Elenchi** per visualizzare tutti gli elenchi disponibili nel sito di SharePoint.  Notare che è presente un solo elenco per gli annunci denominato **Annunci**.  
  
3.  Nella parte superiore della pagina Web di SharePoint, scegliere il collegamento **Sito Flusso di lavoro**.  
  
4.  Nella sezione Avvio di un nuovo flusso di lavoro, scegliere il collegamento **AnnouncementBackup – Workflow1**.  Questa operazione comporta l'avvio del flusso di lavoro del sito e l'esecuzione del codice nell'azione personalizzata.  
  
5.  Nella barra Avvio Veloce, scegliere il collegamento **Backup annunci**.  Notare che tutti gli annunci contenuti nell'elenco **Annunci** sono stati copiati in questo nuovo elenco.  
  
## Vedere anche  
 [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  