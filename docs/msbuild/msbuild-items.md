---
title: "Elementi MSBuild | Microsoft Docs"
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
  - "MSBuild, gli elementi"
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elementi MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Elementi MSBuild sono input nel sistema di compilazione, e rappresentano in genere i file. Gli elementi sono raggruppati in tipi di elemento in base ai nomi di elemento. Tipi di elemento vengono denominati elenchi di elementi che possono essere utilizzati come parametri per le attività. Le attività utilizzano i valori degli elementi per eseguire i passaggi del processo di compilazione.  
  
 Perché gli elementi sono denominati per il tipo di elemento a cui appartengono, i termini "elemento" e "valore dell'elemento" possono essere utilizzate indifferentemente.  
  
 **In questo argomento**  
  
-   [Creazione di elementi in un File di progetto](#BKMK_Creating1)  
  
-   [Creazione di elementi durante l'esecuzione](#BKMK_Creating2)  
  
-   [Fare riferimento a elementi in un File di progetto](#BKMK_ReferencingItems)  
  
-   [Utilizzo dei caratteri jolly per specificare gli elementi](#BKMK_Wildcards)  
  
-   [Utilizzo dell'attributo Exclude](#BKMK_ExcludeAttribute)  
  
-   [Metadati dell'elemento](#BKMK_ItemMetadata)  
  
    -   [Fa riferimento ai metadati di elemento in un File di progetto](#BKMK_ReferencingItemMetadata)  
  
    -   [Metadati noti degli elementi](#BKMK_WellKnownItemMetadata)  
  
    -   [La trasformazione dei tipi di elemento utilizzando i metadati](#BKMK_Transforming)  
  
-   [Definizioni di elementi](#BKMK_ItemDefinitions)  
  
-   [Attributi per gli elementi in un ItemGroup di una destinazione](#BKMK_AttributesWithinTargets)  
  
    -   [Rimuovere l'attributo](#BKMK_RemoveAttribute)  
  
    -   [Attributo KeepMetadata](#BKMK_KeepMetadata)  
  
    -   [Attributo RemoveMetadata](#BKMK_RemoveMetadata)  
  
    -   [Attributo KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="a-namebkmkcreating1a-creating-items-in-a-project-file"></a><a name="BKMK_Creating1"></a> Creazione di elementi in un File di progetto  
 È necessario dichiarare gli elementi nel file di progetto come figlio elementi di un [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elemento. Il nome dell'elemento figlio è il tipo dell'elemento. Il `Include` attributo dell'elemento specifica gli elementi (file) da includere nel tipo di elemento. Ad esempio, il codice XML seguente crea un tipo di elemento denominato `Compile`, che include due file.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 L'elemento "file2" non sostituisce l'elemento "file1"; al contrario, il nome del file viene aggiunto all'elenco di valori per il `Compile` tipo di elemento. È possibile rimuovere un elemento da un tipo di elemento durante la fase di valutazione di una compilazione.  
  
 Il codice XML seguente viene creato lo stesso tipo di elemento dichiarando entrambi i file in uno `Include` attributo. Si noti che i nomi dei file sono separati da un punto e virgola.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="a-namebkmkcreating2a-creating-items-during-execution"></a><a name="BKMK_Creating2"></a> Creazione di elementi durante l'esecuzione  
 Gli elementi che non rientrano [destinazione](../msbuild/target-element-msbuild.md) elementi vengono assegnati valori durante la fase di valutazione di una compilazione. Durante la fase di esecuzione successiva, gli elementi possono essere creati o modificati nei modi seguenti:  
  
-   Qualsiasi attività può emettere un elemento. Per creare un elemento, il [attività](../msbuild/task-element-msbuild.md) elemento deve disporre di un elemento figlio [Output](../msbuild/output-element-msbuild.md) elemento che dispone di un `ItemName` attributo.  
  
-   Il [CreateItem](../msbuild/createitem-task.md) attività può creare un elemento. Questo utilizzo è deprecato.  
  
-   A partire da .NET Framework 3.5, `Target` possono contenere elementi [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementi che possono contenere elementi di elemento.  
  
##  <a name="a-namebkmkreferencingitemsa-referencing-items-in-a-project-file"></a><a name="BKMK_ReferencingItems"></a> Fare riferimento a elementi in un File di progetto  
 Per fare riferimento a tipi di elemento nel file di progetto, utilizzare la sintassi @(`ItemType`). Ad esempio, si fa riferimento il tipo di elemento dell'esempio precedente utilizzando `@(Compile)`. Utilizzando questa sintassi, è possibile passare elementi alle attività specificando il tipo di elemento come un parametro dell'attività. Per ulteriori informazioni, vedere [procedura: selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md).  
  
 Per impostazione predefinita, gli elementi di un tipo di elemento sono separati da punti e virgola (;) quando viene espanso. È possibile utilizzare la sintassi @(*ItemType*, '*separatore*') per specificare un separatore diverso da quello predefinito. Per ulteriori informazioni, vedere [procedura: visualizzare un elenco di elementi separati da virgole](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="a-namebkmkwildcardsa-using-wildcards-to-specify-items"></a><a name="BKMK_Wildcards"></a> Utilizzo dei caratteri jolly per specificare gli elementi  
 È possibile utilizzare il * *, \*, e? caratteri jolly per specificare un gruppo di file come input per una compilazione anziché elencare ogni file separatamente.  
  
-   La distribuzione? carattere jolly corrisponde a un singolo carattere.  
  
-   Il * corrisponde a zero o più caratteri.  
  
-   Il * * la sequenza di caratteri jolly corrisponde a un percorso parziale.  
  
 Ad esempio, è possibile specificare tutti i file con estensione cs nella directory che contiene il file di progetto utilizzando l'elemento seguente nel file di progetto.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 L'elemento seguente seleziona tutti i file vb nell'unità d:  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Per ulteriori informazioni sui caratteri jolly, vedere [procedura: selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="a-namebkmkexcludeattributea-using-the-exclude-attribute"></a><a name="BKMK_ExcludeAttribute"></a> Utilizzo dell'attributo Exclude  
 Possono contenere elementi di `Exclude` attributo, che consente di escludere elementi (file) specifici dal tipo di elemento. Il `Exclude` attributo viene in genere utilizzato con i caratteri jolly. Ad esempio, il codice XML seguente aggiunge tutti i file con estensione cs nella directory al tipo di elemento CSFile, ad eccezione di `DoNotBuild.cs` file.  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 Il `Exclude` attributo interessa solo gli elementi che vengono aggiunti per il `Include` attributo nell'elemento item che li contiene entrambi. Nell'esempio seguente non esclude il file Form1. cs, aggiunto nell'elemento item precedente.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Per ulteriori informazioni, vedere [procedura: escludere file dalla compilazione](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="a-namebkmkitemmetadataa-item-metadata"></a><a name="BKMK_ItemMetadata"></a> Metadati dell'elemento  
 Gli elementi possono contenere metadati oltre alle informazioni nel `Include` e `Exclude` gli attributi. Questo metadati possono essere utilizzati dalle attività che richiedono ulteriori informazioni sugli elementi o di destinazioni e attività batch. Per ulteriori informazioni, vedere [batch](../msbuild/msbuild-batching.md).  
  
 I metadati sono una raccolta di coppie chiave-valore dichiarate nel file di progetto come elementi figlio di un elemento item. Il nome dell'elemento figlio è il nome dei metadati e il valore dell'elemento figlio è il valore dei metadati.  
  
 I metadati sono associato l'elemento che lo contiene. Ad esempio, il codice XML seguente aggiunge `Culture` i metadati con il valore `Fr` per sia gli elementi "one.cs" e "Two.cs" di CSFile il tipo di elemento.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Un elemento può avere zero o più valori di metadati. È possibile modificare i valori dei metadati in qualsiasi momento. Se si impostano i metadati su un valore vuoto, è effettivamente rimuoverlo dalla compilazione.  
  
###  <a name="a-namebkmkreferencingitemmetadataa-referencing-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Fa riferimento ai metadati di elemento in un File di progetto  
 È possibile fare riferimento a metadati dell'elemento nel file di progetto utilizzando la sintassi %(`ItemMetadataName`). Se non esiste ambiguità, è possibile qualificare un riferimento utilizzando il nome del tipo di elemento. Ad esempio, è possibile specificare %(*ItemMetaDataName*). Nell'esempio seguente utilizza i metadati di visualizzazione per batch di attività del messaggio. Per ulteriori informazioni su come utilizzare i metadati per l'invio in batch, vedere [metadati degli elementi in batch di attività](../msbuild/item-metadata-in-task-batching.md).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="a-namebkmkwellknownitemmetadataa-well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Metadati noti degli elementi  
 Quando un elemento viene aggiunto a un tipo di elemento, tale elemento vengono assegnati metadati noti. Ad esempio, tutti gli elementi presentano metadati noti `%(Filename)`, il cui valore è il nome del file dell'elemento. Per ulteriori informazioni, vedere [Well-Known metadati dell'elemento](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="a-namebkmktransforminga-transforming-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> La trasformazione dei tipi di elemento utilizzando i metadati  
 È possibile trasformare gli elenchi di elementi in nuovi elenchi di elementi tramite i metadati. Ad esempio, è possibile trasformare un tipo di elemento `CppFiles` che dispone di elementi che rappresentano file cpp in un elenco di file con estensione obj corrispondente utilizzando l'espressione `@(CppFiles -> '%(Filename).obj')`.  
  
 Il codice seguente crea un `CultureResource` dell'elemento del tipo che contiene copie di tutti `EmbeddedResource` elementi con `Culture` metadati. Il `Culture` metadati valore diventa il valore dei nuovi metadati `CultureResource.TargetDirectory`.  
  
```  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Per ulteriori informazioni, vedere [Trasforma](../msbuild/msbuild-transforms.md).  
  
##  <a name="a-namebkmkitemdefinitionsa-item-definitions"></a><a name="BKMK_ItemDefinitions"></a> Definizioni di elementi  
 A partire da .NET Framework 3.5, è possibile aggiungere metadati predefiniti a qualsiasi tipo di elemento utilizzando il [elemento ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Come metadati noti, i metadati predefiniti sono associato a tutti gli elementi del tipo di elemento specificato. È possibile ignorare in modo esplicito i metadati predefiniti in una definizione di elemento. Ad esempio, il codice XML seguente consente di `Compile` elementi "one.cs" e "three.cs" i metadati `BuildDay` con il valore "Monday". Il codice assegna l'elemento "two.cs" i metadati `BuildDay` con il valore "Tuesday".  
  
```  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 Per ulteriori informazioni, vedere [definizioni di elementi](../msbuild/item-definitions.md).  
  
##  <a name="a-namebkmkattributeswithintargetsa-attributes-for-items-in-an-itemgroup-of-a-target"></a><a name="BKMK_AttributesWithinTargets"></a> Attributi per gli elementi in un ItemGroup di una destinazione  
 A partire da .NET Framework 3.5, `Target` possono contenere elementi [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementi che possono contenere elementi di elemento. Gli attributi in questa sezione sono validi quando vengono specificate per un elemento in un `ItemGroup` che si trova in un `Target`.  
  
###  <a name="a-namebkmkremoveattributea-remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Rimuovere l'attributo  
 Gli elementi un `ItemGroup` di una destinazione può contenere il `Remove` attributo, che rimuove gli elementi specifici (file) dal tipo di elemento. Questo attributo è stato introdotto in .NET Framework 3.5.  
  
 Nell'esempio seguente rimuove il tipo di elemento di compilazione di ogni file con estensione config.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="a-namebkmkkeepmetadataa-keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> Attributo KeepMetadata  
 Se viene generato un elemento all'interno di una destinazione, l'elemento può contenere il `KeepMetadata` attributo. Se questo attributo viene specificato, solo i metadati specificati nell'elenco delimitato da punto e virgola dei nomi verranno trasferiti dall'elemento di origine per l'elemento di destinazione. Un valore vuoto per questo attributo equivale a non specificarla. Il `KeepMetadata` attributo è stato introdotto in .NET Framework 4.5.  
  
 Nell'esempio seguente viene illustrato come utilizzare il `KeepMetadata` attributo.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="a-namebkmkremovemetadataa-removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> Attributo RemoveMetadata  
 Se viene generato un elemento all'interno di una destinazione, l'elemento può contenere il `RemoveMetadata` attributo. Se questo attributo viene specificato, tutti i metadati viene trasferito dall'elemento di origine per l'elemento di destinazione, ad eccezione dei metadati i cui nomi sono contenuti nell'elenco delimitato da punto e virgola dei nomi. Un valore vuoto per questo attributo equivale a non specificarla. Il `RemoveMetadata` attributo è stato introdotto in .NET Framework 4.5.  
  
 Nell'esempio seguente viene illustrato come utilizzare il `RemoveMetadata` attributo.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="a-namebkmkkeepduplicatesa-keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> Attributo KeepDuplicates  
 Se viene generato un elemento all'interno di una destinazione, l'elemento può contenere il `KeepDuplicates` attributo. `KeepDuplicates` è un `Boolean` attributo che specifica se un elemento deve essere aggiunto al gruppo di destinazione se l'elemento è un duplicato esatto di un elemento esistente.  
  
 Se l'elemento di origine e destinazione hanno lo stesso valore di inclusione ma metadati diversi, l'elemento viene aggiunto anche se `KeepDuplicates` è impostato su `false`. Un valore vuoto per questo attributo equivale a non specificarla. Il `KeepDuplicates` attributo è stato introdotto in .NET Framework 4.5.  
  
 Nell'esempio seguente viene illustrato come utilizzare il `KeepDuplicates` attributo.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)   
 [Procedura: selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md)   
 [Procedura: escludere file dalla compilazione](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Procedura: visualizzare un elenco di elementi separato da virgole](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Definizioni di elementi](../msbuild/item-definitions.md)   
 [L'invio in batch](../msbuild/msbuild-batching.md)   
 [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)