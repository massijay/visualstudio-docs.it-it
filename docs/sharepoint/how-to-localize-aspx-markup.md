---
title: 'Procedura: localizzare il Markup ASPX | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d72d4807f61adcab1321b6471c2bea31f048a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-localize-aspx-markup"></a>Procedura: localizzare il markup ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]pagine (aspx), in genere, utilizzare i valori stringa hardcoded. Per localizzare le stringhe, sostituirli con espressioni che fanno riferimento alle risorse localizzate.  
  
## <a name="localizing-aspx-markup"></a>Localizzazione Markup ASPX  
  
#### <a name="to-localize-aspx-markup"></a>Per localizzare il markup ASPX  
  
1.  Aggiungere file di risorse separati: uno per la lingua predefinita e uno per ogni lingua localizzata.  
  
     Se si localizza solo il markup e non di codice, aggiungere un elemento di progetto di File di risorse globali. Se si localizza codice e markup, aggiungere un elemento di progetto di File di risorse.  
  
    1.  Per aggiungere un File di risorse globali in **Esplora**, aprire il menu di scelta rapida per un elemento di progetto SharePoint e quindi scegliere **Aggiungi**, **nuovo elemento**. In SharePoint **2010** nodo, scegliere il **File di risorse globali** modello.  
  
    2.  Per aggiungere un File di risorse, in **Esplora**, aprire il menu di scelta rapida per un elemento di progetto SharePoint e quindi scegliere **Aggiungi**, **nuovo elemento**. Sotto il **Visual Basic** o **Visual c#** nodo, scegliere il **File di risorse** modello.  
  
    > [!NOTE]  
    >  Assicurarsi di aggiungere i file di risorse a un elemento di progetto SharePoint per abilitare la proprietà del tipo di distribuzione. Questa proprietà è necessario più avanti in questa procedura. Se la soluzione non dispone di un elemento di progetto SharePoint, è possibile aggiungere un progetto SharePoint vuoto e rimuovere il file Elements.xml predefinito.  
  
2.  Assegnare il file di risorse di lingua predefinita di un nome di propria scelta con estensione resx, ad esempio MyAppResources. Utilizzare lo stesso nome base per ogni file di risorse localizzato, ma aggiungere l'[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] delle impostazioni cultura. Assegnare un nome, ad esempio, una risorsa localizzata tedesca MyAppResources.de-de.  
  
3.  Modificare il valore della **tipo di distribuzione** proprietà di ogni file di risorse per **AppGlobalResource** per cartella App_GlobalResources del server.  
  
4.  Se si utilizzano le risorse per localizzare il codice oltre al markup ASPX, lasciare il valore di **azione di compilazione** proprietà di ogni file come **risorsa incorporata**. Se si utilizza i file di risorse solo per localizzare il markup, è possibile modificare facoltativamente il valore della proprietà dei file **contenuto**. Per ulteriori informazioni, vedere [localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Aprire ogni file di risorse e aggiungere le stringhe localizzate, utilizzando la stessa stringa ID in ogni file.  
  
6.  Nel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] markup per la pagina ASPX o di un controllo, sostituire le stringhe hardcoded con i valori che utilizzano il formato seguente:  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Per localizzare il testo per un controllo etichetta in una pagina applicazione, ad esempio, sarebbe modificare:  
  
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
  
8.  In SharePoint, modificare la lingua di visualizzazione da quello predefinito.  
  
     Le stringhe localizzate visualizzata nell'applicazione. Per visualizzare le risorse localizzate, il server di SharePoint deve disporre di un language pack installati che corrispondono alle impostazioni cultura del file di risorse.  
  
## <a name="see-also"></a>Vedere anche  
 [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)   
 [Procedura: aggiungere un File di risorse](../sharepoint/how-to-add-a-resource-file.md)   
 [Procedura: Localizzare il codice](../sharepoint/how-to-localize-code.md)  
  
  