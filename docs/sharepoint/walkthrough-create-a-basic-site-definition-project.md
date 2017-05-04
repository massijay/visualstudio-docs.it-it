---
title: "Procedura dettagliata: Creare un progetto di definizione di sito di base | Microsoft Docs"
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
  - "sviluppo per SharePoint in Visual Studio, definizioni di sito"
  - "definizioni di sito [sviluppo per SharePoint in Visual Studio]"
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Procedura dettagliata: Creare un progetto di definizione di sito di base
  In questa procedura dettagliata viene illustrato come creare una definizione di sito di base in cui è contenuta una web part visiva e alcuni relativi controlli.  Per garantire una maggior chiarezza, la web part visiva creata dispone solo di alcuni controlli.  Tuttavia, è possibile creare definizioni di sito di SharePoint più sofisticate in cui sono incluse più funzionalità.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di una definizione di sito tramite il modello di progetto di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Creazione di un sito di SharePoint tramite l'utilizzo di una definizione di sito in SharePoint.  
  
-   Aggiunta di una web part visiva alla soluzione.  
  
-   Personalizzazione della pagina del sito default.aspx tramite l'aggiunta della nuova web part visiva.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint.  Per ulteriori informazioni, vedere Requisiti per lo sviluppo di soluzioni SharePoint.  
  
-   Visual Studio.  
  
## Creazione di una soluzione di definizione di sito  
 Creare il progetto di definizione di sito in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Per creare un progetto di definizione di sito  
  
1.  Sulla barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  Se l'IDE è configurato per utilizzare le impostazioni di sviluppo di Visual Basic, nella barra dei menu, scegliere **File**, **Nuovo progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
2.  Espandere il nodo **Visual C\#** o il nodo **Visual Basic**, espandere il nodo **SharePoint** quindi scegliere il nodo **2010**.  
  
3.  Nell'elenco **Modelli**, scegliere il modello **Progetto SharePoint 2010**.  
  
4.  Nella casella **Nome** immettere TestSiteDef, e quindi selezionare il pulsante **ApproveTimeOff**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
5.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug** immettere l'URL per il sito del server SharePoint in cui si desidera eseguire il debug della definizione di sito o utilizzare il percorso predefinito \(http:\/\/*System Name*\/\).  
  
6.  Nella sezione **Selezionare il livello di attendibilità per la soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come soluzione farm**.  
  
     Tutti i progetti di definizione di sito devono essere distribuiti come soluzioni della farm.  Per ulteriori informazioni sulle differenze tra le soluzioni create mediante sandbox e quelle della farm, vedere [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Fare clic sul pulsante **Fine**.  
  
     Il progetto viene visualizzato in **Esplora soluzioni**.  
  
8.  In **Esplora soluzioni** scegliere il nodo del progetto, quindi, nella barra dei menu scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
9. Sotto **Visual C\#** o **Visual Basic**, espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
10. Nel riquadro **Modelli**, scegliere il modello **Definizione di sito**, lasciare **Nome** come **SiteDefinition1** e quindi scegliere il pulsante **Aggiungi**.  
  
## Creare una web part visiva  
 Successivamente, creare una web part per visualizzare nella pagina principale della definizione di sito.  
  
#### Per creare una web part visiva  
  
1.  In **Esplora soluzioni**, selezionare il pulsante **Mostra tutti i file**.  
  
2.  Scegliere il nodo del progetto **SiteDefinition1**, quindi sulla barra dei menu, scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
3.  Espandere il nodo **Visual C\#** o il nodo **Visual Basic**, espandere il nodo **SharePoint** quindi scegliere il nodo **2010**.  
  
4.  Nell'elenco di modelli, scegliere il modello **Web part visiva**, mantenere il nome predefinito VisualWebPart1 quindi scegliere il pulsante **Aggiungi**.  
  
     Il file di VisualWebPart1.ascx viene aperto.  
  
5.  Nella parte inferiore di VisualWebPart1UserControl.ascx, aggiungere il markup seguente per fornire tre controlli al form: una casella di testo, un pulsante e un'etichetta.  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  Sotto VisualWebPart1.ascx, aprire il file VisualWebPart1.ascx.cs \(per [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]\) o VisualWebPart1.ascx.vb \(per [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), quindi aggiungere il seguente codice:  
  
     [!code-csharp[SP_SimpleSiteDef#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_simplesitedef/cs/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_SimpleSiteDef#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_simplesitedef/vb/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
     Questo codice consente di aggiungere funzionalità per il clic sul pulsante della web part.  
  
## Aggiungere la web part visiva alla pagina ASPX predefinita  
 Aggiungere la web part visiva alla pagina ASPX predefinita della definizione di sito.  
  
#### Per aggiungere una web part visiva alla pagina ASPX predefinita  
  
1.  Aprire la pagina default.aspx e aggiungere la linea seguente sotto il tag `WebPartPages`:  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Questa riga consente di associare il nome MyWebPartControls alla web part e al codice.  Il parametro *Namespace* corrisponde allo spazio dei nomi utilizzato nel file di codice VisualWebPart1.ascx.  
  
2.  Dopo l'elemento `</asp:Content>`, sostituire tutta la sezione `ContentPlaceHolderId="PlaceHolderMain"` e il relativo contenuto con il seguente codice:  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Questo codice consente di creare un riferimento alla web part visiva creata precedentemente.  
  
3.  In **Esplora soluzioni** aprire il menu di scelta rapida del nodo **SiteDefinition1**, quindi scegliere **Imposta elemento di avvio**.  
  
## Distribuire ed eseguire la soluzione di definizione di sito  
 Successivamente, distribuire il progetto in SharePoint ed eseguire il progetto.  
  
#### Per distribuire ed eseguire la definizione di sito  
  
-   Nella barra dei menu ,scegliere **Compila**, **Distribuisci TestSiteDef**.  
  
-   Premere F5.  
  
     Visual Studio consente di compilare il codice, aggiungere le relative funzionalità, assemblare tutti i file in un file di soluzione SharePoint \(WSP\) e distribuire i file WSP per il server SharePoint.  Successivamente, tramite SharePoint, vengono installati i file e attivate le funzionalità.  
  
## Creare un sito basato sulla definizione di sito  
 Creare un sito tramite la nuova definizione di sito.  
  
#### Per creare un sito tramite la definizione di sito  
  
1.  Sul sito di SharePoint viene visualizzata la pagina Nuovo sito di SharePoint.  
  
2.  Nella sezione **Titolo e descrizione** immettere Nuovo sito per il titolo e una descrizione del sito.  
  
3.  Nella sezione **Indirizzo sito Web** immettere nuovosito nella casella **Nome URL**.  
  
4.  Nella sezione **Modello**, scegliere la scheda **Personalizzazioni di SharePoint**.  
  
5.  Nell'elenco **Seleziona un modello**, scegliere **SiteDefinition1**.  
  
6.  Mantenere i valori predefiniti delle altre impostazioni, selezionare il pulsante **Crea**.  
  
     Viene visualizzato il nuovo sito.  
  
## Testare il nuovo sito  
 Testare il nuovo sito per verificare il corretto funzionamento.  
  
#### Per testare il nuovo sito  
  
-   Nella pagina predefinita ASPX, inserire un testo e selezionare il pulsante **Modifica testo dell'etichetta** accanto alla casella di testo.  
  
     Il testo viene visualizzato nell'etichetta sul lato destro del pulsante.  
  
## Vedere anche  
 [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  