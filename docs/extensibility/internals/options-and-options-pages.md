---
title: "Opzioni e le pagine di opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Opzioni pagine [Visual Studio SDK], gestite pacchetto framework supporto degli strumenti"
  - "framework pacchetto gestito, il supporto di pagine di opzioni del menu Strumenti"
  - "supporto, pagine delle opzioni strumenti"
  - "Pagine delle opzioni [Visual Studio SDK], layout degli strumenti"
  - "Pagine delle opzioni degli strumenti [Visual Studio SDK], gli attributi"
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 34
caps.handback.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
---
# Opzioni e le pagine di opzioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fare clic su **Opzioni** sul **strumenti** menu viene aperto il **Opzioni** la finestra di dialogo. Le opzioni nella finestra di dialogo vengono definiti collettivamente come pagine di opzioni. Il controllo struttura ad albero nel riquadro di spostamento include le categorie delle opzioni e ogni categoria dispone di pagine di opzioni. Quando si seleziona una pagina, le relative opzioni vengono visualizzate nel riquadro di destra. Queste pagine consentono di modificare i valori delle opzioni che determinano lo stato di un package VS.  
  
## Supporto per le pagine di opzioni  
 La <xref:Microsoft.VisualStudio.Shell.Package> classe offre supporto per la creazione di pagine di opzioni e le categorie di opzioni. La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa una pagina di opzioni.  
  
 L'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage> offre le proprietà pubbliche di un utente in una griglia delle proprietà generica. È possibile personalizzare questo comportamento eseguendo l'override di diversi metodi della pagina per creare una pagina di opzioni personalizzate che è un'interfaccia utente \(UI\). Per altre informazioni, vedere [Creazione di una pagina di opzioni](../../extensibility/creating-an-options-page.md).  
  
 Il <xref:Microsoft.VisualStudio.Shell.DialogPage> implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, che fornisce la persistenza per le pagine di opzioni e anche per le impostazioni utente. Le implementazioni predefinite della <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> e <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> metodi rendere persistenti le modifiche alle proprietà in una sessione utente del Registro di sistema se la proprietà può essere convertita in e da una stringa.  
  
## Percorso del Registro di sistema pagina Opzioni  
 Per impostazione predefinita, il percorso del Registro di sistema di proprietà gestite da una pagina di opzioni viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la parola DialogPage e il nome del tipo della classe delle pagine di opzioni. Classe di pagina di opzioni, ad esempio, potrebbe essere definita come segue.  
  
 [!code-cs[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Se il <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> è HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp, le coppie di nome e il valore di proprietà sono sottochiavi del HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\DialogPage\\Company.OptionsPage.OptionsPageGeneral.  
  
 Il percorso del Registro di sistema della pagina Opzioni viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la parola, ToolsOptionsPages e le opzioni pagina categoria e il nome. Ad esempio, se la pagina di opzioni personalizzato dispone della categoria, le pagine di opzioni personali e <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> è HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, quindi nella pagina Opzioni dispone della chiave del Registro di sistema, HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\ToolsOptionsPages\\My opzione Pages\\Custom.  
  
## Strumenti\/opzioni di Layout e gli attributi di pagina  
 Il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo determina il raggruppamento delle pagine di opzioni personalizzate in categorie nella struttura ad albero del **Opzioni** la finestra di dialogo. Il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo associa una pagina Opzioni di VSPackage che fornisce l'interfaccia. Si consideri il frammento di codice riportato di seguito.  
  
 [!code-cs[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Questo codice dichiara che MyPackage fornisce due pagine di opzioni, OptionsPageGeneral e OptionsPageCustom. Nel **Opzioni** vengono visualizzate entrambe le opzioni della finestra di dialogo nel **le pagine di opzioni personali** categoria come **Generale** e **personalizzato**, rispettivamente.  
  
## Gli attributi di opzione e il Layout  
 L'interfaccia utente \(UI\) che fornisce la pagina determina l'aspetto delle opzioni in una pagina di opzioni personalizzate. Il layout, assegnazione di etichette e la descrizione delle opzioni in una pagina di opzioni generiche sono determinati dai seguenti attributi:  
  
-   <xref:System.ComponentModel.CategoryAttribute> Determina la categoria dell'opzione.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> Determina il nome visualizzato dell'opzione.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> Determina la descrizione dell'opzione.  
  
    > [!NOTE]
    >  Attributi equivalenti, SRCategory, LocDisplayName e SRDescription, utilizzare risorse di tipo stringa per la localizzazione e sono definiti nel [esempio progetto gestito](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Si consideri il frammento di codice riportato di seguito.  
  
 [!code-cs[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 L'opzione OptionInteger viene visualizzata nella pagina Opzioni **opzione intero** nel **opzioni personali** categoria. Se l'opzione è selezionata, la descrizione, **l'opzione intero**, viene visualizzato nella casella Descrizione.  
  
## L'accesso alle pagine di opzioni da un altro VSPackage  
 Un package VS che gestisce una pagina di opzioni a livello di codice accessibile da un altro VSPackage utilizzando il modello di automazione. Nel codice seguente, ad esempio, un VSPackage viene registrato come una pagina di opzioni di hosting.  
  
 [!code-cs[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 Nel frammento di codice seguente ottiene il valore di OptionInteger da MyOptionPage:  
  
 [!code-cs[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Quando il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo registra una pagina di opzioni, la pagina viene registrata in AutomationProperties chiave se il `SupportsAutomation` argomento dell'attributo è `true`. Automazione esamina questa voce del Registro di sistema per individuare il VSPackage associato e automazione quindi accede alla proprietà tramite la pagina Opzioni ospitato, in questo caso, My pagina della griglia.  
  
 Il percorso del Registro di sistema della proprietà di automazione è determinato dalla combinazione <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la parola AutomationProperties e le opzioni pagina categoria e il nome. Ad esempio, se la pagina di opzioni dispone della categoria di categoria personale, il nome della pagina di griglia personale e <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, quindi la proprietà dispone della chiave del Registro di sistema, pagina della griglia Category\\My HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\AutomationProperties\\My.  
  
> [!NOTE]
>  Il nome canonico, pagina di griglia Category.My personale, è il valore della sottochiave del nome di questa chiave.