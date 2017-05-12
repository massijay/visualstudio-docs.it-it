---
title: "Localizzazione di soluzioni SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.GlobalAndFeatureResource"
  - "VS.SharePoint.Project.AddResourceDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "globalizzazione [sviluppo per SharePoint in Visual Studio]"
  - "localizzazione [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, localizzazione"
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Localizzazione di soluzioni SharePoint
  Il processo di preparazione delle applicazioni in modo che possano essere utilizzate a livello mondiale è noto come localizzazione.  La localizzazione consiste nella traduzione delle risorse in determinate impostazioni cultura.  Per ulteriori informazioni, vedere [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md).  In questo argomento sono contenuti cenni preliminari sulla localizzazione di una soluzione SharePoint.  
  
 Per localizzare una soluzione, è necessario rimuovere stringhe hardcoded dal codice ed estrarle in file di risorse.  Un file di risorse è un file basato su [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] con estensione resx.  Il file di risorse contiene le versioni tradotte delle stringhe utilizzate nella soluzione.  Per ulteriori informazioni, vedere [Risorse nelle applicazioni](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Aggiungere solo risorse di tipo stringa ai file di risorse delle soluzioni SharePoint.  Sebbene Editor risorse consenta di aggiungere risorse non di tipo stringa, tali risorse non vengono distribuite in SharePoint.  
  
## File di risorse  
 Esistono tre tipi di file di risorse: predefinito, indipendente dalla lingua e specifico della lingua.  
  
|Tipo di file di risorse|Descrizione|  
|-----------------------------|-----------------|  
|Predefinito|Anche noti come risorse di fallback, i file di risorse predefiniti contengono stringhe localizzate per le impostazioni cultura predefinite, ad esempio Inglese.  Vengono utilizzati se non è possibile trovare file di risorse localizzati per la lingua specificata.  Le risorse predefinite non presentano file separati e vengono archiviate nell'assembly dell'applicazione principale.|  
|Indipendente dalla lingua|File di risorse contenente stringhe localizzate per una lingua, ma non per impostazioni cultura specifiche,  ad esempio "fr" per il francese.|  
|Specifico della lingua|File di risorse contenente stringhe localizzate per una lingua e per impostazioni cultura specifiche,  ad esempio "fr\-CA" per il francese canadese.|  
  
 Per ulteriori informazioni, vedere [Organizzazione gerarchica delle risorse per la localizzazione](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Per specificare file di risorse predefiniti nei progetti SharePoint sviluppati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], selezionare **Lingua inglese \(non associata ad alcun paese\)** nell'elenco delle impostazioni cultura della finestra di dialogo **Aggiungi risorsa** quando si aggiunge un file di risorse.  
  
## Localizzazione delle soluzioni SharePoint di Visual Studio  
 Quando si localizza una soluzione, è necessario considerare tutte le informazioni testuali che vengono visualizzate al suo interno per gli utenti.  È necessario tradurre le stringhe dei messaggi informativi, dei messaggi di errore e dell'[!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] e quindi inserire le traduzioni nei file di risorse.  
  
 Ogni stringa in un file di risorse dispone di un identificatore univoco.  Utilizzare lo stesso identificatore per la stringa tradotta in ogni file di risorse.  Se, ad esempio, "String1" è l'identificatore della prima stringa nel file di risorse predefinito, utilizzare lo stesso identificatore per la prima stringa nei file di risorse specifici della lingua.  
  
 Nelle applicazioni di SharePoint di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vengono in genere localizzate tre aree: funzionalità, markup delle pagine ASPX e codice.  A scopo dimostrativo, nelle sezioni seguenti si suppone di disporre di una soluzione SharePoint da localizzare in tedesco e in giapponese.  La lingua predefinita è l'inglese.  
  
### Localizzazione di funzionalità  
 Per localizzare una funzionalità, è necessario sostituire il titolo hardcoded e la descrizione della funzionalità con un'espressione che faccia riferimento al titolo e alla stringa tradotti nel file di risorse localizzato.  Per apportare questa modifica è necessario utilizzare **Progettazione funzionalità** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Per ulteriori informazioni, vedere [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md).  
  
 Per localizzare la funzionalità inglese in tedesco e in giapponese, aggiungere tre elementi del progetto File di risorse al proprio progetto: uno per l'inglese, uno per il tedesco e uno per il giapponese.  Non è possibile utilizzare file di risorse di funzionalità per localizzare codice o markup ASPX. Per questi ultimi sono infatti richiesti file di risorse separati.  
  
 Dopo avere creato i file di risorse di funzionalità, aggiungervi le stringhe tradotte.  Accedere alle stringhe localizzate con un'espressione nel formato seguente:  
  
```  
$Resources:String ID  
```  
  
 Le risorse di funzionalità di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vengono sempre denominate Resources.  Se viene selezionata una lingua diverso dalla lingua inglese, allora le impostazioni cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] vengono aggiunti al nome del file di risorse.  Ad esempio, se si aggiunge un file di risorse della funzionalità relativa alla lingua inglese \(impostazione predefinita\), questo viene denominato Resources.resx.  Se si aggiunge una risorsa di funzionalità specifica della lingua selezionando le impostazioni cultura per la lingua giapponese \(Giappone\), il file viene denominato Resources.ja\-JP.resx.  Ai file di risorse di funzionalità viene automaticamente assegnato un nome non modificabile.  
  
 L'ambito delle risorse di funzionalità è locale rispetto alla funzionalità alla quale vengono aggiunte.  Per creare risorse utilizzabili con qualsiasi file di funzionalità o elemento nella soluzione, aggiungere un elemento del progetto **File di risorse globali** anziché un file di risorse di funzionalità.  L'elemento del progetto **File di risorse globali** si trova nella cartella **2010** di **SharePoint** nella finestra di dialogo **Aggiungi nuovo elemento**.  I file di risorse globali vengono distribuiti nella cartella \\Resources della cartella radice di SharePoint.  
  
### Localizzazione del markup della pagina ASPX  
 Per localizzare le pagine [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], aggiungere tre elementi del progetto File di risorse al proprio progetto: uno per l'inglese, uno per il tedesco e uno per il giapponese.  Se non è necessario localizzare il codice oltre al markup, è possibile allora aggiungere File di risorse globali.  
  
 Specificare un nome per il file di risorse della lingua predefinita.  Assegnare ai file di risorse localizzati lo stesso nome aggiunto all'[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] delle impostazioni cultura specifico della lingua,  ad esempio MyAppResources.de\-DE.resx per il tedesco e MyAppResources.ja\-JP.resx per il giapponese.  
  
 Impostare la proprietà **Tipo distribuzione** di ogni file di risorse su **AppGlobalResource**.  In questo modo i file di risorse vengono distribuiti nella cartella App\_GlobalResources, dove sono disponibili per tutte le pagine e i controlli ASPX della soluzione.  La cartella App\_GlobalResources si trova in C:\\inetpub\\wwwroot\\wss\\VirtualDirectories\\\<numero porta\>\\App\_GlobalResources.  
  
> [!NOTE]  
>  Se si utilizzano file di risorse non globali, spostarli nella cartella degli elementi del progetto per abilitare la proprietà Tipo distribuzione e altre proprietà specifiche di SharePoint.  
  
 È inoltre possibile utilizzare i file di risorse di markup ASPX per localizzare il codice.  Se si utilizzano le risorse per localizzare codice oltre al markup ASPX, lasciare l'impostazione della proprietà Operazione di compilazione di ogni file su Risorsa incorporata per fare in modo che la risorsa venga compilata in un assembly satellite.  Se invece si utilizzano i file di risorse solo per localizzare il markup, è possibile modificare l'impostazione di Operazione di compilazione in Contenuto per evitare che il file venga compilato nell'assembly dell'applicazione principale.  
  
 Sostituire tutte le stringhe delle proprietà hardcoded nel markup delle pagine e dei controlli ASPX con un'espressione che abbia il formato seguente:  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Ad esempio:  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Per ASPX come testo, utilizzare un'espressione nel formato seguente:  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Ad esempio:  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Per ulteriori informazioni, vedere [Procedura: localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md).  
  
### Localizzazione del codice  
 Oltre a localizzare le stringhe di funzionalità e il markup [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], è anche necessario localizzare le stringhe relative a messaggi ed errori visualizzate nel codice della soluzione.  Messaggi di informazione e di errore localizzati sono contenuti in assembly satellite.  Gli assembly satellite contengono stringhe visibili agli utenti, ad esempio testo e messaggi di output di [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] come le eccezioni.  
  
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene utilizzato il modello hub e spoke di .NET Framework standard.  L'hub, o assembly del programma principale, contiene le risorse della lingua predefinita.  Gli spoke, o assembly satellite, contengono le risorse specifiche della lingua.  Per ulteriori informazioni, vedere [Creazione del package e distribuzione delle risorse](http://go.microsoft.com/fwlink/?LinkId=179280).  Gli assembly satellite vengono compilati da file di risorse \(con estensione resx\).  Quando si aggiungono file di risorse specifici della lingua al progetto e al pacchetto della soluzione, in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tali file vengono compilati in assembly satellite denominati *Project Name*.resources.dll.  
  
 Come per il markup ASPX, localizzare il codice dell'applicazione di SharePoint aggiungendo elementi del progetto File di risorse separati al proprio progetto, ovvero uno per la lingua predefinita e uno per ogni lingua localizzata.  Come indicato in precedenza, tuttavia, se già si dispone di file di risorse per la localizzazione del markup ASPX, è possibile riutilizzarli per localizzare il codice.  Se è necessario creare file di risorse, assegnare al file di risorse della lingua predefinita un nome di propria scelta con estensione resx.  Assegnare ai file di risorse localizzati lo stesso nome aggiunto all'[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] delle impostazioni cultura specifico della lingua,  Impostare la proprietà Operazione di compilazione di ogni file di risorse su Risorsa incorporata per consentire la creazione di assembly di risorse satellite.  
  
 Per creare gli assembly satellite, compilare il progetto, quindi aggiungere i file come assembly aggiuntivi tramite la scheda **Avanzate** di **Progettazione pacchetti**.  Quando si aggiungono gli assembly, anteporre una cartella con l'[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] delle impostazioni cultura al percorso, ad esempio it\-IT\\*Project Item Name*.resources.dll.  In questo modo nel pacchetto potranno essere contenuti file con lo stesso nome.  
  
 Nel codice sostituire le stringhe hardcoded con chiamate al metodo <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> utilizzando la sintassi seguente:  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Per ulteriori informazioni, vedere [Procedura: localizzare il codice](../sharepoint/how-to-localize-code.md).  
  
#### Localizzazione del codice delle Web part  
 Le Web part offrono una funzionalità dell'editor proprietà personalizzata che include attributi di codice che utilizzano stringhe hardcoded, quali WebDisplayName, Category e WebDescription.  Per sostituire i valori di stringa con tali attributi, creare una classe separata che derivi dalla classe dell'attributo.  In queste classi impostare la proprietà dell'attributo.  Tale proprietà dipende dalla classe base.  La proprietà dell'attributo WebDisplayName è ad esempio DisplayNameValue e la proprietà dell'attributo WebDescription è DescriptionValue.  
  
 Nella classe derivata fare riferimento all'ID stringa dal file di risorse e dall'oggetto ResourceManager per ottenere il valore localizzato di tale ID stringa.  Restituire questo valore all'attributo dell'editor proprietà.  
  
## Vedere anche  
 [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)   
 [Procedura: localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Procedura: localizzare il codice](../sharepoint/how-to-localize-code.md)   
 [Procedura: aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)   
 [Procedura: utilizzare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  