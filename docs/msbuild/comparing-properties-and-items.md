---
title: "Confronto di propriet&#224; ed elementi | Microsoft Docs"
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
  - "MSBuild, proprietà di msbuild"
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Confronto di propriet&#224; ed elementi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Proprietà di MSBuild e gli elementi vengono utilizzati per passare informazioni alle attività, valutare le condizioni e archiviare i valori che possono essere utilizzati in tutto il file di progetto.  
  
-   Le proprietà sono coppie nome-valore. Per ulteriori informazioni, vedere [proprietà MSBuild](../msbuild/msbuild-properties.md).  
  
-   Gli elementi sono oggetti che rappresentano in genere i file. Oggetti elemento è possono associare insiemi di metadati. I metadati sono coppie nome-valore. Per ulteriori informazioni, vedere [elementi](../msbuild/msbuild-items.md).  
  
## <a name="scalars-and-vectors"></a>Valori scalari e vettori  
 Poiché le proprietà MSBuild sono coppie nome-valore con un solo valore di stringa, sono spesso descritti come *scalare*. Poiché i tipi di elemento MSBuild sono elenchi di elementi, sono spesso descritti come *vettore*. Tuttavia, in pratica, le proprietà possono rappresentare più valori e tipi di elemento possono avere zero o più elementi.  
  
### <a name="target-dependency-injection"></a>Inserimento di dipendenze di destinazione  
 Per comprendere come le proprietà possono rappresentare più valori, si consideri un modello di utilizzo comune per l'aggiunta di una destinazione per un elenco di destinazioni da compilare. Questo elenco è in genere rappresentato da un valore della proprietà, con i nomi di destinazione, separati da punti e virgola.  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Il `BuildDependsOn` proprietà viene in genere utilizzata come argomento di una destinazione `DependsOnTargets` attributo, in modo efficace convertirlo in un elenco di elementi. Questa proprietà può essere sottoposto a override per aggiungere una destinazione o per modificare l'ordine di esecuzione di destinazione. Di seguito è riportato un esempio:  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Aggiunge la destinazione CustomBuild all'elenco di destinazione, dando `BuildDependsOn` il valore `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 Inserimento di dipendenze di destinazione a partire da MSBuild 4.0, è deprecata. Utilizzare il `AfterTargets` e `BeforeTargets` invece di attributi. Per ulteriori informazioni, vedere [Target Build Order](../msbuild/target-build-order.md).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Conversioni fra stringhe e gli elenchi di elementi  
 MSBuild esegue conversioni da e verso tipi di elemento e i valori stringa in base alle esigenze. Per vedere come un elenco di elementi può diventare un valore stringa, si consideri cosa succede quando un tipo di elemento viene utilizzato come valore di proprietà MSBuild:  
  
```  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 Il tipo di elemento OutputDir presenta un `Include` attributo con il valore "KeyFiles\\; I certificati\\". MSBuild analizza questa stringa in due elementi: i certificati e KeyFiles\\\. Quando il tipo di elemento OutputDir viene utilizzato come valore della proprietà OutputDirList, MSBuild converte o "appiattisce" il tipo di elemento nella stringa separati da punto e virgola "KeyFiles\\; I certificati\\".  
  
## <a name="properties-and-items-in-tasks"></a>Proprietà e gli elementi in attività  
 Proprietà e gli elementi vengono utilizzati come input e output per le attività MSBuild. Per ulteriori informazioni, vedere [attività](../msbuild/msbuild-tasks.md).  
  
 Le proprietà vengono passate alle attività come attributi. All'interno dell'attività, una proprietà di MSBuild è rappresentata da un tipo di proprietà il cui valore può essere convertito in e da una stringa. I tipi di proprietà supportati includono `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`, e qualsiasi tipo che <xref:System.Convert.ChangeType%2A> in grado di gestire.  
  
 Gli elementi vengono passati all'attività, come <xref:Microsoft.Build.Framework.ITaskItem> oggetti. All'interno dell'attività, <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> rappresenta il valore dell'elemento e <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> Recupera i metadati.  
  
 Elenco di elementi di un tipo di elemento può essere passato come matrice di `ITaskItem` oggetti. A partire da .NET Framework 3.5, gli elementi possono essere rimossi da un elenco di elementi in una destinazione utilizzando il `Remove` attributo. Poiché gli elementi possono essere rimossi da un elenco di elementi, è possibile che un tipo di elemento presenti zero elementi. Se un elenco di elementi viene passato a un'attività, il codice dell'attività deve verificare questa possibilità.  
  
## <a name="property-and-item-evaluation-order"></a>Proprietà e l'ordine di valutazione di articolo  
 Durante la fase di valutazione di una compilazione, i file importati vengono incorporati nella build nell'ordine in cui appaiono. Proprietà e gli elementi sono definiti in tre passaggi nell'ordine seguente:  
  
-   Le proprietà sono definite e modificate nell'ordine in cui appaiono.  
  
-   Le definizioni di elemento vengono definite e modificate nell'ordine in cui appaiono.  
  
-   Gli elementi vengono definiti e modificati nell'ordine in cui appaiono.  
  
 Durante la fase di esecuzione di una compilazione, proprietà e gli elementi definiti all'interno di destinazioni vengono valutati insieme in un'unica fase nell'ordine in cui appaiono.  
  
 Tuttavia, non è questo l'intera storia. Quando si definisce una proprietà, una definizione dell'elemento o un elemento, viene valutato il relativo valore. L'analizzatore di espressioni espande la stringa che specifica il valore. Espansione della stringa dipende dalla fase di compilazione. Ecco un ordine di valutazione di proprietà e degli elementi più dettagliato:  
  
-   Durante la fase di valutazione di una compilazione:  
  
    -   Le proprietà sono definite e modificate nell'ordine in cui appaiono. Le funzioni di proprietà vengono eseguite. I valori di proprietà di $ (NomeProprietà) form vengono espansi all'interno di espressioni. Il valore della proprietà è impostato sull'espressione espansa.  
  
    -   Le definizioni di elemento vengono definite e modificate nell'ordine in cui appaiono. Funzioni di proprietà sono già stati espansi all'interno di espressioni. Valori di metadati vengono impostati sulle espressioni espanse.  
  
    -   Tipi di elemento vengono definiti e modificati nell'ordine in cui appaiono. I valori sotto forma di elemento @(ItemType) vengono espanse. Vengono espansi anche le trasformazioni degli elementi. I valori e le funzioni di proprietà sono già stati espansi all'interno di espressioni. I valori di elenco e i metadati di elemento vengono impostati sulle espressioni espanse.  
  
-   Durante la fase di esecuzione di una compilazione:  
  
    -   Proprietà e gli elementi definiti all'interno di destinazioni vengono valutati insieme nell'ordine in cui appaiono. Vengono eseguite le funzioni di proprietà e i valori delle proprietà vengono espansi all'interno di espressioni. Vengono espansi anche i valori degli elementi e le trasformazioni degli elementi. I valori delle proprietà dei tipi di elemento e i valori dei metadati vengono impostati sulle espressioni espanse.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Effetti meno evidenti dell'ordine di valutazione  
 In fase di valutazione di una compilazione, proprietà valutate prima degli elementi. Tuttavia, le proprietà possono avere valori che sembrano dipendono dai valori di elemento. Si consideri il seguente script.  
  
```  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 L'esecuzione dell'attività Message Visualizza questo messaggio:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 Infatti, il valore di `KeyFileVersion` è la stringa "@(KeyFile->'%(Version)')". elemento e le trasformazioni degli elementi non sono stati espansi quando la proprietà è stata definita, in modo che il `KeyFileVersion` proprietà è stato assegnato il valore della stringa non espansa.  
  
 Durante la fase di esecuzione della compilazione, durante l'elaborazione dell'attività Message, MSBuild espande la stringa "@(KeyFile->'%(Version)')" in "1.0.0.3".  
  
 Si noti che lo stesso messaggio verrà visualizzato anche se sono stati annullati i gruppi di proprietà e degli elementi in ordine.  
  
 Come secondo esempio, si consideri cosa può accadere quando i gruppi di proprietà e degli elementi si trovano all'interno di destinazioni:  
  
```  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 L'attività Message Visualizza questo messaggio:  
  
```  
KeyFileVersion:   
```  
  
 In questo modo durante la fase di esecuzione della compilazione, i gruppi di proprietà e degli elementi definiti all'interno di destinazioni vengono valutati dall'alto verso il basso nello stesso momento. Quando `KeyFileVersion` è definito, `KeyFile` è sconosciuto. Pertanto, la trasformazione dell'elemento si espande in una stringa vuota.  
  
 In questo caso, invertendo l'ordine dei gruppi di proprietà e l'elemento consente di ripristinare il messaggio originale:  
  
```  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Il valore di `KeyFileVersion` è impostato su "1.0.0.3" e non a "@(KeyFile->'%(Version)')". messaggio dell'attività consente di visualizzare questo messaggio:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)