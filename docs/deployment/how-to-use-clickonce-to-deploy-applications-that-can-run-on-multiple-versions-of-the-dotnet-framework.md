---
title: "How to: Use ClickOnce to Deploy Applications That Can Run on Multiple Versions of the .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce applications, multiple .NET Framework versions"
  - "ClickOnce deployment, multiple .NET Framework versions"
  - "deploying applications [ClickOnce], multiple .NET Framework versions"
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Use ClickOnce to Deploy Applications That Can Run on Multiple Versions of the .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile distribuire un'applicazione destinata a più versioni di .NET Framework tramite la tecnologia di distribuzione ClickOnce.  Ciò richiede che si generino e aggiornino i manifesti dell'applicazione e della distribuzione.  
  
> [!NOTE]
>  Prima di modificare l'applicazione in modo che sia destinata a più versioni di .NET Framework, è necessario verificare che l'applicazione venga eseguita con più versioni di .NET Framework.  Il Common Language Runtime della versione di [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] è diverso da quello di .NET Framework 2.0, .NET Framework 3.0 e .NET Framework 3.5.  
  
 Questo processo richiede l'esecuzione dei passaggi seguenti:  
  
1.  Generare i manifesti dell'applicazione e della distribuzione.  
  
2.  Modificare il manifesto della distribuzione in modo da elencare le diverse versioni di .NET Framework.  
  
3.  Modificare il file app.config in modo da elencare le versioni del runtime di .NET Framework compatibili.  
  
4.  Modificare il manifesto dell'applicazione in modo da contrassegnare gli assembly dipendenti come assembly di .NET Framework.  
  
5.  Firmare il manifesto dell'applicazione.  
  
6.  Aggiornare e firmare il manifesto della distribuzione.  
  
### Per generare i manifesti dell'applicazione e della distribuzione  
  
-   Utilizzare la Pubblicazione guidata o la pagina Pubblica di Progettazione progetti per pubblicare l'applicazione e generare i file dei manifesti dell'applicazione e della distribuzione.  Per ulteriori informazioni, vedere [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md) o [Pagina Pubblica, Progettazione progetti](../ide/reference/publish-page-project-designer.md).  
  
### Per modificare il manifesto della distribuzione in modo da elencare le diverse versioni di .NET Framework  
  
1.  Nella directory di pubblicazione aprire il manifesto della distribuzione mediante l'editor XML in Visual Studio.  L'estensione di file del manifesto della distribuzione è .application.  
  
2.  Sostituire il codice XML compreso tra gli elementi `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` e `</compatibleFrameworks>` con codice XML che elenca le versioni di .NET Framework supportate per l'applicazione.  
  
     Nella tabella seguente vengono illustrate alcune delle versioni di .NET Framework disponibili e il codice XML corrispondente che è possibile aggiungere al manifesto della distribuzione.  
  
    |Versione di .NET Framework|XML|  
    |--------------------------------|---------|  
    |4 client|\<framework targetVersion\="4.0" profile\="Client" supportedRuntime\="4.0.30319" \/\>|  
    |4 completa|\<framework targetVersion\="4.0" profile\="Full" supportedRuntime\="4.0.30319" \/\>|  
    |3.5 client|\<framework targetVersion\="3.5" profile\="Client" supportedRuntime\="2.0.50727" \/\>|  
    |3.5 completa|\<framework targetVersion\="3.5" profile\="Full" supportedRuntime\="2.0.50727" \/\>|  
    |3.0|\<framework targetVersion\="3.0" supportedRuntime\="2.0.50727" \/\>|  
  
### Per modificare il file app.config in modo da elencare le versioni del runtime di .NET Framework compatibili  
  
1.  In Esplora soluzioni aprire il file App.config mediante l'editor XML in Visual Studio.  
  
2.  Sostituire \(o aggiungere\) il codice XML compreso tra gli elementi `<startup>` e `</startup>` con codice XML che elenca i runtime di .NET Framework supportati per l'applicazione.  
  
     Nella tabella seguente vengono illustrate alcune delle versioni di .NET Framework disponibili e il codice XML corrispondente che è possibile aggiungere al manifesto della distribuzione.  
  
    |Versione del runtime di .NET Framework|XML|  
    |--------------------------------------------|---------|  
    |4 client|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0,Profile\=Client" \/\>|  
    |4 completa|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0" \/\>|  
    |3.5 completa|\<supportedRuntime version\="v2.0.50727"\/\>|  
    |3.5 client|\<supportedRuntime version\="v2.0.50727" sku\="Client"\/\>|  
  
### Per modificare il manifesto dell'applicazione in modo da contrassegnare gli assembly dipendenti come assembly di .NET Framework  
  
1.  Nella directory di pubblicazione aprire il manifesto dell'applicazione mediante l'editor XML in Visual Studio.  L'estensione di file del manifesto della distribuzione è .manifest.  
  
2.  Aggiungere `group="framework"` al codice XML della dipendenza per gli assembly sentinel \(`System.Core`, `WindowsBase`, `Sentinel.v3.5Client` e `System.Data.Entity`\).  Ad esempio, il codice XML potrebbe essere simile al seguente:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Aggiornare il numero della versione dell'elemento `<assemblyIdentity>` per Microsoft.Windows.CommonLanguageRuntime al numero della versione di .NET Framework che rappresenta il minimo comune denominatore.  Ad esempio, se l'applicazione è destinata a .NET Framework 3.5 e a [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], utilizzare il numero di versione 2.0.50727.0. Il codice XML dovrebbe essere simile al seguente:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### Per aggiornare e firmare nuovamente i manifesti dell'applicazione e della distribuzione  
  
-   Aggiornare e firmare nuovamente i manifesti dell'applicazione e della distribuzione.  Per ulteriori informazioni, vedere [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Vedere anche  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks\> Element](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [\<dependency\> Element](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [Schema dei file di configurazione](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)