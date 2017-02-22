---
title: "Modelli di sito Web supporto tecnico | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Abbiamo i progetti, modelli di sito"
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Modelli di sito Web supporto tecnico
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

il progetto di sito Web e i modelli di elemento di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sono disponibili stub elemento personalizzabili e riutilizzabili di progetto di sito Web che velocizzare il processo di sviluppo rimuovendo la necessità di creare nuovi progetti di sito Web ed elementi da zero.  per ulteriori informazioni sui modelli di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , vedere [Creazione di un progetto e di modelli di elemento personalizzati](../../ide/creating-project-and-item-templates.md).  
  
## Cartella dei modelli di progetto  
 I modelli del modello di progetto Web in genere vengono installati*percorso di installazione di Visual Studio*\[\] in \\Common7\\IDE\\ProjectTemplates\\Web \\, ciascuno in una sottocartella denominata in base al linguaggio di programmazione Web.  
  
## File di progetto  
 L'ambiente di sviluppo integrato di  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\(IDE\) richiede un'estensione di file di progetto come per eseguire il mapping di un modello al tipo di progetto corrente.  Poiché i progetti Web non dispongono di un file di progetto, l'estensione di file di progetto fittizia .webproj è registrata per supportare questa.  
  
 Facoltativamente, una stringa del nome della lingua è possibile aggiungere al modello per consentire al sistema di progetto Web per impostare la proprietà predefinita del linguaggio nella finestra di dialogo di **Aggiungi nuovo elemento** per gli elementi basati sul modello.  La stringa deve essere la prima riga del file e deve corrispondere al nome registrato in AddItemLanguageName nella registrazione del motore di Intellisense che il nome registrato nel sottotipo di progetto \(VsTemplate\).  Per ulteriori informazioni, vedere [Attributi di supporto del sito Web](../../extensibility/internals/web-site-support-attributes.md).  
  
 Se la stringa non è presente, il sistema di progetto Web tenterà di determinare la lingua predefinita basata sull'attributo di linguaggio e sulle estensioni di file delle pagine aggiunte al progetto Web dal modello di progetto.  
  
## Modelli di progetto  
 I modelli di progetto di sito Web vengono utilizzati per compilare i nuovi siti Web in risposta al comando di **nuovo sito Web** il menu File.  tre tipi di progetto di sito Web sono attualmente supportati:  
  
-   progetti di sito Web vuoti  
  
-   Progetti di sito Web  
  
-   Progetti di servizi Web  
  
### svuotare i progetti di sito Web  
 Questi file viene creato un nuovo sito Web vuoto in risposta al comando di **sito Web vuoto** , che è disponibile dopo avere fa riferimento a **nuovo sito Web** il menu File:  
  
-   EmptyWeb.vstemplate  
  
     Il file modello che consentono la creazione di un nuovo sito Web vuoto.  
  
-   EmptyWeb.webproj  
  
     Questo è un elemento del sistema del modello di progetto.  It satisfies the project file reference in the EmptyWeb.vstemplate file.  
  
### web.config  
 Questi file viene creato un nuovo sito Web in risposta al comando di **Sito Web ASP.NET** , che è disponibile dopo avere fa riferimento a **nuovo sito Web** il menu File:  
  
-   Default.aspx  
  
     La home page predefinito per il nuovo sito Web.  L'attributo di linguaggio specifica il linguaggio e l'attributo codebehind CodeFile specifica il file dipendente che contiene il codice di codebehind associato a questa pagina.  
  
-   Default.aspx.*estensione*  
  
     Il file dipendente che contiene il codice di codebehind per la home page predefinito.  Il linguaggio di codebehind determina *estensione* di questo file.  
  
-   web.config  
  
     Il file di configurazione radice web.site.  
  
-   WebApplication.vstemplate  
  
     Il file modello che determina il contenuto della soluzione del sito Web e forza la creazione della cartella App\_Data.  
  
-   WebApplication.webproj  
  
     Questo è un elemento del sistema del modello di progetto.  Soddisfa il riferimento di file di progetto nel file di WebApplication.vstemplate.  
  
### Progetti di servizi Web  
 Questi file viene creato un nuovo sito Web in risposta al comando di **Servizio Web ASP.NET** disponibile una volta fa riferimento a **nuovo sito Web** il menu File:  
  
-   Service.asmx  
  
     la pagina HTML per il nuovo servizio Web.  L'attributo di linguaggio specifica il linguaggio di codebehind e l'attributo CodeBehind specifica il file dipendente che contiene il codice di codebehind associato a questo servizio.  
  
-   servizio. *estensione*  
  
     il file dipendente che implementa la classe di servizio.  Il linguaggio di codebehind determina *estensione* di questo file.  
  
-   web.config  
  
-   Il file di configurazione radice web.site.  
  
-   WebService.vstemplate  
  
     Il file modello che determina il contenuto della soluzione del sito Web e forza la creazione App\_Data e delle cartelle App\_Code.  il servizio. il file di*estensione* viene copiato nella cartella App\_Code.  
  
-   WebService.webproj  
  
     Questo è un elemento del sistema del modello di progetto.  Soddisfa il riferimento di file di progetto nel file di WebService.vstemplate.  
  
## Cartella del modello di elemento di progetto  
 I modelli Web del modello di elemento di progetto in genere vengono installati*percorso di installazione di Visual Studio*\[\] in \\Common7\\IDE\\ItemTemplates\\Web \\, ciascuno in una sottocartella denominata in base al linguaggio di programmazione Web.  
  
## Modelli di elementi di progetto  
 I modelli di elemento di progetto di sito Web vengono utilizzati per aggiungere nuove pagine Web a un sito Web in risposta al comando di **aggiungere l'elemento esistente** .  questi tipi di pagine Web sono attualmente supportati:  
  
-   nuova classe  
  
-   Nuova pagina HTML  
  
-   Il Web Form  
  
-   nuova pagina master  
  
### nuova classe  
 Questo modello consente di creare un nuovo file di origine che definisce una classe vuota in risposta al comando di **Aggiungere una nuova classe** .  
  
-   classe. *estensione*  
  
     il file di origine che implementa la classe vuota.  Il linguaggio di codebehind determina *estensione* di questo file.  
  
-   Class.vstemplate  
  
     Il file modello che crea il file di origine e determina il contenuto.  
  
### New HTML Page  
 Questo modello consente di creare una nuova pagina Web in risposta al comando di **Aggiungere una nuova pagina HTML** .  
  
-   HTMLPage.htm  
  
     Il contenuto iniziale della pagina Web.  La pagina Web non dispone in genere di file dipendente codebehind associato.  Per creare una pagina intelligente con associato un file di codebehind, utilizzare il modello Web Form anziché.  
  
-   HTMLPage.vstemplate  
  
     Il file modello che crea la pagina Web e determina il contenuto.  
  
### nuovo WebForm  
 Questo modello consente di creare una nuova pagina Web intelligente in risposta al comando di **aggiungere il nuovo Web Form** .  
  
 Per creare un file di origine dipendente codebehind, **Codice del posto in file separato**selezionato.  In caso contrario, chiamare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> del servizio di linguaggio per ottenere un elemento il colore.  
  
 Per creare una pagina di contenuto per una pagina master selezionata, **pagina master selezionata**selezionato.  
  
-   WebForm.aspx  
  
     Il contenuto iniziale della pagina Web.  La pagina Web non dispone di un file dipendente codebehind associato.  
  
-   WebForm\_cb.aspx  
  
     Il contenuto iniziale della pagina Web.  Questa pagina Web dispone di un file dipendente codebehind associato.  
  
-   Codebehind. *estensione*  
  
     Il file dipendente che implementa la classe del webform.  Il linguaggio di codebehind determina *estensione* di questo file.  
  
-   ContentPage.aspx  
  
     Il contenuto iniziale della pagina Web come pagina contenuto.  La pagina Web non dispone di un file dipendente codebehind associato.  
  
-   ContentPage\_cb.aspx  
  
     Il contenuto iniziale della pagina Web come pagina contenuto.  Questa pagina Web dispone di un file dipendente codebehind associato.  
  
-   WebForm.vstemplate  
  
     Il file modello che determina il contenuto di una nuova pagina Web e del relativo file dipendente, se disponibile.  
  
### nuova pagina master  
 This template creates a new master page in response to the **Add New Master Page** command.  
  
 Per creare un file di origine dipendente codebehind, **Codice del posto in file separato**selezionato.  In caso contrario, chiamare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> del servizio di linguaggio per ottenere un elemento il colore.  
  
-   MasterPage.master  
  
     Il contenuto iniziale della pagina master.  Questa pagina master non dispone di un file dipendente codebehind associato.  
  
-   MasterPage\_cb.master  
  
     Il contenuto iniziale della pagina master.  Questa pagina master corrisponde un file dipendente codebehind associato.  
  
-   Codebehind.*estensione*  
  
     Il file dipendente che implementa la classe della pagina master.  Il linguaggio di codebehind determina *estensione* di questo file.  
  
-   MasterPage.vstemplate  
  
     Il file modello che determina il contenuto della nuova pagina master e del relativo file dipendente, se disponibile.  
  
## Vedere anche  
 [Sito Web di supporto](../../extensibility/internals/web-site-support.md)