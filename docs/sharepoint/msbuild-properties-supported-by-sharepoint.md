---
title: "Propriet&#224; MSBuild supportate in SharePoint | Microsoft Docs"
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
  - "sviluppo per SharePoint in Visual Studio, proprietà di MSBuild"
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Propriet&#224; MSBuild supportate in SharePoint
  Tutte le proprietà [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] definite nel file Microsoft.VisualStudio.SharePoint.targets, nel file di progetto o nel file di progetto dell'utente possono essere utilizzate nei progetti SharePoint di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Oltre alle proprietà [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] comuni incluse nel progetto, in SharePoint vengono definite proprietà aggiuntive specifiche dei progetti SharePoint.  
  
 Per un elenco delle proprietà comuni di [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)], vedere [Proprietà di progetto MSBuild comuni](http://go.microsoft.com/fwlink/?LinkID=168687).  Per un elenco completo delle proprietà supportate dal linguaggio di programmazione, esaminare il file con estensione targets, il file di progetto \(con estensione .csproj o .vbproj\) o il file di progetto dell'utente \(csproj.user o .user .vbproj\).  
  
## Proprietà MSBuild specifiche di SharePoint  
 Nella tabella seguente sono elencate le proprietà [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] che si applicano in modo specifico ai progetti SharePoint di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Esistono anche altre proprietà, ma sono destinate solo a un uso interno.  
  
|Nome proprietà|Descrizione|  
|--------------------|-----------------|  
|SharePointSiteUrl|Stringa che rappresenta l'oggetto [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] del sito di SharePoint.|  
|SandboxedSolution|Valore booleano che indica se la soluzione è una soluzione creata mediante sandbox.|  
|ActiveDeploymentConfiguration|Configurazione di distribuzione attiva.|  
|IncludeAssemblyInPackage|Valore booleano che indica se l'assembly è incluso nel file di pacchetto.|  
|PreDeploymentCommand|Valore stringa che rappresenta il comando da eseguire durante il passaggio relativo al comando pre\-distribuzione.|  
|PostDeploymentCommand|Valore stringa che rappresenta il comando da eseguire durante il passaggio relativo al comando post\-distribuzione.|  
|CustomBeforeSharePointTargets|Stringa che rappresenta il percorso di un file targets di [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  Se il file targets esiste ed è definito, viene importato prima dei dati delle destinazioni di SharePoint.  Questa proprietà consente di personalizzare il processo del pacchetto predefinendo proprietà correlate al pacchetto senza modificare il file targets incluso in SharePoint, che rimane comunque applicabile a tutti i progetti SharePoint.|  
|CustomAfterSharePointTargets|Stringa che rappresenta il percorso di un file targets di [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  Se il file targets esiste ed è definito, viene importato dopo tutti i dati delle destinazioni di SharePoint.  Questa proprietà consente di personalizzare il processo del pacchetto eseguendo l'override delle proprietà e delle destinazioni correlate al pacchetto senza modificare il file targets incluso in SharePoint, che rimane comunque applicabile a tutti i progetti SharePoint.|  
|LayoutPath|Stringa che rappresenta la directory radice in cui vengono temporaneamente inseriti i singoli file da includere nel pacchetto prima di aggiungerli al file con estensione wsp.  Può essere utile conoscere questo percorso quando si esegue l'override delle destinazioni BeforeLayout e AfterLayout per aggiungere, rimuovere o modificare file da inserire nel pacchetto, in quanto è possibile utilizzarlo per modificare il contenuto del file con estensione wsp.|  
|BasePackagePath|Stringa che rappresenta la cartella in cui viene inserito il pacchetto.  Per questo valore viene utilizzata la directory di output del progetto, ad esempio Bin\\Debug.|  
|PackageExtension|Stringa che rappresenta l'estensione del nome file da aggiungere al pacchetto.  Il valore predefinito è wsp.|  
|AssemblyDeploymentTarget|Stringa che rappresenta il percorso in cui viene distribuito l'assembly del progetto sul server SharePoint.  Il valore è GlobalAssemblyCache \(impostazione predefinita\) o WebApplication.  È inoltre possibile impostare questa proprietà nella finestra Proprietà.|  
|PackageWithValidation|Valore booleano che specifica se la convalida viene eseguita prima della creazione del pacchetto.  Questa proprietà consente di ignorare gli errori di convalida durante la compilazione dei pacchetti.|  
|ValidatePackageDependsOn|Stringa che definisce ulteriori destinazioni da eseguire prima della destinazione ValidatePackage.|  
|TokenReplacementFileExensions|Stringa che definisce i file i cui token vengono sostituiti durante la creazione del pacchetto.|  
  
## Utilizzo delle proprietà MSBuild nella pagina Proprietà  
 Per maggiore flessibilità, anziché utilizzare stringhe hardcoded nelle caselle **Riga di comando pre\-distribuzione** e **Riga di comando post\-distribuzione** della pagina Proprietà di SharePoint, è possibile utilizzare le proprietà di SharePoint come argomenti.  Anziché specificare una determinata stringa [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] per il sito di SharePoint, è ad esempio possibile utilizzare `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Per specificare una proprietà, è possibile utilizzare la sintassi [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] delle variabili `$(`*propertyName*`)` o delle variabili di ambiente `%`*propertyName*`%`.  
  
## Vedere anche  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  
  
  