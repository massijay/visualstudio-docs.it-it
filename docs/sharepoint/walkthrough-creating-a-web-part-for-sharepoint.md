---
title: "Procedura dettagliata: creazione di una web part per SharePoint | Microsoft Docs"
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
  - "Web part [sviluppo per SharePoint in Visual Studio], creazione"
  - "Web part [sviluppo per SharePoint in Visual Studio], progettazione"
  - "Web part [sviluppo per SharePoint in Visual Studio], sviluppo"
ms.assetid: 51fb5bdd-b99c-4716-83bc-e66a5da15169
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Procedura dettagliata: creazione di una web part per SharePoint
  Le web part consentono agli utenti di modificare direttamente il contenuto, l'aspetto e il comportamento di pagine del sito di SharePoint tramite un browser.  In questa procedura dettagliata viene illustrato come creare una web part tramite il modello di elemento **Web part** in Visual Studio 2010.  
  
 Nella web part vengono visualizzati i dipendenti in una griglia dati.  Il percorso del file contenente i dati relativi ai dipendenti viene specificato dall'utente.  L'utente può inoltre filtrare la griglia dati in modo che dipendenti con il ruolo di manager vengano visualizzati solo nell'elenco.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di una web part tramite il modello di elemento **Web part** di Visual Studio.  
  
-   Creazione di una proprietà che può essere impostata dall'utente della Web part.  Questa proprietà specifica il percorso del file di dati dei dipendenti.  
  
-   Rendering del contenuto in una web part mediante l'aggiunta di controlli alla raccolta di controlli web part.  
  
-   Creazione di una nuova voce di menu, definita *verbo*, visualizzata nel menu dei verbi della web part di cui è stato eseguito il rendering.  I verbi consentono all'utente di modificare i dati visualizzati nella web part.  
  
-   Test della web part in SharePoint.  
  
    > [!NOTE]  
    >  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] o un'edizione di Visual Studio Application Lifecycle Management \(ALM\).  
  
## Creazione di un progetto SharePoint vuoto  
 Creare innanzitutto un progetto SharePoint vuoto.  In un secondo momento, si aggiungerà una web part al progetto tramite il modello di elemento **Web part**.  
  
#### Per creare un progetto SharePoint vuoto  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizzando l'opzione **Esegui come amministratore**.  
  
2.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **SharePoint** sotto il linguaggio che si desidera utilizzare, quindi selezionare il nodo **2010**.  
  
4.  Nel riquadro **Modelli**, scegliere la voce **Progetto SharePoint 2010**, quindi fare clic sul pulsante **OK**.  
  
     Verrà visualizzata la **Personalizzazione guidata SharePoint** .  Questa procedura guidata consente di selezionare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.  
  
5.  Selezionare il pulsante di opzione **Distribuisci come soluzione farm**, quindi fare clic sul pulsante **Fine** per accettare il sito di SharePoint locale predefinito.  
  
## Aggiunta di una web part al progetto  
 Aggiungere un elemento **Web part** al progetto.  L'elemento **Web part** consente di aggiungere il file di codice della web part.  In un secondo momento, si aggiungerà codice al file di codice della web part per eseguire il rendering del contenuto della web part.  
  
#### Per aggiungere una web part al progetto  
  
1.  Nella barra dei menu, scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** nel pannello **Modelli installati** espandere il nodo **SharePoint**, quindi fare clic su **2010**.  
  
3.  Nell'elenco dei modelli SharePoint, scegliere il modello **Web Part** e quindi fare click sul pulsante **OK**.  
  
     L'elemento **Web part** verrà visualizzato in **Esplora soluzioni**.  
  
## Rendering del contenuto nella web part  
 È possibile specificare quali controlli si desidera visualizzare nella web part aggiungendoli alla raccolta di controlli della classe Web part.  
  
#### Per eseguire il rendering del contenuto nella web part  
  
1.  In **Esplora soluzioni** aprire WebPart1.vb \(in Visual Basic\) o WebPart1.cs \(in C\#\).  
  
     Il file di codice della web part viene aperto nell'editor di codice.  
  
2.  Aggiungere le seguenti istruzioni all'inizio del file di codice della web part.  
  
     [!code-csharp[SP_WebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#1)]  
  
3.  Aggiungere il codice seguente alla classe `WebPart1`.  In questo codice vengono dichiarati i campi seguenti:  
  
    -   Griglia dati per la visualizzazione dei dipendenti nella web part.  
  
    -   Testo visualizzato nel controllo utilizzato per filtrare la griglia dati.  
  
    -   Etichetta che visualizza un errore se non è possibile visualizzare dati nella griglia dati.  
  
    -   Stringa contenente il percorso del file di dati dei dipendenti.  
  
     [!code-csharp[SP_WebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#2)]  
  
4.  Aggiungere il codice seguente alla classe `WebPart1`.  Questo codice aggiunge alla web part una proprietà personalizzata denominata `DataFilePath`.  Una proprietà personalizzata è una proprietà che può essere impostata dall'utente in SharePoint.  Questa proprietà ottiene e imposta il percorso di un file di dati XML utilizzato per popolare la griglia dati.  
  
     [!code-csharp[SP_WebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#3)]  
  
5.  Sostituire il metodo `CreateChildControls` con il codice seguente.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Aggiunta della griglia dati e dell'etichetta dichiarate nel passaggio precedente.  
  
    -   Associazione della griglia dati a un file XML che contiene dati dei dipendenti.  
  
     [!code-csharp[SP_WebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#4)]  
  
6.  Aggiungere il seguente metodo alla classe `WebPart1`.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Creazione di un verbo che viene visualizzato nel menu dei verbi della web part di cui è stato eseguito il rendering.  
  
    -   Gestisce l'evento generato quando l'utente seleziona il verbo nel menu dei verbi.  Questo codice filtra l'elenco dei dipendenti visualizzato nella griglia dati.  
  
     [!code-csharp[SP_WebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#5)]  
  
## Test della web part  
 Quando si esegue il progetto viene aperto il sito di SharePoint.  La web part viene aggiunta automaticamente alla Raccolta web part in SharePoint.  È possibile aggiungere la web part a qualsiasi pagina web part.  
  
#### Per testare la web part  
  
1.  Incollare il codice XML riportato di seguito in un file del Blocco note.  Questo file XML contiene i dati di esempio che saranno visualizzati nella web part.  
  
    ```  
  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
       <employee>  
           <name>David Hamilton</name>  
           <hireDate>2001-05-11</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Karina Leal</name>  
           <hireDate>1999-04-01</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Nancy Davolio</name>  
           <hireDate>1992-05-01</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Steven Buchanan</name>  
           <hireDate>1955-03-04</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Suyama Michael</name>  
           <hireDate>1963-07-02</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
    </employees>  
    ```  
  
2.  Nella barra dei menu in Blocco note, scegliere **File**, **Salva**.  
  
3.  Nella finestra di dialogo **Salva con nome** selezionare **Tutti i file** dell'elenco a discesa **Salva come**.  
  
4.  Nella casella **Nome file** digitare data.xml.  
  
5.  Selezionare una cartella qualsiasi tramite il pulsante **Sfoglia cartelle**, quindi fare clic sul pulsante **Salva**.  
  
6.  In Visual Studio, selezionare il pulsante **F5**.  
  
     Verrà aperto il sito di SharePoint.  
  
7.  Scegliere **Altre opzioni** dal menu **Azioni sito**.  
  
8.  Nella pagina **Crea**, scegliere il tipo **Pagina Web Part**, quindi fare click sul pulsante **Crea**.  
  
9. Nella pagina **Nuova pagina Web Part**, denominare la pagina **SampleWebPartPage.aspx**, quindi fare click sul pulsante **Crea**.  
  
     Verrà visualizzata la pagina web part.  
  
10. Selezionare un'area qualsiasi nella pagina web part.  
  
11. All'inizio della pagina scegliere la scheda **Inserisci**, quindi fare clic sul pulsante **Web part**.  
  
12. Nel riquadro **Categorie** fare clic sulla cartella **Personalizzata**, selezionare la Web Part **WebPart1**, quindi fare click sul pulsante **Aggiungi**.  
  
     La web part verrà visualizzata nella pagina.  
  
## Test della proprietà personalizzata  
 Per popolare la griglia dati visualizzata nella web part, specificare il percorso del file XML che contiene dati relativi a ogni dipendente.  
  
#### Per testare la proprietà personalizzata  
  
1.  Scegliere la freccia visualizzata a destra della Web Part e selezionare **Modificare la Web part** dal menu visualizzato.  
  
     Sul lato destro della pagina verrà visualizzato un riquadro contenente le proprietà della web part.  
  
2.  Nel riquadro espandere il nodo **Varie**, digitare il percorso del file XML creato precedentemente e fare clic su **Applica**, quindi selezionare **OK**.  
  
     Verificare che nella web part venga visualizzato un elenco di dipendenti.  
  
## Test del verbo della web part  
 Visualizzare e nascondere i dipendenti che non sono manager facendo clic su un elemento presente nel menu dei verbi della web part.  
  
#### Per testare il verbo della web part  
  
1.  Scegliere la freccia visualizzata a destra della Web Part e selezionare **Mostra solo amministratori** dal menu visualizzato.  
  
     Nella web part verranno visualizzati solo dipendenti con il ruolo di manager.  
  
2.  Scegliere nuovamente la freccia e fare click su **Mostra tutti i dipendenti** dal menu visualizzato.  
  
     Nella web part verranno visualizzati tutti i dipendenti.  
  
## Vedere anche  
 [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Procedura: creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Procedura: creare una web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procedura dettagliata: creazione di una web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  