---
title: "Walkthrough: Extending a SharePoint Project Item Type | Microsoft Docs"
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
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 1cea4e0f-ce33-4cd7-a664-800184865456
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Walkthrough: Extending a SharePoint Project Item Type
  È possibile utilizzare l'elemento del progetto **Modello di integrazione applicativa dei dati** per creare un modello per il servizio Integrazione applicativa dei dati \(BDC, Business Data Connectivity\) in SharePoint.  Per impostazione predefinita, quando si crea un modello tramite questo elemento di progetto, i dati nel modello non vengono visualizzati agli utenti.  Per cambiare questa condizione, è necessario creare anche un elenco esterno in SharePoint.  
  
 In questa procedura dettagliata verrà creata un'estensione per l'elemento di progetto **Modello di integrazione applicativa dei dati**.  Gli sviluppatori possono utilizzare l'estensione per creare un elenco esterno nel progetto che consenta di visualizzare i dati nel modello BDC.  In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che esegue due attività principali:  
  
    -   Genera un elenco esterno che visualizza i dati in un modello BDC.  L'estensione utilizza il modello a oggetti affinché il sistema di progetto SharePoint generi un file Elements.xml che definisce l'elenco.  Inoltre aggiunge il file al progetto in modo che venga distribuito insieme al modello BDC.  
  
    -   Aggiunge una voce di menu di scelta rapida agli elementi di progetto **Modello di integrazione applicativa dei dati** in **Esplora soluzioni**.  Gli sviluppatori possono fare clic su questa voce di menu per generare un elenco esterno per il modello BDC.  
  
-   Compilazione di un pacchetto Visual Studio Extension \(VSIX\) per distribuire l'assembly delle estensioni.  
  
-   Test dell'estensione.  
  
## Prerequisiti  
 Per completare la procedura dettagliata, nel computer di sviluppo devono essere presenti i componenti elencati di seguito:  
  
-   Edizioni supportate di Microsoft Windows, SharePoint e Visual Studio.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Campo [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  In questa procedura dettagliata viene utilizzato il modello **VSIX Project** di SDK per creare un pacchetto VSIX e distribuire l'elemento di progetto.  Per ulteriori informazioni, vedere [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Per completare la procedura dettagliata è consigliabile conoscere i concetti riportati di seguito:  
  
-   Servizio BDC in [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)].  Per ulteriori informazioni, vedere [BDC Architecture](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   XML Schema per i modelli BDC.  Per ulteriori informazioni, vedere [BDC Model Infrastructure](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## Creazione dei progetti  
 Per completare questa procedura dettagliata è necessario creare due progetti:  
  
-   Un progetto VSIX per creare il pacchetto VSIX allo scopo di distribuire l'estensione di elemento di progetto.  
  
-   Un progetto Libreria di classi che implementa l'estensione di elemento di progetto.  
  
 Iniziare la procedura dettagliata creando i progetti.  
  
#### Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu, scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **Estendibilità**.  
  
    > [!NOTE]  
    >  Il nodo **Estendibilità** è disponibile solo se si installa Visual Studio SDK.  Per ulteriori informazioni, vedere la sezione precedente relativa ai prerequisiti.  
  
4.  Nella lista nella parte superiore della finestra di dialogo **Nuovo progetto**, scegliere **.NET Framework 4.5**.  
  
     Le estensioni degli strumenti di SharePoint richiedono alcune funzionalità di questa versione di .NET Framework.  
  
5.  Selezione del modello **VSIX Project**.  
  
6.  Nella casella di testo **Nome**, immettere **GenerateExternalDataLists**, quindi scegliere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **GenerateExternalDataLists** a **Esplora soluzioni**.  
  
7.  Se il file source.extension.vsixmanifest non viene visualizzato automaticamente, aprire il menu di scelta rapida nel progetto GenerateExternalDataLists e scegliere **Apri**  
  
8.  Verificare che il file source.extension.vsixmanifest dispone di una voce da spazio vuoto \(immettere Contoso\) per il campo Autore, salvare e chiudere il file.  
  
#### Per creare il progetto di estensione  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo soluzione **GenerateExternalDataLists**, scegliere **Aggiungi**, quindi scegliere **Nuovo Progetto**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic, il nodo della soluzione viene visualizzato in **Esplora soluzioni** solo quando la casella di controllo **Mostra sempre soluzione** viene selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Nella finestra di dialogo **Aggiungi nuovo progetto** espandere i nodi **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **Windows**.  
  
3.  Nella lista nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5**.  
  
4.  Nell'elenco dei modelli di progetto scegliere **Libreria di classi**.  
  
5.  Nella casella di testo **Nome**, immettere **BdcProjectItemExtension**, quindi scegliere il pulsante **OK**.  
  
     In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il progetto **BdcProjectItemExtension** viene aggiunto alla soluzione e viene aperto il file di codice predefinito Class1.  
  
6.  Eliminare il file di codice Class1 dal progetto.  
  
## Configurazione del progetto di estensione  
 Prima di scrivere codice per creare l'estensione di elemento del progetto, aggiungere al progetto di estensione file di codice e riferimenti all'assembly.  
  
#### Per configurare il progetto  
  
1.  Nel progetto BdcProjectItemExtension aggiungere due file di codice con i nomi seguenti:  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Scegliere il progetto BdcProjectItemExtension, quindi, nella barra dei menu, scegliere **Progetto**, **Aggiungi riferimento**.  
  
3.  Nel nodo **Assembly**, selezionare il nodo **Framework** e selezionare la casella di controllo per ognuno degli assembly seguenti:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  Nel nodo **Assembly**, selezionare il nodo **Estensioni** quindi selezionare la casella di controllo del seguente assembly:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Scegliere il pulsante **OK**.  
  
## Definizione dell'estensione dell'elemento di progetto  
 Creare una classe che definisce l'estensione per l'elemento di progetto **Modello di integrazione applicativa dei dati**.  Per definire l'estensione, la classe implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Implementare questa interfaccia tutte le volte che si desidera estendere un tipo esistente di elemento di progetto.  
  
#### Per definire l'estensione dell'elemento di progetto  
  
1.  Inserire il seguente codice nel file di codice ProjectItemExtension.  
  
    > [!NOTE]  
    >  Dopo aver aggiunto questo codice, il progetto presenterà alcuni errori di compilazione  che scompariranno quando si aggiunge codice nei passaggi successivi.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## Creazione di elenchi di dati esterni  
 Aggiungere una definizione parziale della classe `GenerateExternalDataListsExtension` che crea un elenco di dati esterni per ogni entità nel modello BDC.  Per creare l'elenco di dati esterni, questo codice innanzitutto legge i dati di entità nel modello BDC analizzando i dati XML nel file del modello BDC.  Successivamente, crea un'istanza di elenco basata sul modello BDC e la aggiunge al progetto.  
  
#### Per creare gli elenchi di dati esterni  
  
1.  Inserire il seguente codice nel file di codice GenerateExternalDataLists.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/generateexternaldatalists.cs#2)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/generateexternaldatalists.vb#2)]  
  
## Verifica  
 In questa fase della procedura dettagliata, tutto il codice per l'estensione dell'elemento di progetto si trova nel progetto.  Compilare la soluzione per assicurarsi che il progetto venga compilato correttamente.  
  
#### Per compilare la soluzione  
  
1.  Nella barra dei menu, scegliere **Compilazione**, **Compila soluzione**.  
  
## Creazione di un pacchetto VSIX per distribuire l'estensione dell'elemento di progetto  
 Per distribuire l'estensione, utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX.  Anzitutto, configurare il pacchetto VSIX modificando il file source.extension.vsixmanifest incluso nel progetto VSIX.  Successivamente, creare il pacchetto VSIX compilando la soluzione.  
  
#### Per configurare e creare il pacchetto VSIX  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del file source.extension.vsixmanifest nel progetto GenerateExternalDataLists, quindi scegliere **Apri**.  
  
     Visual Studio consente di aprire il file nell'editor del manifesto.  Il file source.extension.vsixmanifest è la base del file extension.vsixmanifest richiesto da tutti i pacchetti VSIX.  Per ulteriori informazioni su questo file, vedere [Informazioni di riferimento sullo schema dell'estensione VSIX](http://msdn.microsoft.com/it-it/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nella casella **Nome prodotto**, immettere **Generatore Elenco Dati Esterno**.  
  
3.  Nella casella **Autore**, inserire **Contoso**.  
  
4.  Nella casella **Descrizione**, immettere **Un'estensione per gli elementi del progetto Business Data Connectivity Model che può essere usata per generare elenchi di dati esterni**.  
  
5.  Nella scheda **Assets** dell'editor, scegliere il pulsante **Nuovo**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo Asset**.  
  
6.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde all'elemento `MefComponent` del file extension.vsixmanifest.  Questo elemento specifica il nome di un assembly dell'estensione nel pacchetto VSIX.  Per ulteriori informazioni, vedere [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Nell'elenco **Origine**, scegliere **Un progetto nella soluzione corrente**.  
  
8.  Nell'elenco **Progetto**, scegliere **BdcProjectItemExtension**, quindi scegliere il pulsante **OK**.  
  
9. Nella barra dei menu, scegliere **Compilazione**, **Compila soluzione**.  
  
10. Compilare e generare il progetto assicurandosi che tali operazioni vengano eseguite correttamente.  
  
11. Verificare che la cartella di output di compilazione per il progetto GenerateExternalDataLists adesso contenga il file GenerateExternalDataLists.vsix.  
  
     Per impostazione predefinita, la cartella di output di compilazione è ..\\bin\\Debug all'interno della cartella che contiene i file di progetto.  
  
## Test dell'estensione dell'elemento di progetto  
 È ora possibile testare l'estensione dell'elemento di progetto.  Innanzitutto, avviare il debug del progetto di estensione nell'istanza sperimentale di Visual Studio.  Successivamente, utilizzare l'estensione nell'istanza sperimentale di Visual Studio per generare un elenco esterno per un modello di integrazione applicativa dei dati.  Infine, aprire l'elenco esterno sul sito di SharePoint per verificare che funzioni nel modo previsto.  
  
#### Per avviare il debug dell'estensione  
  
1.  Se necessario, riavviare Visual Studio con credenziali amministrative e aprire quindi la soluzione GenerateExternalDataLists.  
  
2.  Nel progetto BdcProjectItemExtension, aprire il file di codice ProjectItemExtension e aggiungere un punto di interruzione alla riga di codice nel metodo `Initialize`.  
  
3.  Aprire il file di codice GenerateExternalDataLists e quindi aggiungere un punto di interruzione alla prima riga di codice nel metodo `GenerateExternalDataLists_Execute`.  
  
4.  Avviare il debug con il tasto F5 o, sulla barra dei menu, scegliendo **Debug**, **Avvia Debug**.  
  
     In Visual Studio i file di estensione vengono installati in %UserProfile%\\Dati applicazione\\Locale\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\External Data List Generator\\1.0 e viene avviata un'istanza sperimentale di Visual Studio.  L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### Per testare l'estensione  
  
1.  Nell'istanza sperimentale di Visual Studio, nella barra del menu, scegliere **File**, **Nuovo**, quindi fare clic su **Progetto**.  
  
2.  Nel finestra di dialogo **Nuovo progetto**, espandere il nodo **Modelli**, espandere il nodo **Visual C\#**, espandere il nodo **SharePoint**, quindi scegliere **2010**.  
  
3.  Nella lista nella parte superiore della finestra di dialogo, assicurarsi che sia selezionata l'opzione **.NET Framework 3.5**.  I progetti per [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] richiedono questa versione di .NET Framework.  
  
4.  Nell'elenco dei modelli di progetto fare clic su **Progetto SharePoint 2010**.  
  
5.  Nella casella di testo **Nome** immettere **SharePointProjectTestBDC**, quindi scegliere il pulsante **OK**.  
  
6.  Nella personalizzazione guidata SharePoint, immettere l'URL del sito che si desidera utilizzare per il debug, quindi scegliere **Distribuisci come soluzione farm** quindi scegliere il pulsante **Fine**.  
  
7.  Aprire il menu di scelta rapida per il progetto SharePointProjectTestBDC, scegliere **Aggiungi** e quindi selezionare **Nuovo elemento**.  
  
8.  Nella finestra di dialogo **Aggiungi NewItem – SharePointProjectTestBDC**, espandere il nodo installato di linguaggio, espandere il nodo **SharePoint**.  
  
9. Scegliere il nodo **2010** quindi scegliere il modello **Modello di integrazione applicativa dei dati \(solo soluzione farm\)**.  
  
10. Nella casella **Nome**, immettere **TestBDCModel**, quindi scegliere il pulsante **Aggiungi**.  
  
11. Verificare che il codice nell'altra istanza di Visual Studio venga interrotto in corrispondenza del punto di interruzione impostato precedentemente nel metodo `Initialize` del file di codice ProjectItemExtension.  
  
12. Nell'istanza interrotta di Visual Studio, scegliere il tasto **F5**, o nella barra dei menu, scegliere **Debug**, **Continua** per continuare il debug del progetto.  
  
13. Nell'istanza sperimentale di Visual Studio, scegliere il tasto **F5**, o, sulla barra dei menu, scegliere **Debug**, **Avvia debug** per compilare, distribuire ed eseguire il progetto **TestBDCModel**.  
  
     Nel browser web viene visualizzata la pagina predefinita del sito di SharePoint specificata per il debug.  
  
14. Verificare che la sezione **Elenchi** nell'area Avvio veloce non contenga ancora un elenco basato sul modello BDC predefinito del progetto.  È necessario innanzitutto creare un elenco di dati esterni mediante l'interfaccia utente di SharePoint o l'estensione dell'elemento di progetto.  
  
15. Chiudere il browser web.  
  
16. Nell'istanza di Visual Studio in cui è aperto il progetto TestBDCModel, aprire il menu di scelta rapida del nodo **TestBDCModel** in **Esplora soluzioni**, quindi scegliere **Generate External Data List**.  
  
17. Verificare che il codice nell'altra istanza di Visual Studio venga interrotto in corrispondenza del punto di interruzione impostato precedentemente nel metodo `GenerateExternalDataLists_Execute`.  Scegliere il tasto **F5**, o, sulla barra dei menu, scegliere **Debug**, **Continua** per continuare il debug del progetto.  
  
18. Nell'istanza sperimentale di Visual Studio viene aggiunta un'istanza di elenco denominata **Entity1DataList** al progetto TestBDCModel e l'istanza genera anche una funzionalità denominata **Feature2** per l'istanza di elenco.  
  
19. Scegliere il tasto **F5**, o, sulla barra dei menu, scegliere **Debug**, **Avvia debug** per compilare, distribuire ed eseguire il progetto TestBDCModel.  
  
     Nel browser web viene visualizzata la pagina predefinita del sito di SharePoint utilizzata per il debug.  
  
20. Nella sezione **Elenchi** dell'area Avvio Veloce, scegliere l'elenco **Entity1DataList**.  
  
21. Verificare che nell'elenco siano contenute le colonne denominate Identifier1 e Message, nonché un elemento con il valore Identifier1 pari a 0 e il valore Message pari a Hello World.  
  
     Il modello di progetto **Business Data Connectivity Model** genera il modello BDC predefinito che fornisce tutti questi dati.  
  
22. Chiudere il browser web.  
  
## Pulizia del computer di sviluppo  
 Dopo aver completato il test dell'estensione dell'elemento di progetto, rimuovere l'elenco esterno e il modello BDC dal sito di SharePoint, nonché l'estensione dell'elemento di progetto da Visual Studio.  
  
#### Per rimuovere l'elenco di dati esterni dal sito di SharePoint  
  
1.  Nell'area Avvio veloce del sito di SharePoint scegliere l'elenco **Entity1DataList**.  
  
2.  Nella barra multifunzione del sito di SharePoint scegliere la scheda **Elenco**.  
  
3.  Nel gruppo **Impostazioni** della scheda **Elenco**, scegliere **Impostazioni elenco**.  
  
4.  In **Autorizzazioni e gestione**, scegliere **Elimina l'elenco**, quindi scegliere **OK** per confermare che si desidera spostare l'elenco nel cestino.  
  
5.  Chiudere il browser web.  
  
#### Per rimuovere il modello BDC dal sito di SharePoint  
  
1.  Scegliere **Ritrai** dal menu **Compila** nell'istanza sperimentale di Visual Studio.  
  
     Visual Studio rimuove il modello di integrazione applicativa dei dati dal sito di SharePoint.  
  
#### Per rimuovere l'estensione dell'elemento di progetto da Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, nella barra del menu, scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco di estensioni, scegliere **External Data List Generator**, quindi scegliere il pulsante **Disinstalla**.  
  
3.  Nella finestra di dialogo visualizzata, scegliere **Sì** per confermare che si desidera disinstallare l'estensione.  
  
4.  Scegliere **Riavvia adesso** per completare la disinstallazione.  
  
5.  Chiudere entrambe le istanze di Visual Studio \(ovvero quella sperimentale e l'istanza in cui è aperta la soluzione GenerateExternalDataLists\).  
  
## Vedere anche  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  