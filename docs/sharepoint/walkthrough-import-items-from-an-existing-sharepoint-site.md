---
title: "Procedura dettagliata: importare gli elementi da un sito di SharePoint esistente"
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
  - "importazione di elementi [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, importazione di elementi"
ms.assetid: faac3309-88d7-4fb2-8392-feda07fc00e5
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Procedura dettagliata: importare gli elementi da un sito di SharePoint esistente
  In questa procedura dettagliata viene illustrato come importare elementi da un sito di SharePoint esistente in un progetto SharePoint per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Personalizzazione di un sito di SharePoint tramite l'aggiunta di una colonna del sito personalizzata \(nota anche come *campo*\).  
  
-   Esportazione di un sito di SharePoint in un file con estensione wsp.  
  
-   Importazione del file con estensione wsp in SharePoint per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tramite il progetto di importazione del file con estensione wsp.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Personalizzazione di un sito di SharePoint  
 In questo esempio si creerà e personalizzerà un sito secondario di SharePoint aggiungendovi una nuova colonna e creando un altro sito secondario da utilizzare in un secondo momento.  Successivamente, si esporterà il primo sito secondario in un file con estensione wsp, quindi si importerà la colonna del sito personalizzata nel secondo sito secondario tramite il progetto di importazione del file con estensione wsp.  
  
#### Per creare e personalizzare un sito di SharePoint  
  
1.  Aprire un sito di SharePoint tramite un browser, come ad esempio http:\/\/*system name*\/SitePages\/Home.aspx.  
  
2.  Creare un sito secondario del sito principale di SharePoint aprendo il menu **Nuovo sito** e selezionando **Nuovo sito**.  
  
3.  Nella finestra di dialogo **Crea** del sito, selezionare il tipo **Sito vuoto**.  
  
4.  Nella casella **Titolo** immettere "Prova colonna sito 1"; nella casella **Nome URL** immettere columntest1: lasciare le altre impostazioni sui valori predefiniti; quindi selezionare il pulsante **Crea**.  
  
5.  Una volta creato il sito, spostarsi nel browser nel sito principale, http:\/\/*system name*\/SitePages\/Home.aspx.  
  
6.  Nuovamente, creare di nuovo un sito secondario vuoto dal sito di SharePoint principale aprendo il menu **Azioni sito**, selezionando **Nuovo sito** e quindi selezionando il tipo **Sito vuoto**.  
  
7.  Nella casella **Titolo** immettere "Prova colonna sito 2", nella casella **Nome URL** immettere columntest2: lasciare le altre impostazioni sui valori predefiniti; quindi selezionare il pulsante **Crea**.  
  
8.  Tornare al primo sito secondario, http:\/\/*SystemName*\/columntest1\/default.aspx.  
  
9. Nel menu **Azioni sito**, selezionare **Impostazioni sito** per visualizzare la pagina delle impostazioni del sito.  
  
10. Nella sezione **Raccolta**, selezionare il collegamento **Colonne del sito**.  
  
11. Nella parte superiore della pagina **Raccolta colonne del sito**, selezionare il pulsante **Crea**.  
  
12. Nella casella **Nome colonna**, immettere la colonna di prova, mantenere gli altri valori predefiniti e quindi scegliere il pulsante **OK**.  
  
13. La colonna **Colonna di prova** viene visualizzata sotto l'intestazione Colonne personalizzate in Raccolta colonne del sito.  
  
## Esportazione del sito di SharePoint  
 Ottenere un file di installazione \(con estensione wsp\) di SharePoint in cui sono contenuti gli elementi di SharePoint e ciò che si desidera importare nel progetto SharePoint per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Se non si dispone già di un file con estensione wsp, è necessario crearne uno da un sito di SharePoint esistente.  In questo esempio si esporterà il sito di SharePoint predefinito in un file con estensione wsp.  
  
> [!IMPORTANT]  
>  Se durante l'esecuzione della procedura seguente si riceve un errore di runtime è necessario eseguirla su un sistema che dispone dell'accesso al sito di SharePoint.  
  
#### Per esportare un sito di SharePoint esistente  
  
1.  Nel sito SharePoint, selezionare **Impostazioni sito** nella scheda **Azioni sito** per visualizzare la pagina impostazioni sito.  
  
2.  Nella sezione **Azioni sito** nella pagina Impostazioni sito, selezionare il collegamento **Salva sito come modello**.  
  
3.  Nella casella **Nome file** immettere ExampleSite e nella casella **Nome modello** immettere Sito di esempio.  
  
4.  In questo esempio lasciare deselezionata la casella di controllo **Includi contenuto**.  
  
     Se questa casella viene selezionata, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente di salvare tutti gli elenchi, le raccolte documenti e il relativo contenuto nel file con estensione wsp.  Nonostante si riveli utile in alcune circostanze, tale opzione non è richiesta in questo esempio.  
  
5.  Una volta terminata correttamente l'operazione, selezionare il collegamento **raccolta di soluzioni** per visualizzare il file con estensione .wsp.  
  
     Per visualizzare in un secondo momento la pagina della raccolta di soluzioni, aprire il menu **Azioni sito**, selezionare **Impostazioni sito**, scegliere il collegamento **Vai alle impostazioni del sito principale** nella sezione **Amministrazione raccolta siti** e quindi selezionare il collegamento **Soluzioni** nella sezione **Raccolte**.  
  
6.  Nella raccolta di soluzioni, scegliere il collegamento **ExampleSite**.  
  
7.  Nella finestra di dialogo **Download del file**, scegliere il pulsante **Salva** per salvare il file nel sistema locale, per impostazione predefinita, nella cartella di download.  
  
## Importazione del file con estensione wsp  
 Ora che si dispone di un file con estensione wsp in cui è contenuto un elemento che si desidera riutilizzare \(la colonna del sito personalizzata Colonna di prova\), importare il file con estensione wsp per accedevi.  
  
#### Per importare un file con estensione  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sulla barra dei menu, scegliere **File**, **Nuovo**, **Progetto** per visualizzare la finestra di dialogo **Nuovo progetto**.  Se l'IDE è configurato per utilizzare le impostazioni di sviluppo di Visual Basic, nella barra dei menu, scegliere **File**, **Nuovo progetto**.  
  
2.  Espandere il nodo **SharePoint** sotto **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **2010**.  
  
3.  Selezionare il modello **Importa pacchetto di soluzione SharePoint 2010** nel riquadro **Modelli**, mantenere il nome del progetto WspImportProject1, quindi scegliere il pulsante **OK**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
4.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug** immettere l'[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] per il secondo sito secondario di SharePoint che è stato creato precedentemente.  Aggiunto il nuovo elemento del campo personalizzato, http:\/\/*system name*\/columntest2, a tale sito secondario.  
  
5.  Nella sezione **Selezionare il livello di attendibilità per la soluzione SharePoint** lasciare la selezione **Distribuisci come soluzione creata mediante sandbox**.  
  
6.  Nella pagina **Specificare l'origine del nuovo progetto** individuare il percorso nel sistema in cui è stato salvato precedentemente il file con estensione wsp, quindi selezionare il pulsante **Avanti**.  
  
    > [!NOTE]  
    >  Se si sceglie il pulsante **Fine** in questa pagina, vengono importati tutti gli elementi disponibili nel file con estensione .wsp.  
  
7.  Nella casella **Selezionare gli elementi da importare** deselezionare tutti gli elementi nell'elenco delle caselle di controllo tranne **Colonna di prova**, scegliere quindi il pulsante **Fine**.  
  
     Poiché l'elenco contiene molti elementi, è possibile premere la combinazione di tasti Ctrl\+A per selezionare tutti gli elementi nell'elenco, premere la barra spaziatrice per rimuovere tutte le caselle di controllo e selezionare solo la casella di controllo accanto all'elemento **Colonna di test**.  
  
     Una volta terminata l'operazione di importazione, viene creato un nuovo progetto definito **WspImportProject1** in cui è contenuta una cartella denominata **Campi**.  In questa cartella sono presenti la colonna del sito personalizzata **Colonna di prova** e il relativo file di definizione Elements.xml.  
  
## Distribuzione del progetto  
 Distribuire **WspImportProject1** nel secondo sito secondario di SharePoint creato precedentemente per visualizzare la colonna del sito personalizzata.  
  
#### Per distribuire il progetto  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] premere il tasto F5 per distribuire ed eseguire il progetto di importazione del file con estensione .wsp.  
  
2.  Nel sito di SharePoint, aprire il menu **Azioni sito** quindi scegliere **Impostazioni sito** per visualizzare la pagina impostazioni sito.  
  
3.  Nella sezione **Raccolta**, selezionare il collegamento **Colonne del sito**.  
  
4.  Scorrere verso il basso fino alla sezione **Colonne personalizzate**.  
  
     Notare che la colonna del sito personalizzata importata dal primo sito di SharePoint viene visualizzata nell'elenco.  
  
## Vedere anche  
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  