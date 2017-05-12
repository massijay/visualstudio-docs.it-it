---
title: "Elemento XML della barra multifunzione"
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
  - "VSTO.Ribbon.RibbonXMLItem"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "barra multifunzione personalizzata, XML"
  - "personalizzazione della barra multifunzione, XML"
  - "barra multifunzione [sviluppo per Office in Visual Studio], XML"
  - "metodi di callback"
  - "barra multifunzione personalizzata, visualizzazione"
  - "barra multifunzione personalizzata, definizione del comportamento"
  - "XML [sviluppo per Office in Visual Studio], barra multifunzione"
  - "personalizzazione della barra multifunzione, definizione del comportamento"
  - "barra multifunzione [sviluppo per Office in Visual Studio], personalizzazione"
  - "personalizzazione della barra multifunzione, visualizzazione"
ms.assetid: a5945667-40e8-4191-9f1e-71c18ec30a2e
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Elemento XML della barra multifunzione
  L'elemento Barra multifunzione \(XML\) consente di personalizzare una barra multifunzione tramite XML. Usare l'elemento Barra multifunzione \(XML\) se si desidera personalizzare la barra multifunzione in un modo non supportato dall'elemento Barra multifunzione \(finestra di progettazione visiva\). Per un confronto tra le operazioni che possono essere eseguite con ognuna di esse, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## Aggiunta di un elemento Barra multifunzione \(XML\) a un progetto  
 È possibile aggiungere un elemento **Barra multifunzione \(XML\)** a qualsiasi progetto di Office dalla finestra di dialogo **Aggiungi nuovo elemento**. Visual Studio aggiunge automaticamente i file seguenti al progetto:  
  
-   Un file XML della barra multifunzione. Questo file definisce l'interfaccia utente della barra multifunzione. Usare questo file per aggiungere elementi dell'interfaccia utente, ad esempio schede, gruppi e controlli. Per informazioni dettagliate, vedere [Informazioni di riferimento sul file XML della barra multifunzione](#RibbonDescriptorFile) più avanti in questo argomento.  
  
-   Un file di codice della barra multifunzione. Questo file contiene la *classe Ribbon*. Il nome della classe corrisponde a quello specificato per l'elemento **Barra multifunzione \(XML\)** nella finestra di dialogo **Aggiungi nuovo elemento**. Le applicazioni di Microsoft Office usano un'istanza di questa classe per caricare la barra multifunzione personalizzata. Per informazioni, vedere [Informazioni di riferimento sulla classe Ribbon](#RibbonExtensionClass) più avanti in questo argomento.  
  
 Per impostazione predefinita, questi file aggiungono un gruppo personalizzato nella scheda **Componenti aggiuntivi** della barra multifunzione.  
  
## Visualizzazione della barra multifunzione personalizzata in un'applicazione di Microsoft Office  
 Dopo aver aggiunto un elemento **Barra multifunzione \(XML\)** al progetto, è necessario aggiungere il codice alla classe **ThisAddin**, **ThisWorkbook** o **ThisDocument** che esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce la classe Ribbon XML all'applicazione di Office.  
  
 L'esempio di codice seguente esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce una classe Ribbon XML denominata MyRibbon.  
  
 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
## Definizione del comportamento della barra multifunzione personalizzata  
 È possibile rispondere alle azioni utente, ad esempio il clic su un pulsante della barra multifunzione, creando *metodi di callback*. I metodi di callback sono simili agli eventi nei controlli Windows Form, ma vengono identificati da un attributo nel codice XML dell'elemento dell'interfaccia utente. I metodi vengono scritti nella classe Ribbon e un controllo chiama il metodo con lo stesso nome del valore dell'attributo. Ad esempio, è possibile creare un metodo di callback che viene chiamato quando un utente fa clic su un pulsante della barra multifunzione. Per creare un metodo di callback, sono necessari due passaggi:  
  
-   Assegnare un attributo a un controllo nel file XML della barra multifunzione che identifica un metodo di callback nel codice.  
  
-   Definire il metodo di callback nella classe Ribbon.  
  
> [!NOTE]  
>  Outlook richiede un ulteriore passaggio. Per altre informazioni, vedere [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
 Per una procedura dettagliata che illustra come automatizzare un'applicazione dalla barra multifunzione, vedere [Procedura dettagliata: creazione di una scheda personalizzata utilizzando l'elemento XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).  
  
### Assegnazione di metodi di callback ai controlli  
 Per assegnare un metodo di callback a un controllo nel file XML della barra multifunzione, aggiungere un attributo che specifica il tipo del metodo di callback e il nome del metodo. Ad esempio, l'elemento seguente definisce un interruttore con un metodo di callback **onAction** denominato `OnToggleButton1`.  
  
```  
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />  
```  
  
 **onAction** viene chiamato quando l'utente esegue l'attività principale associata a un controllo specifico. Ad esempio, il metodo di callback **onAction** di un interruttore viene chiamato quanto l'utente fa clic sul pulsante.  
  
 Il metodo specificato nell'attributo può avere qualsiasi nome. Tuttavia, deve corrispondere al nome del metodo definito nel file di codice della barra multifunzione.  
  
 Ci sono molti tipi diversi di metodi di callback che è possibile assegnare ai controlli della barra multifunzione. Per un elenco completo dei metodi di callback disponibili per ogni controllo, vedere l'articolo tecnico [Personalizzazione dell'interfaccia utente della barra multifunzione di Office \(2007\) per sviluppatori \(parte 3 di 3\)](http://msdn.microsoft.com/it-it/a16c7df5-93f3-4920-baa8-7b7290794c15).  
  
###  <a name="CallBackMethods"></a> Definizione dei metodi di callback  
 Definire i metodi di callback nella classe Ribbon nel file di codice della barra multifunzione. Un metodo di callback presenta diversi requisiti:  
  
-   Deve essere dichiarato come pubblico.  
  
-   Il nome deve corrispondere al nome di un metodo di callback assegnato a un controllo nel file XML della barra multifunzione.  
  
-   La firma deve corrispondere alla firma di un tipo di metodo di callback disponibile per il controllo barra multifunzione associato.  
  
 Per un elenco completo delle firme dei metodi di callback disponibili per i controlli barra multifunzione, vedere l'articolo tecnico [Personalizzazione dell'interfaccia utente della barra multifunzione di Office \(2007\) per sviluppatori \(parte 3 di 3\)](http://msdn.microsoft.com/it-it/a16c7df5-93f3-4920-baa8-7b7290794c15). Visual Studio non fornisce supporto IntelliSense per i metodi di callback creati nel file di codice della barra multifunzione. Se si crea un metodo di callback che non corrisponde a una firma valida, il codice verrà compilato, ma non succederà niente quando l'utente fa clic sul controllo.  
  
 Tutti i metodi di callback hanno un parametro <xref:Microsoft.Office.Core.IRibbonControl> che rappresenta il controllo che ha chiamato il metodo. È possibile usare questo parametro per riutilizzare lo stesso metodo di callback per più controlli. L'esempio di codice seguente illustra un metodo di callback **onAction** che esegue attività diverse a seconda del controllo su cui l'utente fa clic.  
  
 [!code-csharp[Trin_RibbonOutlookBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/CS/Ribbon1.cs#2)]
 [!code-vb[Trin_RibbonOutlookBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/VB/Ribbon1.vb#2)]  
  
##  <a name="RibbonDescriptorFile"></a> Informazioni di riferimento sul file XML della barra multifunzione  
 È possibile definire la barra multifunzione personalizzata aggiungendo elementi e attributi al file XML della barra multifunzione. Per impostazione predefinita, il file XML della barra multifunzione contiene il codice XML seguente.  
  
```  
<?xml version="1.0" encoding="UTF-8"?> <customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad"> <ribbon> <tabs> <tab idMso="TabAddIns"> <group id="MyGroup" label="My Group"> </group> </tab> </tabs> </ribbon> </customUI>  
```  
  
 La tabella seguente descrive gli elementi predefiniti del file XML della barra multifunzione:  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|**customUI**|Rappresenta la barra multifunzione personalizzata nel progetto di componente aggiuntivo VSTO.|  
|**ribbon**|Rappresenta la barra multifunzione.|  
|**tabs**|Rappresenta un set di schede della barra multifunzione.|  
|**tab**|Rappresenta una singola scheda della barra multifunzione.|  
|**group**|Rappresenta un gruppo di controlli nella scheda della barra multifunzione.|  
  
 Questi elementi hanno attributi che specificano l'aspetto e il comportamento della barra multifunzione personalizzata. La tabella seguente descrive gli attributi predefiniti del file XML della barra multifunzione:  
  
|Attributo|Elemento padre|Descrizione|  
|---------------|--------------------|-----------------|  
|**onLoad**|**customUI**|Identifica un metodo che viene chiamato quando l'applicazione carica la barra multifunzione.|  
|**idMso**|**tab**|Identifica una scheda predefinita da visualizzare nella barra multifunzione.|  
|**id**|**group**|Identifica il gruppo.|  
|**label**|**group**|Specifica il testo visualizzato nel gruppo.|  
  
 Gli elementi e gli attributi predefiniti nel file XML della barra multifunzione sono un piccolo subset degli elementi e degli attributi disponibili. Per un elenco completo degli elementi e degli attributi disponibili, vedere l'articolo tecnico [Personalizzazione dell'interfaccia utente della barra multifunzione di Office \(2007\) per sviluppatori \(parte 2 di 3\)](http://msdn.microsoft.com/it-it/6b904f55-525f-4520-9b81-a017db65657b).  
  
##  <a name="RibbonExtensionClass"></a> Informazioni di riferimento sulla classe Ribbon  
 Visual Studio genera la classe Ribbon nel file di codice della barra multifunzione. Aggiungere i metodi di callback per i controlli della barra multifunzione a questa classe. Questa classe implementa l'interfaccia <xref:Microsoft.Office.Core.IRibbonExtensibility>.  
  
 La tabella seguente descrive i metodi predefiniti della classe.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`GetCustomUI`|Restituisce il contenuto del file XML della barra multifunzione. Le applicazioni di Microsoft Office chiamano questo metodo per ottenere una stringa XML che definisce l'interfaccia utente della barra multifunzione personalizzata. Questo metodo implementa il metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>. **Note:**  `GetCustomUI` deve essere implementato solo per restituire il contenuto del file XML della barra multifunzione e non deve essere usato per inizializzare il componente aggiuntivo VSTO. In particolare, non tentare di visualizzare finestre di dialogo o altre finestre nell'implementazione di `GetCustomUI`. In caso contrario, la barra multifunzione personalizzata potrebbe non funzionare correttamente. Se è necessario eseguire codice per l'inizializzazione del componente aggiuntivo VSTO, aggiungere il codice al gestore eventi `ThisAddIn_Startup`.|  
|`OnLoad`|Assegna il parametro <xref:Microsoft.Office.Core.IRibbonControl> al campo `ribbon`. Le applicazioni di Microsoft Office chiamano questo metodo per caricare la barra multifunzione personalizzata. È possibile usare questo campo per aggiornare dinamicamente la barra multifunzione personalizzata. Per altre informazioni, vedere l'articolo tecnico [Personalizzazione dell'interfaccia utente della barra multifunzione di Office \(2007\) per sviluppatori \(parte 1 di 3\)](http://msdn.microsoft.com/it-it/a4fd6d18-d4a8-4e64-bd89-f437208573d3).|  
|`GetResourceText`|Chiamato dal metodo `GetCustomUI` per ottenere il contenuto del file XML della barra multifunzione.|  
  
## Vedere anche  
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando l'elemento XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)  
  
  