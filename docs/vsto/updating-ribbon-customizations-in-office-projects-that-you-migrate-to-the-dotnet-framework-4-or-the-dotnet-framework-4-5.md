---
title: "Aggiornamento delle personalizzazioni della barra multifunzione nei progetti di Office di cui si esegue la migrazione a .NET Framework 4 o a .NET Framework 4.5 | Microsoft Docs"
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
  - "progetti Office [sviluppo per Office in Visual Studio], migrazione a .NET Framework 4"
ms.assetid: 3b7c8ad4-a616-4b42-9d62-9658fdefe6a3
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Aggiornamento delle personalizzazioni della barra multifunzione nei progetti di Office di cui si esegue la migrazione a .NET Framework 4 o a .NET Framework 4.5
  Se il progetto contiene una personalizzazione della barra multifunzione creata usando l'elemento di progetto **Barra multifunzione \(finestra di progettazione visiva\)**, è necessario apportare le seguenti modifiche al codice del progetto se il framework di destinazione viene modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive:  
  
-   Modificare il codice della barra multifunzione generato.  
  
-   Modificare qualsiasi codice che crea un'istanza dei controlli della barra multifunzione in fase di esecuzione, gestisce gli eventi della barra multifunzione o imposta la posizione di un componente della barra multifunzione a livello di programmazione.  
  
## Aggiornamento del codice della barra multifunzione generato  
 Se la versione di. il Framework di destinazione del progetto viene aggiornato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario modificare il codice generato per l'elemento barra multifunzione effettuando i passaggi seguenti.  I file di codice che è necessario aggiornare dipendono dal linguaggio di programmazione e dalla modalità di creazione del progetto:  
  
-   Nei progetti di Visual Basic o nei progetti Visual C\# creati in [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] o [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] eseguire tutti i passaggi nel file code\-behind della barra multifunzione \(*YourRibbonItem*. Designer.cs o *YourRibbonItem*. Designer.vb\).  Per visualizzare il file code\-behind nei progetti Visual Basic, fare clic sul pulsante **Mostra tutti i file** in **Esplora soluzioni**.  
  
-   Nei progetti Visual C\# creati in Visual Studio 2008 e successivamente aggiornati a [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], eseguire i primi due passaggi nel file di codice della barra multifunzione \(*YourRibbonItem*.cs o *YourRibbonItem*.vb\) ed eseguire i passaggi rimanenti nel file code\-behind della barra multifunzione.  
  
#### Per modificare il codice della barra multifunzione generato  
  
1.  Modificare la dichiarazione della classe Ribbon in modo che derivi da <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> anziché da Microsoft.Office.Tools.Ribbon.OfficeRibbon.  
  
2.  Modificare il costruttore della classe Ribbon come illustrato di seguito.  Se è stato aggiunto codice al costruttore, non modificare il codice.  Nei progetti Visual Basic modificare solo il costruttore senza parametri.  Ignorare l'altro costruttore.  
  
     L'esempio di codice seguente illustra il costruttore predefinito di una classe Ribbon in un progetto destinato a .NET Framework 3.5  
  
    ```vb  
    Public Sub New()  
        MyBase.New()  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
    {  
        InitializeComponent();  
    }  
    ```  
  
     L'esempio di codice seguente illustra il costruttore predefinito di una classe Ribbon in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive.  
  
    ```vb  
    Public Sub New()  
        MyBase.New(Globals.Factory.GetRibbonFactory())  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
        : base(Globals.Factory.GetRibbonFactory())  
    {  
        InitializeComponent();  
    }  
    ```  
  
3.  Nel metodo `InitializeComponent` modificare il codice con il quale viene costruito un controllo barra multifunzione in modo che il codice usi invece uno dei metodi di supporto dell'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
    > [!NOTE]  
    >  Nei progetti Visual C\# è necessario espandere l'area denominata `Component Designer generated code` per visualizzare il metodo `InitializeComponent`.  
  
     Ad esempio, si supponga che il file contenga la riga di codice seguente con la quale viene creata un'istanza di un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> denominata `button1` in un progetto destinato a .NET Framework 3.5.  
  
    ```vb  
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();  
    ```  
  
     In un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario usare il codice seguente.  
  
    ```vb  
    Me.button1 = Me.Factory.CreateRibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = this.Factory.CreateRibbonButton();  
    ```  
  
     Per un elenco completo dei metodi di supporto per i controlli barra multifunzione, vedere [Creazione di un'istanza dei controlli barra multifunzione](#ribboncontrols).  
  
4.  Nei progetti Visual C\# modificare qualsiasi riga di codice nel metodo `InitializeComponent` che usa un delegato <xref:System.EventHandler%601> per usare invece un delegato specifico della barra multifunzione.  
  
     Ad esempio, si supponga che il file contenga la riga di codice seguente con la quale viene gestito l'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> in un progetto destinato a .NET Framework 3.5.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler<Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>(  
        this.button1_Click);  
    ```  
  
     In un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario usare il codice seguente.  
  
    ```csharp  
    this.button1.Click += new Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler(  
        this.button1_Click);  
    ```  
  
     Per un elenco completo di delegati della barra multifunzione, vedere [Gestione di eventi della barra multifunzione](#ribbonevents).  
  
5.  Nei progetti Visual Basic trovare la classe `ThisRibbonCollection` alla fine del file.  Modificare la dichiarazione della classe in modo che non erediti più da Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection.  
  
##  <a name="ribboncontrols"></a> Creazione di un'istanza dei controlli barra multifunzione  
 È necessario modificare il codice che crea dinamicamente un'istanza dei controlli barra multifunzione.  Nei progetti destinati a .NET Framework 3.5 i controlli barra multifunzione sono classi per le quali è possibile creare un'istanza direttamente in alcuni scenari.  Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, questi controlli sono interfacce di cui non è possibile creare istanze direttamente.  È necessario creare i controlli con i metodi forniti dall'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
 Sono disponibili due modi per accedere all'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:  
  
-   Usando la proprietà Factory della classe Ribbon.  Usare questo approccio dal codice della classe Ribbon.  
  
-   Usando il metodo Globals.Factory.GetRibbonFactory.  Usare questo approccio dal codice all'esterno della classe Ribbon.  Per altre informazioni sulla classe Globals, vedere [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 L'esempio di codice seguente dimostra come creare <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> in una classe Ribbon in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive.  
  
```vb  
Dim button As Microsoft.Office.Tools.Ribbon.RibbonButton =  
    Me.Factory.CreateRibbonButton()  
```  
  
```csharp  
Microsoft.Office.Tools.Ribbon.RibbonButton button =  
    this.Factory.CreateRibbonButton();  
```  
  
 La tabella seguente elenca i controlli creati a livello di codice e il metodo da usare per creare i controlli nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive.  
  
|CTRL|Metodo RibbonFactory da usare nei progetti [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e versioni successive|  
|----------|------------------------------------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|  
  
##  <a name="ribbonevents"></a> Gestione di eventi della barra multifunzione  
 È necessario modificare il codice che gestisce gli eventi dei controlli barra multifunzione.  Nei progetti destinati a .NET Framework 3.5 questi eventi sono gestiti dal delegato <xref:System.EventHandler%601> generico.  Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, questi eventi sono ora gestiti da altri delegati.  
  
 La tabella seguente elenca gli eventi della barra multifunzione e i delegati associati nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive.  
  
|Evento|Delegato da usare in progetti di [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e versioni successive|  
|------------|--------------------------------------------------------------------------------------------------------------------|  
|Evento <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> in una classe Ribbon generata|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|  
  
## Impostazione della posizione di un componente della barra multifunzione a livello di codice  
 È necessario modificare il codice che imposta la posizione di gruppi, schede o controlli barra multifunzione.  Nei progetti destinati a .NET Framework 3.5 è possibile usare i metodi AfterOfficeId e BeforeOfficeId della classe Microsoft.Office.Tools.Ribbon.RibbonPosition statica per assegnare la proprietà Position di un gruppo, una scheda o un controllo.  Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario accedere a questi metodi usando la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> fornita dall'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
 Sono disponibili due modi per accedere all'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:  
  
-   Usando la proprietà Factory della classe Ribbon.  Usare questo approccio dal codice della classe Ribbon.  
  
-   Usando il metodo Globals.Factory.GetRibbonFactory.  Usare questo approccio dal codice all'esterno della classe Ribbon.  Per altre informazioni sulla classe Globals, vedere [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 L'esempio di codice seguente dimostra come impostare la proprietà Position di una scheda in una classe Ribbon in un progetto destinato a .NET Framework 3.5.  
  
```vb  
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");  
```  
  
 L'esempio di codice seguente illustra la stessa attività per un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
```vb  
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");  
```  
  
## Vedere anche  
 [Migrazione di soluzioni Office a .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)  
  
  