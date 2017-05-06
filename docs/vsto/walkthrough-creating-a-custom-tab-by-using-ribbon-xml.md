---
title: "Procedura dettagliata: creazione di una scheda personalizzata utilizzando l&#39;elemento XML della barra multifunzione"
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
  - "scheda personalizzata [sviluppo per Office in Visual Studio]"
  - "personalizzazione della barra multifunzione, tabscustom (barra multifunzione), schede"
  - "barra multifunzione [sviluppo per Office in Visual Studio], personalizzazione"
  - "barra multifunzione [sviluppo per Office in Visual Studio], schede"
  - "barra multifunzione [sviluppo per Office in Visual Studio], XML"
  - "XML [sviluppo per Office in Visual Studio], barra multifunzione"
ms.assetid: f6391a01-df1a-4a0f-bfbb-a9526c73b2b3
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Procedura dettagliata: creazione di una scheda personalizzata utilizzando l&#39;elemento XML della barra multifunzione
  Questa procedura dettagliata illustra come creare una scheda personalizzata della barra multifunzione usando l'elemento **Barra multifunzione \(XML\)**.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Aggiunta di pulsanti alla scheda **Componenti aggiuntivi**.  La scheda **Componenti aggiuntivi** è la scheda predefinita che viene definita nel file XML della barra multifunzione.  
  
-   Automazione di Microsoft Office Word usando i pulsanti nella scheda **Componenti aggiuntivi**.  
  
> [!NOTE]  
>  Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso.  La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi.  Per altre informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Creazione del progetto  
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Word.  Successivamente si personalizzerà la scheda **Componenti aggiuntivi** di questo documento.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto **Componente aggiuntivo per Word** denominato MyRibbonAddIn.  
  
     Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Tramite [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verrà aperto il file di codice **ThisAddIn.cs** o **ThisAddIn.vb** e il progetto **MyRibbonAddIn** in **Esplora soluzioni**.  
  
## Creazione della scheda Componenti aggiuntivi VSTO  
 Per creare la scheda **Componenti aggiuntivi** aggiungere un elemento **Barra multifunzione \(XML\)** al progetto.  Più avanti nella procedura dettagliata verranno aggiunti alcuni pulsanti a questa scheda.  
  
#### Per creare la scheda Componenti aggiuntivi  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione \(XML\)**.  
  
3.  Modificare il nome della nuova barra multifunzione in **MyRibbon** e quindi scegliere **Aggiungi**.  
  
     Nella finestra di progettazione verrà aperto il file **MyRibbon.cs** o **MyRibbon.vb**.  Verrà inoltre aggiunto al progetto un file XML denominato **MyRibbon.xml**.  
  
4.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ThisAddin.cs** o **ThisAddin.vb** e scegliere **Visualizza codice**.  
  
5.  Aggiungere il codice seguente alla classe **ThisAddIn**.  Questo codice esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce la classe XML della barra multifunzione all'applicazione Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **MyRibbonAddIn** e scegliere **Compila**.  Verificare che il progetto venga compilato senza errori.  
  
## Aggiunta di pulsanti alla scheda Componenti aggiuntivi  
 L'obiettivo di questo componente aggiuntivo VSTO consiste nell'offrire all'utente un modo per aggiungere testo standard e una tabella specifica al documento attivo.  Per fornire l'interfaccia utente, aggiungere due pulsanti alla scheda **Componenti aggiuntivi** modificando il file XML della barra multifunzione.  Più avanti nella procedura dettagliata verranno definiti i metodi di callback per i pulsanti.  Per altre informazioni sulla file XML della barra multifunzione, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
#### Per aggiungere pulsanti alla scheda Componenti aggiuntivi  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **MyRibbon.xml** e quindi scegliere **Apri**.  
  
2.  Sostituire il contenuto dell'elemento **tab** con i dati XML seguenti.  Tali dati XML modificano l'etichetta del gruppo di controlli predefinito su **Content** e aggiungono due nuovi pulsanti con le etichette **Insert Text** e **Insert Table**.  
  
    ```  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## Automazione del documento usando i pulsanti  
 È necessario aggiungere i metodi di callback `onAction` affinché i pulsanti **Insert Text** e **Insert Table** eseguano le azioni corrispondenti quando vengono scelti dall'utente.  Per altre informazioni sui metodi di callback per i controlli della barra multifunzione, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
#### Per aggiungere i metodi di callback per i pulsanti  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su**MyRibbon.cs** o **MyRibbon.vb** e quindi scegliere **Apri**.  
  
2.  Aggiungere il codice seguente all'inizio del file **MyRibbon.cs** o **MyRibbon.vb**.  Tramite questo codice viene creato un alias per lo spazio dei nomi <xref:Microsoft.Office.Interop.Word>.  
  
     [!code-csharp[Trin_RibbonButtons#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonButtons/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonButtons/VB/MyRibbon.vb#1)]  
  
3.  Aggiungere il metodo seguente alla classe `MyRibbon`.  Si tratta di un metodo di callback per il pulsante **Insert Text** che aggiunge una stringa al documento attivo nella posizione corrente del cursore.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#2)]  
  
4.  Aggiungere il metodo seguente alla classe `MyRibbon`.  Si tratta di un metodo di callback per il pulsante **Insert Table** che aggiunge una tabella al documento attivo nella posizione corrente del cursore.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#3)]  
  
## Test del componente aggiuntivo VSTO  
 Quando si esegue il progetto, nella barra multifunzione di Word viene visualizzata la scheda denominata **Componenti aggiuntivi**.  Fare clic sui pulsanti **Insert Text** e **Insert Table** nella scheda **Componenti aggiuntivi** per eseguire il test del codice.  
  
#### Per sottoporre a test il componente aggiuntivo VSTO  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Confermare che la scheda **Componenti aggiuntivi** sia visibile nella barra multifunzione.  
  
3.  Fare clic sulla scheda **Componenti aggiuntivi**.  
  
4.  Confermare che il gruppo **Content** sia visibile nella barra multifunzione.  
  
5.  Fare clic sul pulsante **Insert Text** nel gruppo **Content**.  
  
     Verrà aggiunta una stringa in corrispondenza della posizione corrente del cursore nel documento.  
  
6.  Fare clic sul pulsante **Insert Table** nel gruppo **Content**.  
  
     Verrà aggiunta una tabella in corrispondenza della posizione corrente del cursore nel documento.  
  
## Passaggi successivi  
 È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:  
  
-   Personalizzare la barra multifunzione di un'applicazione di Office diversa.  Per altre informazioni sulle applicazioni che supportano la personalizzazione della barra multifunzione, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).  
  
-   Personalizzare la barra multifunzione di un'applicazione di Office usando la finestra di progettazione della barra multifunzione.  Per altre informazioni, vedere [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md).  
  
-   Creare un riquadro azioni personalizzato.  Per altre informazioni, vedere [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md).  
  
-   Personalizzare l'interfaccia utente di Microsoft Office Outlook usando le aree del modulo di Outlook.  Per altre informazioni, vedere [Procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## Vedere anche  
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  