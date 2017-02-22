---
title: "Organizzare gli oggetti in contenitori nella finestra di progettazione XAML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Organizzare gli oggetti in contenitori nella finestra di progettazione XAML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si supponga di voler impostare la posizione degli oggetti, quali immagini, pulsanti e video, in una pagina.  È probabile che si preferisca organizzarli in righe e colonne, su un'unica riga disposti orizzontalmente o verticalmente o impostare per ognuno una posizione fissa.  
  
 Dopo aver dedicato tempo all'organizzazione degli oggetti nella pagina, è possibile passare alla scelta di un pannello di layout.  Inizialmente in tutte le pagine è presente un pannello di layout in quanto viene usato per aggiungervi gli oggetti.  Il pannello di layout predefinito è di tipo **Grid**, ma è possibile modificarlo.  
  
 I pannelli di layout non vengono però usati unicamente per organizzare gli oggetti in una pagina,  ma anche per progettare tenendo conto di risoluzioni e dimensioni dello schermo diverse.  Quando gli utenti eseguono l'app, tutti gli elementi presenti in un pannello di layout vengono ridimensionati in base all'area dello schermo del dispositivo.  Se naturalmente si preferisce che gli elementi non vengano ridimensionati, è possibile disattivare questo comportamento per una parte o per l'intero layout,  usando a tale scopo le proprietà height e width.  
  
 Oltre a una descrizione dei pannelli e dei controlli di layout disponibili, questa pagina include i collegamenti a brevi video introduttivi su questi elementi.  
  
> [!NOTE]
>  Alcuni dei video possono fare riferimento a Blend o Expression Blend, che usano la stessa finestra di progettazione XAML di Visual Studio e Blend per Visual Studio.  
  
## Pannelli di layout  
 Per definire inizialmente la pagina, scegliere uno dei seguenti pannelli di layout.  La pagina può comunque contenere più pannelli di layout.  Si può infatti iniziare con un pannello di layout di tipo **Grid** e quindi aggiungerne uno di tipo **StackPanel** a un'area del pannello **Grid** in modo da disporre i controlli verticalmente in tale elemento.  
  
 I seguenti pannelli di layout sono quelli più usati, ma ne esistono altri.  Tutti i controlli sono disponibili nel pannello **Asset**.  
  
-   [Griglia](#Grid)  
  
-   [UniformGrid](#Uniform)  
  
-   [Canvas](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a> Griglia  
 Consente di disporre gli oggetti in righe e colonne.  
  
 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Uso delle griglie](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
###  <a name="Uniform"></a> UniformGrid  
 Consente di disporre gli oggetti in aree della griglia uguali o uniformi.  Questo pannello è molto utile per definire la disposizione di un elenco di immagini.  
  
 \(Disponibile solo per i progetti WPF\)  
  
 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Uso di un pannello UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
###  <a name="Canvas"></a> Canvas  
 Consente di disporre gli oggetti nel modo desiderato.  Quando gli utenti eseguono l'app, a questi elementi verranno assegnate posizioni fisse sullo schermo.  
  
 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Uso del pannello Canvas](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
###  <a name="Stack"></a> StackPanel  
 Consente di disporre gli oggetti su un'unica riga orizzontalmente o verticalmente.  
  
 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Uso di StackPanel e WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Wrap"></a> WrapPanel  
 Consente di disporre gli oggetti in modo sequenziale da sinistra verso destra.  Quando il pannello esaurisce lo spazio all'estremità destra, *sposta* il contenuto sulla riga successiva e così via da sinistra verso destra e dall'alto verso il basso.  È anche possibile impostare per un pannello di questo tipo l'orientamento verticale in modo che gli oggetti vengano spostati dall'alto verso il basso e da sinistra verso destra.  
  
 \(Disponibile solo per i progetti WPF\)  
  
 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Uso di StackPanel e WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Dock"></a> DockPanel  
 È anche possibile disporre gli oggetti in modo che rimangano *ancorati* a un bordo del pannello.  
  
 \(Disponibile solo per i progetti WPF\)  
  
 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [WPF \- DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## Controlli di layout  
 È possibile aggiungere oggetti anche ai controlli di layout,  che pur includendo un minor numero di funzionalità rispetto a un pannello di layout, possono risultare utili per determinati scenari.  
  
 I seguenti controlli di layout sono quelli più usati, ma ne esistono altri.  Tutti i controlli sono disponibili nel pannello **Asset**.  
  
-   [Bordo](#Border)  
  
-   [Popup](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [UniformGrid](#Uniform)  
  
-   [Viewbox](#View)  
  
###  <a name="Border"></a> Bordo  
 Consente di creare un bordo, uno sfondo o entrambi intorno a un oggetto.  È possibile aggiungere un solo oggetto a un controllo **Border**.  Per applicare un bordo o uno sfondo a più oggetti, aggiungere a **Border** il pannello di layout,  quindi aggiungere gli oggetti al pannello o al controllo.  
  
 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Uso di bordi](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
###  <a name="Popup"></a> Popup  
 Consente di visualizzare informazioni o opzioni destinate agli utenti in una finestra.  È possibile aggiungere un solo oggetto a un controllo **Popup**.  Per impostazione predefinita, un controllo **Popup** contiene un pannello di layout **Grid**, ma è possibile modificare questa impostazione.  
  
###  <a name="Scroll"></a> ScrollViewer  
 Consente agli utenti di scorrere verso il basso in una pagina o un'area di una pagina.  Dal momento che è possibile aggiungere un solo oggetto a un controllo **ScrollViewer**, è preferibile aggiungere un pannello di layout, come **Grid** o **StackPanel**.  
  
###  <a name="View"></a> Viewbox  
 Consente di ridimensionare gli oggetti come con un controllo zoom.  È possibile aggiungere un solo oggetto a un controllo **Viewbox**.  Se si vuole applicare questo effetto a più oggetti, aggiungere un pannello di layout a **ViewBox** e quindi aggiungere i controlli a tale pannello.  
  
 \(Disponibile solo per i progetti WPF\)  
  
## Vedere anche  
 [Utilizzo di elementi in XAML Designer](../designers/working-with-elements-in-xaml-designer.md)   
 [Creazione di un'interfaccia utente tramite XAML Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)