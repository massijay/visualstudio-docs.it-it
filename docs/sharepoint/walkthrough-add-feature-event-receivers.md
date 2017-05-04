---
title: "Procedura dettagliata: aggiungere ricevitori di eventi di funzionalit&#224; | Microsoft Docs"
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
  - "sviluppo per SharePoint in Visual Studio, strumenti di creazione di pacchetti avanzati"
  - "sviluppo per SharePoint in Visual Studio, ricevitori di eventi"
  - "sviluppo per SharePoint in Visual Studio, ricevitori di eventi di funzionalità"
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Procedura dettagliata: aggiungere ricevitori di eventi di funzionalit&#224;
  I ricevitori di eventi di funzionalità sono i metodi che vengono eseguiti quando, in SharePoint, si verifica uno dei seguenti eventi correlati alle funzionalità:  
  
-   Installazione di una funzionalità.  
  
-   Attivazione di una funzionalità.  
  
-   Disattivazione di una funzionalità.  
  
-   Rimozione di una funzionalità.  
  
 In questa procedura dettagliata viene illustrato come aggiungere un ricevitore di eventi a una funzionalità in un progetto SharePoint.  Vengono illustrate le seguenti attività:  
  
-   Creazione di un progetto vuoto con un ricevitore di eventi di funzionalità.  
  
-   Gestione del metodo **FeatureDeactivating**.  
  
-   Utilizzo del modello a oggetti del progetto SharePoint per aggiungere un annuncio al relativo elenco.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Creazione di un progetto con ricevitore di eventi di funzionalità  
 Creare un progetto in cui possa essere incluso il ricevitore di eventi di funzionalità.  
  
#### Per creare un progetto con un ricevitore di eventi di funzionalità  
  
1.  Sulla barra dei menu scegliere **File**, **Nuovo**, **Progetto** per visualizzare la finestra di dialogo **Nuovo progetto**.  
  
2.  Espandere il nodo **SharePoint** sotto **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **2010**.  
  
3.  Nel riquadro **Modelli**, scegliere il modello **Progetto SharePoint 2010**.  
  
     È possibile utilizzare questo tipo di progetto per i ricevitori di eventi di funzionalità perché non dispongono di alcun modello di progetto.  
  
4.  Nella casella **Nome** digitare FeatureEvtTest, quindi selezionare il pulsante **OK** per visualizzare la **Personalizzazione guidata SharePoint**.  
  
5.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug** immettere l'URL per il sito del server SharePoint a cui si desidera aggiungere il nuovo elemento del campo personalizzato o utilizzare il percorso predefinito \(http:\/\/\<*system name*\>\/\).  
  
6.  Nella sezione **Selezionare il livello di attendibilità per la soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come soluzione farm**.  
  
     Per ulteriori informazioni sulle differenze tra le soluzioni create mediante sandbox e quelle della farm, vedere [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Selezionare il pulsante **Fine**, quindi notare che una funzionalità denominata Funzionalità1 viene visualizzata nel nodo **Funzionalità**.  
  
## Aggiunta di un ricevitore di eventi alla funzionalità.  
 Aggiungere un ricevitore di eventi alla funzionalità e aggiungere codice che viene eseguito quando la funzionalità è disattivata.  
  
#### Per aggiungere un ricevitore di eventi alla funzionalità  
  
1.  Aprire il menu di scelta rapida del nodo Funzionalità e quindi selezionare **Aggiungi funzionalità** per creare una funzionalità.  
  
2.  Nel nodo **Funzionalità**, aprire il menu di scelta rapida per **Funzionalità1**, quindi scegliere **Aggiungi ricevitore di eventi** per aggiungere un ricevitore di eventi alla funzionalità.  
  
     Questa operazione consente di aggiungere un file di codice sotto Funzionalità1.  In questo caso, viene denominato Feature1.EventReceiver.cs o Feature1.EventReceiver.vb, a seconda del linguaggio di sviluppo del progetto.  
  
3.  Se il progetto è scritto in [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], aggiungere il seguente codice all'inizio del ricevitore di eventi se non è già presente:  
  
     [!code-csharp[SP_FeatureEvt#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  Nella classe del ricevitore di eventi sono presenti numerosi metodi impostati come commenti che vengono utilizzati come eventi.  Sostituire il metodo **FeatureDeactivating** con quanto riportato di seguito:  
  
     [!code-csharp[SP_FeatureEvt#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#2)]
     [!code-vb[SP_FeatureEvt#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_featureevt/vb/features/feature1/feature1.eventreceiver.vb#2)]  
  
## Test del ricevitore di eventi di funzionalità  
 Disattivare la funzionalità per testare se attraverso il metodo **FeatureDeactivating** viene generato un annuncio nell'elenco Annunci di SharePoint.  
  
#### Per testare il ricevitore di eventi di funzionalità  
  
1.  Impostare il valore della proprietà del progetto **Configurazione distribuzione attiva** su **Nessuna attivazione**.  
  
     L'impostazione di questa proprietà impedisce l'attivazione della funzionalità in SharePoint e consente di eseguire il debug dei ricevitori di eventi di funzionalità.  Per ulteriori informazioni, vedere [Debug di soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Premere il tasto **F5** per eseguire e distribuire il progetto in SharePoint.  
  
3.  Nella parte superiore della pagina Web di SharePoint, aprire il menu **Azioni sito**, quindi scegliere **Impostazioni sito**.  
  
4.  Nella sezione **Azioni sito** della pagina **Impostazioni sito** selezionare il collegamento **Gestisci caratteristiche sito**.  
  
5.  Nella pagina **Funzionalità sito**, selezionare il pulsante **Attiva** accanto alla funzionalità **FeatureEvtTest Funzionalità1**.  
  
6.  Nella pagina **Funzionalità**, scegliere il pulsante **Disattiva** accanto alla funzionalità **FeatureEvtTest Funzionalità1** quindi scegliere il collegamento di conferma **Disattiva questa funzione** per disattivare la funzionalità.  
  
7.  Selezionare il pulsante **Home**.  
  
     Notare che dopo la disattivazione della funzionalità, nell'elenco **Annunci** viene visualizzato un annuncio.  
  
## Vedere anche  
 [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  