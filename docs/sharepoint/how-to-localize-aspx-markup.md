---
title: "Procedura: localizzare il markup ASPX | Microsoft Docs"
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
  - "localizzazione XML [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, localizzazione"
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Procedura: localizzare il markup ASPX
  Le pagine [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] \(.aspx\) utilizzano in genere valori stringa hardcoded.  Per localizzare tali stringhe, sostituirle con espressioni che fanno riferimento a risorse localizzate.  
  
## Localizzazione del markup ASPX  
  
#### Per localizzare il markup ASPX  
  
1.  Aggiungere file di risorse separati, uno per la lingua predefinita e uno per ogni lingua localizzata.  
  
     Se si localizza solo il markup e non il codice, aggiungere un elemento del progetto File di risorse globali.  Se si localizza il codice e il markup, aggiungere un elemento del progetto File di risorse.  
  
    1.  Per aggiungere un File di risorse globali, in **Esplora soluzioni**, aprire il menu di scelta rapida per un elemento di progetto SharePoint e quindi scegliere **Aggiungi**, **Nuovo elemento**.  Sotto il nodo SharePoint **2010**, scegliere il modello di **File di risorse globali**.  
  
    2.  Per aggiungere un File di risorse, in **Esplora soluzioni**, aprire il menu di scelta rapida per un elemento di progetto SharePoint e quindi scegliere **Aggiungi**, **Nuovo elemento**.  Sotto il nodo **Visual Basic** o **Visual C\#**, scegliere il modello **File di risorse**.  
  
    > [!NOTE]  
    >  Assicurarsi di aggiungere i file di risorse a un elemento di progetto SharePoint per abilitare la proprietà Tipo distribuzione.  Questa proprietà viene richiesta in un secondo momento nella procedura.  Se la soluzione non dispone di un elemento di progetto SharePoint, è possibile aggiungere un Progetto SharePoint vuoto e rimuovere il relativo file Elements.xml predefinito.  
  
2.  Assegnare al file di risorse della lingua predefinita un nome di propria scelta con estensione resx, ad esempio MyAppResources.resx.  Utilizzare lo stesso nome di base per ogni file di risorse localizzato, ma aggiungere le impostazioni cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)].  Assegnare, ad esempio, a una risorsa localizzata in tedesco il nome MyAppResources.de\-DE.resx.  
  
3.  Cambiare il valore della proprietà **Tipo distribuzione** di ogni file di risorse su **AppGlobalResource** per indurli a essere distribuiti nella cartella App\_GlobalResources del server.  
  
4.  Se si utilizzano le risorse per localizzare il codice oltre al markup ASPX, lasciare il valore della proprietà **Operazione di compilazione** di ogni file impostato su **Risorsa incorporata**.  Se si utilizzano i file di risorse solo per localizzare il markup, è possibile impostare facoltativamente il valore della proprietà dei file su **Contenuto**.  Per ulteriori informazioni, vedere [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Aprire ogni file di risorse e aggiungere stringhe localizzate, utilizzando gli stessi ID di stringa in ogni file.  
  
6.  Nel markup [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] per la pagina o il controllo ASPX sostituire le stringhe hardcoded con valori che utilizzano il formato seguente:  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Per localizzare ad esempio il testo per un controllo etichetta in una pagina dell'applicazione è necessario modificare:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     in  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Premere il tasto F5 per compilare ed eseguire l'applicazione.  
  
8.  In SharePoint modificare la lingua di visualizzazione predefinita.  
  
     Nell'applicazione verranno visualizzate le stringhe localizzate.  Per la visualizzazione delle risorse localizzate, è necessario che nel server SharePoint sia installato un Language Pack corrispondente alle impostazioni cultura del file di risorse.  
  
## Vedere anche  
 [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)   
 [Procedura: aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)   
 [Procedura: localizzare il codice](../sharepoint/how-to-localize-code.md)  
  
  