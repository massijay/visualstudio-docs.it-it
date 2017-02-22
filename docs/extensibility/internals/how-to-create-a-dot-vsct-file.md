---
title: "Procedura: creare una. File Vsct | Microsoft Docs"
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
  - "File VSCT, creazione"
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: creare una. File Vsct
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esistono diversi modi per creare un file di configurazione \(vsct\) tabella Visual Studio comando basato su XML.  
  
-   È possibile creare un nuovo pacchetto Visual Studio nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modello di pacchetto.  
  
-   È possibile utilizzare il compilatore comando basato su XML di configurazione di tabella, Vsct.exe, per generare un file da un file .ctc esistente.  
  
-   È possibile utilizzare Vsct.exe per generare un file vsct da un file .cto esistente.  
  
-   È possibile creare manualmente un nuovo file. vsct.  
  
 In questo argomento viene illustrato come creare manualmente un nuovo file. vsct.  
  
### Per creare manualmente un nuovo file. vsct  
  
1.  Avviare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  Nel **File** dal menu **New**, quindi fare clic su **File**.  
  
3.  Nel **modelli** riquadro, fare clic su **File XML** e quindi fare clic su **aprire**.  
  
4.  Nel **visualizzazione** menu, fare clic su **finestra proprietà** per visualizzare le proprietà del file XML.  
  
5.  Nel **proprietà** fare clic sul pulsante Sfoglia \(...\) pulsante sulla proprietà schemi.  
  
6.  Nell'elenco di schemi XSD, selezionare lo schema vsct.xsd. Se non è nell'elenco, fare clic su **Aggiungi** e quindi individuare il file in un'unità locale. Fare clic su **OK** quando si è finito.  
  
7.  Nel file XML, digitare `<CommandTable` e quindi premere TAB. Chiudere il tag digitando `>`.  
  
     Viene creato un file di base. vsct.  
  
8.  Inserire gli elementi del file XML che si desidera aggiungere, in base al [VSCT Schema](../../extensibility/vsct-xml-schema-reference.md). Per altre informazioni, vedere [Creazione e modifica. File Vsct](../../extensibility/internals/authoring-dot-vsct-files.md).  
  
## Compilazione del codice  
 Semplicemente aggiunge un file vsct a un progetto non viene spostato da compilare. È necessario includerlo nel processo di compilazione.  
  
### Per aggiungere un file vsct per la compilazione del progetto  
  
1.  Aprire il file di progetto nell'editor. Se il progetto viene caricato, è necessario scaricare prima.  
  
2.  Aggiungere un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) che contiene un elemento VSCTCompile, come illustrato nell'esempio seguente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     L'elemento ResourceName deve sempre essere impostato su `Menus.ctmenu`.  
  
3.  Se il progetto contiene un file. resx, aggiungere un elemento risorsa incorporata contenente un elemento MergeWithCTO, come illustrato nell'esempio seguente.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Questo codice deve essere all'interno dell'elemento ItemGroup che contiene risorse incorporate.  
  
4.  Aprire il file del pacchetto, in genere denominato *NomeProgetto*Package.cs o *NomeProgetto*Package.vb, nell'editor.  
  
5.  Aggiungere un attributo ProvideMenuResource alla classe del pacchetto, come illustrato nell'esempio seguente.  
  
    ```c#  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Il primo valore del parametro deve corrispondere al valore dell'attributo ResourceName che è definito nel file di progetto.  
  
## Vedere anche  
 [Creazione e modifica. File Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Procedura: Creare un file con estensione vsct da un file CTC esistente](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Procedura: Creare un file con estensione vsct da un file CTO esistente](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md)   
 [Riferimento allo Schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)