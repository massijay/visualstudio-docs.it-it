---
title: "Cache degli schemi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Cache degli schemi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor XML fornisce una cache degli schemi situata nella directory %InstallRoot%\\Xml\\Schemas.La cache degli schemi è globale per tutti gli utenti di un computer e include gli schemi XML standard utilizzati per la convalida dei documenti IntelliSense e XML.  
  
 L'editor XML è anche in grado di individuare gli schemi che si trovano nella soluzione, gli schemi specificati nel campo **Schemi** della finestra **Proprietà** del documento e gli schemi identificati dagli attributi `xsi:schemaLocation` e `xsi:noNamespaceSchemaLocation`.  
  
 Nella tabella seguente vengono descritti gli schemi installati con l'editor XML.  
  
|Nome file|Descrizione|  
|---------------|-----------------|  
|catalog.xsd|Schema per i file del catalogo schemi dell'editor XML.Per informazioni sui cataloghi degli schemi, vedere di seguito.|  
|DotNetConfig.xsd|Schema per i file Web.Config, "http:\/\/schemas.microsoft.com\/.NETConfiguration\/v2.0".|  
|msbuild.xsd|Schema per i Makefile MSBuild, "http:\/\/schemas.microsoft.com\/developer\/msbuild\/2003".|  
|msdata.xsd|Schema per le annotazioni XSD aggiunte dalla classe <xref:System.Data.DataSet>, "urn:schemas\-microsoft\-com:xml\-msdata".|  
|msxsl.xsd|Schema per le estensioni del blocco di script Microsoft XSLT, urn:schemas\-microsoft\-com:xslt.|  
|SnippetFormat.xsd|Schema per i file XML del frammento di codice.Per esempi di schema, vedere %InstallDir%\\VC\#\\Expansions.|  
|Soap1.1.xsd|Schema per il protocollo SOAP \(Simple Object Access Protocol\) 1.1, http:\/\/schemas.xmlsoap.org\/soap\/envelope\/.|  
|Soap1.2.xsd|Schema per il protocollo SOAP \(Simple Object Access Protocol\) 1.2.|  
|SiteMapSchema.xsd|Schema per il file XML della mappa del sito ASP.NET, "http:\/\/schemas.microsoft.com\/AspNet\/SiteMap\-File\-1.0".|  
|wsdl.xsd|Schema per il linguaggio WSDL \(Web Service Description Language\), http:\/\/schemas.xmlsoap.org\/wsdl\/.|  
|xenc.xsd|Schema per la crittografia XML, http:\/\/www.w3.org\/2000\/09\/xmldsig\#.|  
|xhtml.xsd|Schemi per XHTML, http:\/\/www.w3.org\/1999\/XMLSchema.|  
|xlink.xsd|Schema per XLink1.0, http:\/\/www.w3.org\/1999\/xlink.|  
|xml.xsd|Schema che descrive gli attributi xml:space e xml:lang, http:\/\/www.w3.org\/XML\/1998\/namespace.|  
|xmlsig.xsd|Schema per le firme digitali XML, http:\/\/www.w3.org\/2000\/09\/xmldsig\#.|  
|xsdschema.xsd|Schema che descrive XSD, http:\/\/www.w3.org\/2001\/XMLSchema.|  
|xslt.xsd|Schema per le trasformazioni XML, http:\/\/www.w3.org\/1999\/XSL\/Transform.|  
  
## Aggiornamento degli schemi nella cache  
 L'editor carica la directory della cache di schema quando il package editor XML viene caricato e verifica le eventuali modifiche durante l'esecuzione.Se è stato aggiunto uno schema, esso viene caricato automaticamente in un indice di schemi noti in memoria.Se è stato rimosso uno schema, esso viene automaticamente rimosso dall'indice in memoria.Se è stato aggiornato uno schema, esso invalida automaticamente la cache degli schemi in memoria.  
  
> [!NOTE]
>  Poiché la directory della cache di schema è globale, è sufficiente aggiungere qui gli schemi standard utili per tutti i progetti di Visual Studio che è possibile creare sul proprio computer.  
  
 L'editor XML supporta inoltre un numero illimitato di file del catalogo degli schemi nella directory della cache.Per i cataloghi degli schemi è possibile scegliere altre posizioni per gli schemi che si desidera tenere sempre ben presenti nell'editor.Il file catalog.xsd definisce il formato del file di catalogo ed è incluso nella directory della cache degli schemi.Il file catalog.xml è il catalogo predefinito e contiene collegamenti ad altri schemi nella %InstallDir%.Di seguito sono riportati esempi del file catalog.xml:  
  
```  
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">  
  <Schema href="%InstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>  
  <Schema href="%InstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>  
  <Schema href="%InstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>  
</SchemaCatalog>  
```  
  
 L'attributo `href` può essere un qualsiasi percorso di file o URL di tipo http che fa riferimento allo schema.Il percorso del file può essere relativo al documento catalogo.Le seguenti variabili, delimitate da %%, sono riconosciute dall'editor e verranno espanse nel percorso:  
  
-   InstallDir  
  
-   System  
  
-   ProgramFiles  
  
-   Programs  
  
-   CommonProgramFiles  
  
-   ApplicationData  
  
-   CommonApplicationData  
  
-   LCID  
  
 Nel documento catalogo può essere incluso un elemento `Catalog` che fa riferimento ad altri cataloghi.È possibile utilizzare l'elemento `Catalog` per scegliere un catalogo centrale condiviso dal team o dalla società o un catalogo online condiviso con i partner commerciali.L'attributo `href` è il percorso del file o l'URL di tipo http per gli altri cataloghi.Di seguito è riportato un esempio dell'elemento `Catalog`:  
  
```  
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>  
```  
  
 Con il catalogo è inoltre possibile controllare in che modo gli schemi vengono associati ai documenti XML utilizzando l'elemento speciale `Association`.Questo elemento consente di associare gli schemi che non dispongono di uno spazio dei nomi di destinazione con una determinata estensione di file. Questo può risultare utile in quanto l'editor XML non esegue l'associazione automatica degli schemi che non presentano un attributo `targetNamespace`.Nell'esempio seguente l'elemento `Association` associa lo schema dotNetConfig con tutti i file che presentano l'estensione "config":  
  
```  
<Association extension="config" schema="%InstallDir%/xml/schemas/dotNetConfig.xsd"/>  
```  
  
## Schemi localizzati  
 In molti casi il file catalog.xml non contiene voci per gli schemi localizzati.È possibile aggiungere ulteriori voci al file catalog.xml che fanno riferimento alla directory degli schemi localizzati.  
  
 Nell'esempio seguente è stato creato un nuovo elemento `Schema` che utilizza la variabile % LCID% per fare riferimento allo schema localizzato.  
  
```  
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"  
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>  
```  
  
## Modifica del percorso della cache degli schemi  
 È possibile personalizzare il percorso della cache degli schemi utilizzando la pagina delle opzioni **Varie**.Se si dispone di una directory di schemi preferiti, è possibile configurare l'editor in modo da utilizzare solo questi schemi.  
  
> [!NOTE]
>  Tale modifica ha effetto solo sull'utente corrente di Visual Studio.  
  
#### Per modificare il percorso della cache degli schemi  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Espandere **Editor di testo**, quindi espandere **XML** e scegliere **Varie**.  
  
3.  Fare clic sul pulsante **Sfoglia** nel campo **Schemi**.  
  
4.  Selezionare la cartella per la cache degli schemi e scegliere **OK**.  
  
#### Per aggiungere un'altra directory di schemi comuni  
  
1.  Modificare il file catalog.xml nella directory della cache di schema dell'editor XML.  
  
2.  Aggiungere un nuovo elemento `<Catalog href="…"/>` che fa riferimento alla directory degli schemi aggiuntivi.  
  
3.  Salvare le modifiche.  
  
     Il catalogo viene ricaricato automaticamente.  
  
## Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)