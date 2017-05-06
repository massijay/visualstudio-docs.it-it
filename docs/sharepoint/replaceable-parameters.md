---
title: "Parametri sostituibili"
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
  - "parametri sostituibili [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, parametri sostituibili"
  - "sviluppo per SharePoint in Visual Studio, token"
  - "token [sviluppo per SharePoint in Visual Studio]"
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Parametri sostituibili
  I parametri sostituibili, o *token*, possono essere utilizzati nei file di progetto per fornire valori agli elementi di soluzione SharePoint i cui valori effettivi non sono noti in fase di progettazione.  Sono simili in funzione ai token di modello standard [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Per ulteriori informazioni, vedere [Parametri di template](../ide/template-parameters.md).  
  
## Formato dei token  
 I token iniziano e terminano con un segno di dollaro \($\).  Qualsiasi token utilizzato viene sostituito con valori effettivi quando, in fase di distribuzione, un progetto viene assemblato in un file del pacchetto della soluzione SharePoint \(con estensione wsp\).  Ad esempio, il token **$SharePoint.Package.Name$** potrebbe essere risolto nella stringa "Pacchetto di SharePoint di prova".  
  
## Regole dei token  
 Ai token si applicano le regole seguenti:  
  
-   I token possono essere specificati in qualsiasi punto di una riga.  
  
-   I token non possono estendersi su più righe.  
  
-   È possibile specificare più volte lo stesso token sulla medesima riga e nello stesso file.  
  
-   È possibile specificare token diversi sulla stessa riga.  
  
 I token che non rispettano queste regole vengono ignorati senza previa visualizzazione di avvisi o errori.  
  
 La sostituzione dei token con valori stringa viene immediatamente eseguita dopo la trasformazione del manifesto, consentendo pertanto ai modelli di manifesto modificati da un utente di utilizzare token.  
  
### Risoluzione dei nomi dei token  
 Nella maggior parte dei casi, un token viene risolto in un valore specifico indipendentemente dall'elemento che lo contiene.  Tuttavia, se il token è correlato a un pacchetto o una funzionalità, il relativo valore dipende dall'elemento che lo contiene.  Ad esempio, se una funzionalità si trova nel pacchetto A, il token `$SharePoint.Package.Name$` viene risolto nel valore "Pacchetto A". Se la stessa funzionalità si trova nel pacchetto B, `$SharePoint.Package.Name$` viene risolto in "Pacchetto B".  
  
## Elenco di token  
 Nella tabella seguente sono elencati i token disponibili.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Nome del file di progetto contenitore, ad esempio "NewProj.csproj".|  
|$SharePoint.Project.FileNameWithoutExtension$|Nome del file di progetto contenitore senza estensione.  Ad esempio, "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Nome visualizzato \(nome sicuro\) dell'assembly di output del progetto contenitore.|  
|$SharePoint.Project.AssemblyFileName$|Nome dell'assembly di output del progetto contenitore.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Nome dell'assembly di output del progetto contenitore senza estensione.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Token di chiave pubblica dell'assembly di output del progetto contenitore, convertito in stringa. 16 caratteri in formato esadecimale "x2".|  
|$SharePoint.Package.Name$|Nome del pacchetto contenitore.|  
|$SharePoint.Package.FileName$|Nome del file di definizione del pacchetto contenitore.|  
|$SharePoint.Package.FileNameWithoutExtension$|Nome del file di definizione del pacchetto contenitore, senza estensione.|  
|$SharePoint.Package.Id$|ID di SharePoint per il pacchetto contenitore.  Se una funzionalità viene utilizzata in più pacchetti, questo valore verrà modificato.|  
|$SharePoint.Feature.FileName$|Nome del file di definizione della funzionalità contenitore, ad esempio Feature1.feature.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Nome del file di definizione della funzionalità senza estensione.|  
|$SharePoint.Feature.DeploymentPath$|Nome della cartella in cui è contenuta la funzionalità del pacchetto.  Questo token corrisponde alla proprietà "Percorso di distribuzione" nella finestra di progettazione delle funzionalità.  Un valore di esempio è "Project1\_Feature1".|  
|$SharePoint.Feature.Id$|ID di SharePoint della funzionalità contenitore.  Questo token, come tutti i token a livello di funzionalità, può essere utilizzato solo da file inclusi in un pacchetto tramite una funzionalità, non aggiunto direttamente a un pacchetto all'esterno di una funzionalità.|  
|$SharePoint.ProjectItem.Name$|Nome dell'elemento di progetto \(non il nome del file\) ottenuto da **ISharePointProjectItem.Name**.|  
|$SharePoint.Type.\<GUID\>.AssemblyQualifiedName$|Il nome completo di assembly del tipo che corrisponde a [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] del token.  Il formato del [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] è minuscolo e corrisponde al formato Guid.ToString\("D"\), ovvero xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx.|  
|$SharePoint.Type.\<GUID\>.FullName$|Nome completo del tipo che corrisponde al GUID del token.  Il formato del GUID è minuscolo e corrisponde al formato Guid.ToString\("D"\), ovvero xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx.|  
  
## Aggiunta di estensioni all'elenco di estensioni di file sostitutive dei token  
 Sebbene i token possano essere utilizzati in teoria da qualsiasi file che appartiene a un elemento del progetto SharePoint incluso nel pacchetto, per impostazione predefinita [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente di cercare i token solo nei file di pacchetto, nei file manifesto e nei file con le estensioni seguenti:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Webpart  
  
-   DWP  
  
 Queste estensioni vengono definite dall'elemento `<TokenReplacementFileExtensions>` nel file Microsoft.VisualStudio.SharePoint.targets disponibile nella cartella …\\\<program files\>\\MSBuild\\Microsoft\\VisualStudio\\v11.0\\SharePointTools.  
  
 Tuttavia, è possibile aggiungere estensioni di file aggiuntive all'elenco.  A tal fine, aggiungere un elemento `<TokenReplacementFileExtensions>` a qualsiasi elemento PropertyGroup del file di progetto SharePoint definito prima dell' \<import\> del file targets di SharePoint.  
  
> [!NOTE]  
>  Poiché la sostituzione dei token avviene dopo la compilazione di un progetto, non è necessario aggiungere estensioni di file per i tipi di file compilati, ad esempio cs, vb o resx.  I token vengono sostituiti solo nei file non compilati.  
  
 Ad esempio, per aggiungere le estensioni di file "myextension" e "yourextension" all'elenco di estensioni di file sostitutive dei token è necessario aggiungere quanto riportato di seguito a un file con estensione csproj:  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 In alternativa, è possibile aggiungere direttamente l'estensione al file con estensione targets.  Tale operazione, però, modifica l'elenco di estensioni per tutti i progetti SharePoint assemblati nel sistema locale, non solo per il proprio.  Pertanto risulta conveniente se si è l'unico sviluppatore del sistema o se la maggior parte dei progetti richiede questa modifica.  Tuttavia, essendo specifico del sistema questo approccio non è molto portabile, pertanto si consiglia di aggiungere le estensioni al file di progetto.  
  
## Vedere anche  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  