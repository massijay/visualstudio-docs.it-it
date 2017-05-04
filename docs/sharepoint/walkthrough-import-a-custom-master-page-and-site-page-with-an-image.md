---
title: "Procedura dettagliata: importazione di una pagina master personalizzata e di una pagina del sito con un&#39;immagine | Microsoft Docs"
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
  - "importazione di elementi [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, importazione di elementi"
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Procedura dettagliata: importazione di una pagina master personalizzata e di una pagina del sito con un&#39;immagine
  In questa procedura dettagliata viene illustrato come importare una pagina master personalizzata di SharePoint e una pagina del sito con un'immagine in un progetto SharePoint per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 In questa procedura dettagliata viene mostrato come completare le attività seguenti:  
  
-   Creare una pagina master personalizzata e una pagina del sito utilizzando un'immagine in SharePoint Designer.  
  
-   Esportare una pagina master personalizzata, un'immagine e una pagina del sito in un file \(con estensione wsp\) della soluzione SharePoint.  
  
-   Importare e distribuire il file con estensione wsp in un progetto SharePoint per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizzando il progetto Importa pacchetto di soluzione SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   SharePoint Designer 2010.  
  
## Creare elementi in SharePoint Designer  
 In questo esempio viene mostrato come creare tre elementi in SharePoint Designer per esportare una pagina master personalizzata, una pagina del sito che fa riferimento alla pagina master personalizzata e un file di immagine da visualizzare nella pagina del sito.  L'immagine viene aggiunta alla cartella \/images\/ in SharePoint.  
  
#### Per creare una pagina master personalizzata in SharePoint Designer  
  
1.  Nel riquadro di navigazione di SharePoint Designer selezionare l'oggetto del sito **Pagine master**.  
  
2.  Sulla barra multifunzione **Pagine master**, scegliere **Pagina master vuota**.  
  
3.  Scegliere la nuova pagina master, quindi sulla barra multifunzione **Pagine master**, scegliere **Modifica file**.  
  
4.  Nella parte inferiore di SharePoint Designer selezionare la scheda **Codice**.  
  
5.  Sostituire il markup esistente con quello riportato di seguito.  
  
    ```  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  
  
6.  Salvare la pagina, scegliere la scheda **Pagine master** e rinominare la pagina master come **mybasic1.master**.  
  
## Aggiungere un'immagine al database del contenuto in SharePoint Designer  
 È possibile aggiungere un'immagine da visualizzare nella pagina del sito.  L'immagine viene distribuita nel database del contenuto SharePoint.  
  
#### Per aggiungere un'immagine al database del contenuto in SharePoint Designer  
  
1.  Nel riquadro di navigazione, selezionare l'oggetto del sito **Tutti i file** quindi, nella visualizzazione struttura ad albero, selezionare la cartella **immagini**.  
  
2.  Sulla barra multifunzione **Tutti i file**, scegliere **Importa file**, scegliere un file desiderato e quindi selezionare il pulsante **OK**.  In questo esempio il file è denominato **myimg1.png**.  
  
     Facoltativamente, è possibile creare una sottocartella per facilitare l'organizzare delle immagini.  
  
3.  Chiudere la finestra di dialogo **Importa**.  
  
## Creare una pagina del sito  
 In questa pagina del sito di base viene utilizzata la pagina master personalizzata e viene visualizzata l'immagine che è stata aggiunta nel passaggio precedente.  
  
#### Per creare una pagina del sito  
  
1.  Nel riquadro di navigazione, selezionare l'oggetto **Pagine sito**.  
  
2.  Sulla barra multifunzione **Pagine**, selezionare il pulsante **Pagina**, scegliere il tipo di pagina **ASPX** quindi assegnare un nuovo al file **mycontentpage1.aspx**.  
  
     Facoltativamente, è possibile creare una sottocartella per facilitare l'organizzazione delle pagine del sito.  
  
3.  Nell'elenco delle pagine del sito, selezionare **MyContentPage1.aspx** per aprire la pagina delle proprietà quindi, nella parte inferiore della pagina, selezionare il collegamento **Modifica file**.  
  
     Se viene visualizzato un messaggio e indica che la pagina non contiene alcune aree che siano modificabili in modalità sicura e viene richiesto se si desidera aprire la pagina in modalità avanzata, selezionare il pulsante **Sì**.  
  
4.  Nella parte inferiore della pagine, selezionare il pulsante **Codice**.  
  
5.  Sostituire il markup esistente con quello riportato di seguito.  
  
    ```  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  
  
    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  
  
6.  Salvare la pagina del sito aggiornata.  
  
## Esportare gli elementi da SharePoint  
 Esportare gli elementi da SharePoint in un file \(con estensione wsp\) della soluzione SharePoint.  
  
#### Per esportare elementi da SharePoint Designer  
  
1.  In SharePoint Designer, nel riquadro di navigazione, selezionare l'oggetto **Sito team** quindi, nella barra multifunzione **Sito**, scegliere **Salva come modello**.  
  
2.  Nella finestra di dialogo **Salva come modello** inserire un nome file e un nome del modello, selezionare la casella di controllo **Includi contenuto**, quindi scegliere il pulsante **Fine**.  
  
     In questo modo viene salvato il contenuto del sito nel file con estensione wsp.  
  
3.  Dopo aver esportato la soluzione, selezionare il collegamento **Raccolta soluzioni** per visualizzare l'elenco dei file di soluzione disponibili.  
  
4.  Aprire il menu di scelta rapida per il nuovo file con estensione .wsp e quindi scegliere **Salva destinazione come** per salvare il file nel sistema.  
  
## Importare gli elementi in Visual Studio  
 Importare il file .wap in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Dopo che il contenuto è stato importato, è possibile personalizzarlo, aggiungere altri elementi e quindi distribuirlo.  
  
#### Per importare elementi dal file con estensione wsp in Visual Studio  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto **Importa pacchetto di soluzione SharePoint 2010**.  
  
2.  Nella pagina **Selezionare elementi da importare**, sotto **Modulo** nella colonna **Tipo** selezionare le caselle di controllo solamente per i file da importare riportati nella seguente tabella.  
  
    |Nome file|Descrizione|  
    |---------------|-----------------|  
    |\_catalogsmasterpage\_|Pagina master personalizzata.|  
    |images\_|File di immagine nel file system di SharePoint.|  
    |SitePages\_|Pagina del sito.|  
  
3.  Scegliere il pulsante **Fine** per importare gli elementi selezionati.  
  
4.  In **Esplora soluzioni** selezionare il nodo \_catalogsmasterpage\_ e impostare il valore della proprietà **Risoluzione conflitti di distribuzione** su **Automatica**.  
  
     In questo modo tutti i conflitti di distribuzione vengono risolti automaticamente.  
  
5.  Se il nome della nuova pagina master corrisponde a quello di una pagina esistente, verificare che la pagina esistente non sia contrassegnata come Pagina master predefinita o Pagina master personalizzata in SharePoint Designer.  
  
     Se una pagina master esistente è contrassegnata come Pagina master predefinita o Pagina master personalizzata, si visualizzerà un errore di distribuzione per indicare che è impossibile eliminare la pagina master.  Per evitare questo problema, effettuare le operazioni riportate di seguito.  
  
    -   Se la pagina master esistente è impostata come Pagina master predefinita, impostare temporaneamente un'altra pagina master come Pagina master predefinita.  Dopo aver distribuito i file in SharePoint, impostare la nuova pagina master come Pagina master predefinita.  
  
    -   Se la pagina master esistente è impostata come Pagina master personalizzata, impostare temporaneamente un'altra pagina master come Pagina master personalizzata.  Dopo aver distribuito i file in SharePoint, impostare la nuova pagina master come Pagina master personalizzata.  
  
6.  Sulla barra dei menu scegliere **Compilazione**, **Distribuisci soluzione**.  
  
7.  Aprire il sito di SharePoint per visualizzare gli elementi distribuiti.  
  
 Un modo alternativo per importare file in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e distribuirli in SharePoint consiste nell'aggiungere i file in moduli in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Procedura: importare una pagina master o un tema](../sharepoint/how-to-import-a-master-page-or-theme.md) e [Utilizzo di moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## Vedere anche  
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  