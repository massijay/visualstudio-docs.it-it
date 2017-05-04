---
title: "Sicurezza per le soluzioni SharePoint | Microsoft Docs"
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
  - "sicurezza [Sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, sicurezza"
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Sicurezza per le soluzioni SharePoint
  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono incorporate le funzionalità elencate di seguito che consentono di migliorare la sicurezza delle applicazioni di SharePoint.  
  
## Voci di controllo sicure  
 Ogni elemento di progetto SharePoint creato in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include una proprietà **Voci di controllo sicure** che rappresenta una raccolta di controlli sicuri.  La relativa sottoproprietà **Sicuro** consente di specificare i controlli considerati sicuri.  Per ulteriori informazioni, vedere [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [Specificare Web part sicuri](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## Attributo AllowPartiallyTrustedCallers  
 Per impostazione predefinita, solo le applicazioni considerate completamente attendibili dal sistema di sicurezza dall'accesso di codice del runtime possono accedere a un assembly di codice gestito condiviso.  Se si contrassegna un assembly completamente attendibile con l'attributo AllowPartiallyTrustedCallers, si consente agli assembly parzialmente attendibili di accedervi.  
  
 L'attributo AllowPartiallyTrustedCallers viene aggiunto a qualsiasi soluzione SharePoint che non venga distribuita nella Global Assembly Cache \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\) di sistema,  incluse le soluzioni create mediante sandbox o distribuite nella directory Bin dell'applicazione di SharePoint.  Per ulteriori informazioni, vedere [Versione 1 Modifiche di sicurezza per Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) e [Distribuzione di Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## Proprietà Sicurezza script  
 Con attacco *script injection* si intende l'inserimento di codice potenzialmente dannoso all'interno di controlli o pagine Web.  Per poter proteggere i siti di SharePoint 2010 da questi tipi di attacchi, per impostazione predefinita i collaboratori non possono visualizzare né modificare le Web part o le relative proprietà.  Questo comportamento viene controllato mediante un attributo SafeControl denominato SafeAgainstScript.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] impostare questo attributo nella sottoproprietà **Sicurezza script** della proprietà **Voci di controllo sicure** di un elemento del progetto.  Per ulteriori informazioni, vedere [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [Procedura: contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## Controllo dell'account utente di Vista e Windows 7  
 In [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] è incorporata una funzionalità di sicurezza nota come Controllo dell'account utente.  Per sviluppare soluzioni SharePoint per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nei sistemi [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], Controllo dell'account utente richiede l'esecuzione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come amministratore di sistema.  Dal menu **Start**, aprire il menu di scelta rapida [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], quindi scegliere **Esegui come amministratore**.  
  
 Per configurare il collegamento [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per funzionare sempre come amministratore, aprire il menu di scelta rapida, scegliere **Proprietà**, scegliere il pulsante **Avanzate** nella finestra di dialogo **Proprietà** quindi selezionare la casella di controllo **Esegui come amministratore**.  
  
 Per ulteriori informazioni, vedere [Informazioni e configurazione di Controllo account utente in Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476) e [Controllo dell'account utente di Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## Considerazioni sulle autorizzazioni di SharePoint  
 Per sviluppare soluzioni SharePoint, è necessario disporre delle autorizzazioni per eseguire ed effettuare il debug delle soluzioni SharePoint.  Prima di poter testare una soluzione SharePoint, effettuare i passaggi riportati di seguito per assicurarsi di disporre delle autorizzazioni necessarie:  
  
1.  Aggiungere il proprio account utente come amministratore nel sistema.  
  
2.  Aggiungere l'account utente come amministratore farm per il server SharePoint.  
  
    1.  Nell'amministrazione centrale di SharePoint 2010 fare clic sul collegamento **Gestisci gruppo amministratori farm**.  
  
    2.  Nella pagina **Amministratori farm**, scegliere l'opzione **Nuova**  
  
3.  Aggiungere l'account utente al gruppo WSS\_ADMIN\_WPG.  
  
## Risorse di sicurezza aggiuntive  
 Per ulteriori informazioni sui problemi relativi alla sicurezza, vedere gli argomenti elencati di seguito.  
  
### Sicurezza in Visual Studio  
  
-   [Sicurezza e autorizzazioni utente](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Sicurezza nel codice nativo e nel codice .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Sicurezza in .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### Sicurezza in SharePoint  
  
-   [Amministrazione e sicurezza di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [Centro delle risorse di sicurezza in Sharepoint](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Protezione delle Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Miglioramento della sicurezza delle applicazioni Web: Minacce e contromisure](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### Sicurezza generale  
  
-   [MSDN Security Development Lifecycle](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Come compilare applicazioni ASP.NET protette: autenticazione, autorizzazione e comunicazioni protette \(la pagina potrebbe essere in inglese\)](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## Vedere anche  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  