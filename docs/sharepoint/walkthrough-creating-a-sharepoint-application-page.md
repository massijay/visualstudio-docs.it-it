---
title: "Procedura dettagliata: creazione di una pagina di un&#39;applicazione SharePoint"
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
  - "pagine applicazione [sviluppo per SharePoint in Visual Studio], sviluppo"
  - "pagine applicazione [sviluppo per SharePoint in Visual Studio], creazione"
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Procedura dettagliata: creazione di una pagina di un&#39;applicazione SharePoint
  Una pagina applicazione è un formato specifico di una pagina ASP.NET.  Nelle pagine applicazione è presente contenuto di cui è stato eseguito il merge con una pagina master di SharePoint.  Per ulteriori informazioni, vedere [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 In questa procedura dettagliata viene illustrato come creare una pagina dell'applicazione ed eseguirne il debug tramite un sito di SharePoint locale.  In questa pagina vengono mostrati tutti gli elementi che ciascun utente ha creato o modificato in tutti i siti della server farm.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un progetto SharePoint.  
  
-   Aggiunta di una pagina applicazione al progetto SharePoint.  
  
-   Aggiunta di controlli ASP.NET alla pagina applicazione.  
  
-   Aggiunta di code\-behind ai controlli ASP.NET.  
  
-   Test della pagina applicazione.  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Windows e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] o un'edizione di Visual Studio Ultimate o Visual Studio Premium.  
  
## Creazione di un progetto SharePoint  
 Creare innanzitutto un **Progetto SharePoint vuoto**.  In un secondo momento, si aggiungerà un elemento **Pagina applicazione** a questo progetto.  
  
#### Per creare un progetto SharePoint  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Aprire la finestra di dialogo **Nuovo progetto**, espandere il nodo **Office\/SharePoint** sotto il linguaggio che si desidera utilizzare, quindi scegliere il nodo **Soluzioni di SharePoint**.  
  
3.  Nel riquadro **Modelli Visual Studio installati** scegliere il modello **SharePoint 2010 – Progetto vuoto**.  Assegnare il nome MySharePointProject al progetto, quindi selezionare il pulsante **OK**.  
  
     Verrà visualizzata la **Personalizzazione guidata SharePoint**.  Questa procedura guidata consente di selezionare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.  
  
4.  Selezionare il pulsante di opzione **Distribuisci come soluzione farm**, quindi fare clic sul pulsante **Fine** per accettare il sito di SharePoint locale predefinito.  
  
## Creazione di una pagina applicazione  
 Per creare una pagina applicazione aggiungere un elemento **Pagina applicazione** al progetto.  
  
#### Per creare una pagina applicazione  
  
1.  In **Esplora soluzioni** scegliere il progetto **MySharePointProject**.  
  
2.  Nella barra dei menu, scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
3.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare il modello **Pagina Applicazione \(solo soluzione Farm\)**.  
  
4.  Denominare la pagina SearchItems, quindi selezionare il pulsante **Aggiungi**.  
  
     Nella finestra di progettazione di Visual Web Developer viene riprodotta la pagina applicazione nella visualizzazione **Origine**, dove è possibile esaminarne gli elementi HMTL.  Nella finestra di progettazione è possibile visualizzare il markup per diversi controlli <xref:System.Web.UI.WebControls.Content>.  Ogni controllo è associato a un controllo <xref:System.Web.UI.WebControls.ContentPlaceHolder> definito nella pagina master dell'applicazione predefinita.  
  
## Progettazione del layout della pagina applicazione  
 L'elemento Pagina applicazione consente di utilizzare una finestra di progettazione per aggiungere controlli ASP.NET alla pagina applicazione.  Questa finestra di progettazione è la stessa utilizzata in Visual Web Developer.  Aggiungere un'etichetta, un elenco di pulsanti di opzione e una tabella alla visualizzazione **Origine** della finestra di progettazione, quindi impostare le proprietà come per la progettazione di qualsiasi pagina ASP.NET standard.  
  
 Per ulteriori informazioni sull'utilizzo della finestra di progettazione in Visual Web Developer, vedere [Visual Studio Web Development Content Map](http://msdn.microsoft.com/it-it/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
#### Per progettare il layout della pagina applicazione  
  
1.  Nella barra dei menu, scegliere **Visualizza**, **Casella degli strumenti**.  
  
2.  Nel nodo standard della **Casella degli strumenti** eseguire una delle operazioni seguenti:  
  
    -   Aprire il menu di scelta rapida per l'elemento **Etichetta**, scegliere **Copia**, aprire il menu di scelta rapida per la riga sotto il controllo **PlaceHolderMain** nella finestra di progettazione, quindi scegliere **Incolla**.  
  
    -   Trascinare l'elemento **Etichetta** dalla **Casella degli strumenti** nel corpo del controllo contenuto **PlaceHolderMain**.  
  
3.  Ripetere il passaggio precedente per aggiungere un elemento **DropDownList** e un elemento **Table** al controllo contenuto **PlaceHolderMain**.  
  
4.  Nella finestra di progettazione modificare il valore dell'attributo `Text` del controllo Label in Mostra tutti gli elementi.  
  
5.  Nella finestra di progettazione sostituire l'elemento `<asp:DropDownList>` con l'XML riportato di seguito.  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## Gestione degli eventi dei controlli nella pagina  
 Per gestire i controlli in una pagina applicazione, procedere come per una qualsiasi pagina ASP.NET.  In questa procedura verrà gestito l'evento `SelectedIndexChanged` dell'elenco a discesa.  
  
#### Per gestire gli eventi dei controlli nella pagina  
  
1.  Nel menu **Visualizza**, scegliere **Codice**.  
  
     Il file di codice della pagina applicazione verrà aperto nell'editor di codice.  
  
2.  Aggiungere il seguente metodo alla classe `SearchItems`.  Questo codice gestisce l'evento <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> di <xref:System.Web.UI.WebControls.DropDownList> chiamando un metodo che verrà creato più avanti in questa procedura dettagliata.  
  
     [!code-csharp[SP_ApplicationPage#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]
     [!code-vb[SP_ApplicationPage#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]  
  
3.  Aggiungere le seguenti istruzioni all'inizio del file di codice della pagina applicazione.  
  
     [!code-csharp[SP_ApplicationPage#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]
     [!code-vb[SP_ApplicationPage#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]  
  
4.  Aggiungere il seguente metodo alla classe `SearchItems`.  Questo metodo scorre tutti i siti nella server farm e ricerca gli elementi creati o modificati dall'utente corrente.  
  
     [!code-csharp[SP_ApplicationPage#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]
     [!code-vb[SP_ApplicationPage#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]  
  
5.  Aggiungere il seguente metodo alla classe `SearchItems`.  Questo metodo visualizza gli elementi creati o modificati dall'utente corrente nella tabella.  
  
     [!code-csharp[SP_ApplicationPage#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]
     [!code-vb[SP_ApplicationPage#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]  
  
## Test della pagina dell'applicazione  
 Quando si esegue il progetto viene aperto il sito di SharePoint e viene visualizzata la pagina applicazione.  
  
#### Per testare la pagina dell'applicazione  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per la pagina dell'applicazione, quindi scegliere **Imposta elemento di avvio**.  
  
2.  Premere il tasto F5.  
  
     Verrà aperto il sito di SharePoint.  
  
3.  Nella pagina dell'applicazione, scegliere l'opzione **Modified by me**.  
  
     La pagina applicazione verrà aggiornata e saranno visualizzati tutti gli elementi modificati dall'utente in tutti i siti della server farm.  
  
4.  Nella pagina applicazione, selezionare **Creati dall'utente** dall'elenco.  
  
     La pagina applicazione verrà aggiornata e verranno visualizzati tutti gli elementi creati dall'utente in tutti i siti della server farm.  
  
## Passaggi successivi  
 Per ulteriori informazioni sulle pagine dell'applicazione di SharePoint, vedere [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Per ulteriori informazioni su come progettare il contenuto delle pagine di SharePoint tramite Visual Web Designer, consultare gli argomenti seguenti:  
  
-   [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## Vedere anche  
 [Procedura: creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md)   
 [Tipo di pagina applicazione \_layouts](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  