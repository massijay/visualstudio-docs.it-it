---
title: "Aggiornamento di aree del modulo in progetti Outlook di cui si esegue la migrazione a .NET Framework 4 o a .NET Framework 4.5 | Microsoft Docs"
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
  - "progetti di Office [sviluppo per Office in Visual Studio], migrazione a .NET Framework 4"
ms.assetid: 65991e2f-4875-49f0-b21b-6a3d0175d0f4
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Aggiornamento di aree del modulo in progetti Outlook di cui si esegue la migrazione a .NET Framework 4 o a .NET Framework 4.5
  Se il framework di destinazione di un progetto di componente aggiuntivo VSTO per Outlook contenente un'area del modulo viene modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario apportare modifiche all'area del modulo generato e a qualsiasi codice che crea istanze di alcune classi di aree del modulo in fase di esecuzione.  
  
## Aggiornamento del codice dell'area del modulo generato  
 Se il framework di destinazione del progetto viene modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario modificare il codice generato dell'area del modulo. Le modifiche da apportare cambiano a seconda che le aree del modulo siano progettate in Visual Studio o importate da Outlook. Per altre informazioni sulle differenze tra questi tipi di aree del modulo, vedere [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md).  
  
#### Per aggiornare il codice generato per un'area del modulo progettata in Visual Studio  
  
1.  Aprire il file code\-behind dell'area del modulo nell'editor del codice. Il nome del file è *YourFormRegion.Designer.cs* o *YourFormRegion.Designer.vb*. Per visualizzare questo file nei progetti Visual Basic, fare clic sul pulsante **Mostra tutti i file** in **Esplora soluzioni**.  
  
2.  Modificare la dichiarazione della classe di aree del modulo in modo che derivi da <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> anziché da Microsoft.Office.Tools.Outlook.FormRegionControl.  
  
3.  Modificare il costruttore della classe di aree del modulo come illustrato negli esempi di codice seguenti.  
  
     L'esempio di codice seguente illustra il costruttore di una classe di aree del modulo in un progetto destinato a .NET Framework 3.5.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion) MyBase.New(formRegion) Me.InitializeComponent() End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion) : base(formRegion) { this.InitializeComponent(); }  
    ```  
  
     L'esempio di codice seguente illustra il costruttore di una classe di aree del modulo in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion) MyBase.New(Globals.Factory, formRegion) Me.InitializeComponent() End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion) : base(Globals.Factory, formRegion) { this.InitializeComponent(); }  
    ```  
  
4.  Modificare la firma del metodo `InitializeManifest` come illustrato di seguito. Assicurarsi di non modificare il codice nel metodo perché rappresenta le impostazioni dell'area del modulo applicate nella finestra di progettazione. Nei progetti Visual C\# è necessario espandere l'area denominata `Form Region Designer generated code` per visualizzare il metodo.  
  
     L'esempio di codice seguente illustra la firma del metodo `InitializeManifest` in un progetto destinato a .NET Framework 3.5.  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest) ' Do not change code in this method. End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest) { // Do not change code in this method. }  
    ```  
  
     L'esempio di codice seguente viene illustrata la firma del metodo `InitializeManifest` in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest, ByVal factory As Microsoft.Office.Tools.Outlook.Factory) ' Do not change code in this method. End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest, Microsoft.Office.Tools.Outlook.Factory factory) { // Do not change code in this method. }  
    ```  
  
5.  Aggiungere un nuovo elemento Area del modulo di Outlook al progetto. Aprire il file code\-behind per la nuova area del modulo, trovare le classi *YourNewFormRegion*`Factory` e `WindowFormRegionCollection` nel file, quindi copiare queste classi negli Appunti.  
  
6.  Eliminare la nuova area del modulo aggiunta al progetto.  
  
7.  Nel file code\-behind dell'area del modulo che si vuole aggiornare per lavorare nel progetto con la nuova destinazione, trovare le classi *YourOriginalFormRegion*`Factory` e `WindowFormRegionCollection` e sostituirle con il codice copiato dalla nuova area del modulo.  
  
8.  Nelle classi *YourNewFormRegion*`Factory` e `WindowFormRegionCollection` cercare tutti i riferimenti alla classe *YourNewFormRegion* e modificarli in modo che facciano riferimento alla classe *YourOriginalFormRegion*. Ad esempio, se l'area del modulo che si vuole aggiornare è denominata `SalesDataFormRegion` e la nuova area del modulo creata nel passaggio 5 è denominata `FormRegion1`, impostare tutti i riferimenti di `FormRegion1` a `SalesDataFormRegion`.  
  
#### Per aggiornare il codice generato per un'area del modulo importata da Outlook  
  
1.  Aprire il file code\-behind dell'area del modulo nell'editor del codice. Il nome del file è *YourFormRegion.Designer.cs* o *YourFormRegion.Designer.vb*. Per visualizzare questo file nei progetti Visual Basic, fare clic sul pulsante **Mostra tutti i file** in **Esplora soluzioni**.  
  
2.  Modificare la dichiarazione della classe di aree del modulo in modo che derivi da <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> anziché da Microsoft.Office.Tools.Outlook.ImportedFormRegion.  
  
3.  Modificare il costruttore della classe di aree del modulo come illustrato negli esempi di codice seguenti.  
  
     L'esempio di codice seguente illustra il costruttore di una classe di aree del modulo in un progetto destinato a .NET Framework 3.5.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion) MyBase.New(formRegion) End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion) : base(formRegion) { this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing); this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed); }  
    ```  
  
     L'esempio di codice seguente illustra la firma del costruttore di una classe di aree del modulo in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion) MyBase.New(Globals.Factory, formRegion) End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion) : base(Globals.Factory, formRegion) { this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing); this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed); }  
    ```  
  
4.  Per ogni riga di codice nel metodo `InitializeControls` che inizializza un controllo nella classe di aree del modulo, modificare il codice come illustrato di seguito.  
  
     L'esempio di codice seguente illustra come inizializzare un controllo in un progetto destinato a .NET Framework 3.5. In questo codice, il metodo GetFormRegionControl ha un parametro di tipo che specifica il tipo del controllo restituito.  
  
    ```vb  
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")  
    ```  
  
    ```csharp  
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");  
    ```  
  
     L'esempio di codice seguente illustra come inizializzare un controllo in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In questo codice, il metodo <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> non ha un parametro di tipo. È necessario sottoporre a cast il valore restituito nel tipo del controllo che si vuole inizializzare.  
  
    ```vb  
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)  
    ```  
  
    ```csharp  
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");  
    ```  
  
5.  Aggiungere un nuovo elemento Area del modulo di Outlook al progetto. Aprire il file code\-behind per la nuova area del modulo, trovare le classi *YourNewFormRegion*`Factory` e `WindowFormRegionCollection` nel file, quindi copiare queste classi negli Appunti.  
  
6.  Eliminare la nuova area del modulo aggiunta al progetto.  
  
7.  Nel file code\-behind dell'area del modulo che si vuole aggiornare per lavorare nel progetto con la nuova destinazione, trovare le classi *YourOriginalFormRegion*`Factory` e `WindowFormRegionCollection` e sostituirle con il codice copiato dalla nuova area del modulo.  
  
8.  Nelle classi *YourNewFormRegion*`Factory` e `WindowFormRegionCollection` cercare tutti i riferimenti alla classe *YourNewFormRegion* e modificarli in modo che facciano riferimento alla classe *YourOriginalFormRegion*. Ad esempio, se l'area del modulo che si vuole aggiornare è denominata `SalesDataFormRegion` e la nuova area del modulo creata nel passaggio 5 è denominata `FormRegion1`, impostare tutti i riferimenti di `FormRegion1` a `SalesDataFormRegion`.  
  
## Creazione di istanze delle classi di aree del modulo  
 È necessario modificare il codice che crea dinamicamente istanze di alcune classi di aree del modulo. Nei progetti destinati a .NET Framework 3.5, è possibile creare direttamente istanze di classi di aree del modulo come Microsoft.Office.Tools.Outlook.FormRegionManifest. Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, queste classi sono interfacce di cui non è possibile creare istanze direttamente.  
  
 Se il framework di destinazione del progetto viene modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario creare istanze delle interfacce usando i metodi forniti dalla proprietà di Globals.Factory. Per altre informazioni sulla proprietà Globals.Factory, vedere [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 La tabella seguente elenca i tipi di area del modulo e il metodo da usare per creare istanze dei tipi nei progetti destinati [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive.  
  
|Tipo|Metodo factory da usare|  
|----------|-----------------------------|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|  
  
## Vedere anche  
 [Migrazione di soluzioni Office a .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)  
  
  