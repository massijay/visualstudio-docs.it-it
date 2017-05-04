---
title: "Unione di codice XML in manifesti di funzionalit&#224; e pacchetto | Microsoft Docs"
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
  - "sviluppo per SharePoint in Visual Studio, creazione di pacchetti"
ms.assetid: fc1cbd2a-0166-4f2f-a81b-4dac2fa7b0f3
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Unione di codice XML in manifesti di funzionalit&#224; e pacchetto
  Funzionalità e pacchetti sono definiti da file manifesto [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  I file manifesto nel pacchetto sono una combinazione di dati generati da finestre di progettazione e [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizzato immesso nel modello di manifesto dagli utenti.  Durante la creazione del pacchetto, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unisce le istruzioni [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] con il codice [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] specificato nella finestra di progettazione per formare il file manifesto [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] nel pacchetto.  Elementi simili, con le eccezioni riportate successivamente nella sezione Eccezioni dell'unione, vengono uniti per evitare errori di convalida [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] in seguito alla distribuzione dei file in SharePoint e per ridurre le dimensioni dei file manifesto e renderli più efficienti.  
  
## Modifica dei manifesti  
 Non è possibile modificare direttamente i file manifesto nel pacchetto finché non si disabilitano Progettazione funzionalità e Progettazione pacchetti.  È tuttavia possibile aggiungere manualmente elementi [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizzati al modello di manifesto tramite Progettazione funzionalità e Progettazione pacchetti o tramite l'editor [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Per ulteriori informazioni, vedere [Procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) e [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## Processo di unione dei manifesti di funzionalità e pacchetto  
 Quando si combinano elementi personalizzati con elementi specificati nella finestra di progettazione, in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene eseguito il processo descritto di seguito.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] controlla se ogni elemento dispone di un valore di chiave univoco.  Se un elemento non ha valore di chiave univoca, viene associato al file manifesto nel pacchetto.  Analogamente, gli elementi che dispongono di più chiavi non possono essere uniti.  Tali elementi vengono pertanto aggiunti al file manifesto.  
  
 Se un elemento presenta una chiave univoca, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] confronta i valori della chiave personalizzata e della chiave della finestra di progettazione.  Se i valori corrispondono, vengono uniti in un singolo valore.  Se invece sono diversi, il valore della chiave della finestra di progettazione viene rimosso e viene utilizzato il valore della chiave personalizzata.  Vengono unite anche le raccolte.  Se, ad esempio, il codice [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] generato nella finestra di progettazione e il codice [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizzato contengono entrambe una raccolta Assemblies, il manifesto nel pacchetto contiene solo una raccolta Assemblies.  
  
## Eccezioni dell'unione  
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] la maggior parte degli elementi [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] della finestra di progettazione viene unita con elementi [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizzati simili a condizione che presentino un singolo attributo di identificazione univoco.  Alcuni elementi, tuttavia, non includono l'identificatore univoco necessario per l'unione [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Tali elementi sono noti come *eccezioni di unione*.  In questi casi, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non unisce gli elementi [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizzati con gli elementi [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] specificati nella finestra di progettazione, ma li aggiunge al file manifesto nel pacchetto.  
  
 Di seguito è riportato un elenco di eccezioni di unione per i file manifesto [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] di funzionalità e pacchetto.  
  
|Finestra di progettazione|Elemento XML|  
|-------------------------------|------------------|  
|Progettazione funzionalità|ActivationDependency|  
|Progettazione funzionalità|UpgradeAction|  
|Progettazione pacchetti|SafeControl|  
|Progettazione pacchetti|CodeAccessSecurity|  
  
## Elementi del manifesto di funzionalità  
 Nella tabella seguente è riportato un elenco di tutti gli elementi del manifesto di funzionalità che possono essere uniti e la relativa chiave univoca utilizzata per la corrispondenza.  
  
|Nome elemento|Chiave univoca|  
|-------------------|--------------------|  
|Feature \(tutti gli attributi\)|*Attribute Name* \(Ogni nome di attributo dell'elemento Feature rappresenta una chiave univoca.\)|  
|ElementFile|Posizione|  
|ElementManifests\/ElementManifest|Posizione|  
|Properties\/Property|Chiave|  
|CustomUpgradeAction|Nome|  
|CustomUpgradeActionParameter|Nome|  
  
> [!NOTE]  
>  Poiché l'unico modo per modificare l'elemento CustomUpgradeAction è tramite l'editor [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizzato, la mancata unione produce un effetto irrilevante.  
  
## Elementi del manifesto di pacchetto  
 Nella tabella seguente è riportato un elenco di tutti gli elementi del manifesto di pacchetto che possono essere uniti e la relativa chiave univoca utilizzata per la corrispondenza.  
  
|Nome elemento|Chiave univoca|  
|-------------------|--------------------|  
|Solution \(tutti gli attributi\)|*Attribute Name* \(Ogni nome di attributo dell'elemento Solution rappresenta una chiave univoca.\)|  
|ApplicationResourceFiles\/ApplicationResourceFile|Posizione|  
|Assemblies\/Assembly|Posizione|  
|ClassResources\/ClassResource|Posizione|  
|DwpFiles\/DwpFile|Posizione|  
|FeatureManifests\/FeatureManifest|Posizione|  
|Resources\/Resource|Posizione|  
|RootFiles\/RootFile|Posizione|  
|SiteDefinitionManifests\/SiteDefinitionManifest|Posizione|  
|WebTempFile|Posizione|  
|TemplateFiles\/TemplateFile|Posizione|  
|SolutionDependency|SolutionID|  
  
## Aggiunta manuale di file distribuiti  
 Alcuni elementi di manifesto, ad esempio ApplicationResourceFile e DwpFiles, specificano un percorso che include un nome file.  L'aggiunta di una voce di nome file al modello di manifesto non comporta, tuttavia, l'aggiunta del file sottostante al pacchetto.  È necessario aggiungere il file al progetto per includerlo nel pacchetto e impostarne la proprietà Tipo distribuzione nel modo appropriato.  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  