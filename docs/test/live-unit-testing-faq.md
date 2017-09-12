---
title: Domande frequenti su Live Unit Testing | Microsoft Docs
ms.date: 2017-08-15
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
ms.assetid: 61baf3bb-646f-4c5a-b7c0-a6bdff68f21c
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c6a2c3b313aca87a77f7ad5b12a3d99c82c042b2
ms.contentlocale: it-it
ms.lasthandoff: 09/06/2017

---
# <a name="live-unit-testing-frequently-asked-questions"></a>Domande frequenti su Live Unit Testing

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-153"></a>Novità di Live Unit Testing per Visual Studio 2017 versione 15.3 

**Risposta:**

- Il supporto per .NET Core/.NET Standard e i miglioramenti delle prestazioni sono le due novità principali. Si noterà che le prestazioni sono notevolmente più veloci dopo la prima compilazione completa e la prima esecuzione di test in Live Unit Testing. Si percepirà anche un significativo miglioramento delle prestazioni durante gli avvii successivi di Live Unit Testing nella stessa soluzione. I dati generati da Live Unit Testing dovranno ora essere salvati in modo permanente e riusati il più possibile con i controlli aggiornati. Oltre a queste aggiunte principali, Live Unit Testing include anche i miglioramenti seguenti: 

  - Una nuova icona becher viene ora usata per distinguere un metodo di test dai metodi regolari. Un'icona becher vuota indica che il test specifico non è incluso in Live Unit Testing. 

  - Quando si fa clic su un metodo di test dalla finestra a comparsa dell'interfaccia utente di un'icona di code coverage di un Live Unit Testing, è ora possibile eseguire il debug di test direttamente da questo contesto all'interno della finestra dell'interfaccia utente e senza dover uscire dall'editor del codice. Questa funzionalità è particolarmente utile quando si esamina un test non riuscito.  

  - In Strumenti/Opzioni/Live Unit Testing/Generale sono state aggiunte altre opzioni configurabili. È possibile limitare la memoria usata per Live Unit Testing. È possibile anche specificare il percorso del file relativo ai dati permanenti di Live Unit Testing per la soluzione aperta. 

  - Nella barra dei menu di Test/Live Unit Testing sono state aggiunte altre voci di menu. **Reset Clean** (Reimposta e pulisci), che elimina i dati permanenti e li rigenera. **Opzione**, che consente di passare a Strumenti/Opzioni/Live Unit Testing/Generale.
  
  - È ora possibile usare gli attributi seguenti per specificare nel codice sorgente che si vuole escludere da Live Unit Testing determinati metodi di test:
    - Per xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
    - Per NUnit: `[Category("SkipWhenLiveUnitTesting")]`
    - Per MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="does-live-unit-testing-work-with-net-core"></a>Live Unit Testing è compatibile con .NET Core?  

**Risposta:**

Sì. Live Unit Testing funziona con .NET Core e .NET Framework. Il supporto per .NET Core è stato aggiunto di recente in Visual Studio 2017 versione 15.3. Aggiornare questa versione di Visual Studio se si vuole il supporto per Live Unit Testing per .NET Core. 

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>Perché Live Unit Testing non funziona quando viene attivato? 

**Risposta:** 

La **finestra di output** (quando è selezionato il menu a discesa Live Unit Testing) indica in genere il motivo per cui Live Unit Testing non funziona. È possibile che Live Unit Testing non funzioni per uno dei motivi seguenti: 

- Se i pacchetti NuGet usati come riferimento nei progetti della soluzione non sono stati ripristinati, Live Unit Testing non funzionerà. Per risolvere il problema, eseguire una compilazione esplicita della soluzione o il ripristino dei pacchetti NuGet della soluzione prima di attivare Live Unit Test. 

- Se nei progetti si usano test basati su MSTest, verificare di rimuovere il riferimento a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` e aggiungere i riferimenti alle versioni più recenti dei pacchetti NuGet di MSTest, ovvero `MSTest.TestAdapter` (è richiesta almeno la versione 1.1.11) e `MSTest.TestFramework` (è richiesta almeno la versione 1.1.11). Per altre informazioni, vedere la sezione sui framework di test supportati nell'argomento [Usare Live Unit Testing in Visual Studio 2017 Enterprise Edition](live-unit-testing.md#supported-test-frameworks).
 
- Almeno un progetto della soluzione dovrebbe includere un riferimento a NuGet o un riferimento diretto al framework di test xUnit, NUnit o MSTest. Questo progetto deve anche fare riferimento a un pacchetto NuGet corrispondente degli adattatori di test di Visual Studio. È anche possibile usare un file `.runsettings` per fare riferimento all'adattatore di test di Visual Studio. Il file `.runsettings` deve avere contenere una voce simile a quella seguente: 

   ```xml
    <RunSettings> 
       <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
       </RunConfiguration> 
    </RunSettings> 
   ``` 

## <a name="why-does-live-unit-testing-show-incorrect-coverage-after-you-upgrade-the-test-adapter-referenced-in-your-visual-studio-projects-to-the-supported-version"></a>Perché Live Unit Testing mostra una coverage errata dopo aver aggiornato l'adattatore di test cui viene fatto riferimento nei progetti Visual Studio alla versione supportata?

**Risposta:**

- Se più progetti nella soluzione fanno riferimento al pacchetto dell'adattatore di test NuGet, è necessario aggiornare ogni progetto alla versione supportata.

- Assicurarsi che anche il file MSBuild con estensione props importato dal pacchetto dell'adattatore di test sia stato aggiornato correttamente. Controllare la versione o il percorso del pacchetto NuGet importato indicato in genere nella parte superiore del file di progetto, come illustrato di seguito:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="can-i-customize-my-live-unit-testing-builds"></a>È possibile personalizzare le compilazioni di Live Unit Testing? 

**Risposta:**

Se per eseguire la compilazione per la strumentazione (Live Unit Testing) la soluzione richiede istruzioni personalizzate che non sono necessarie per la compilazione normale non instrumentata, è possibile aggiungere ai file di progetto o con estensione target il codice che verifica la presenza della proprietà `BuildingForLiveUnitTesting` ed esegue le istruzioni personalizzate di pre/post-compilazione. È anche possibile scegliere di rimuovere alcune istruzioni di compilazione, ad esempio per la pubblicazione o la creazione di pacchetti, o di aggiungere istruzioni di compilazione, ad esempio per la copia dei prerequisiti, a una compilazione di Live Unit Testing in base a questa proprietà del progetto. Questa operazione non modificherà in alcun modo la compilazione normale e influirà solo sulle compilazioni di Live Unit Testing. 

Ad esempio, potrebbe essere presente una destinazione che produce pacchetti NuGet durante una compilazione normale. È probabile che non si vogliano generare pacchetti NuGet dopo ogni modifica apportata. È quindi possibile disabilitare tale destinazione nella compilazione di Live Unit Testing eseguendo quanto segue:   

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'"> 
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/> 
</Target> 
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Messaggi di errore con &lt;OutputPath&gt; o &lt;OutDir&gt;

**Perché quando Live Unit Testing prova a compilare la soluzione viene visualizzato l'errore "...sembra impostato in modo incondizionato su `<OutputPath>` o `<OutDir>`. In Live Unit Testing non verranno eseguiti test dall'assembly di output"?**

**Risposta:**

Questo problema può verificarsi se il processo di compilazione per la soluzione esegue in modo incondizionato l'override di `<OutputPath>` o di `<OutDir>`, in modo tale che non sia una sottodirectory di `<BaseOutputPath>`. In tali casi Live Unit Testing non funziona perché esegue l'override anche di questi elementi per assicurarsi che gli artefatti di compilazione vengano rilasciati in una cartella in `<BaseOutputPath>`. Se è necessario eseguire l'override del percorso devono essere rilasciati gli artefatti di compilazione in una compilazione normale, eseguire l'override di `<OutputPath>` in modo condizionale in base a `<BaseOutputPath>`. 

Se ad esempio la compilazione esegue l'override di `<OutputPath>` come illustrato di seguito: 

```xml 
<Project> 
  <PropertyGroup> 
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath> 
  </PropertyGroup> 
</Project> 
```

è possibile sostituirla con quanto segue: 

```xml 
<Project> 
  <PropertyGroup> 
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath> 
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath> 
  </PropertyGroup> 
</Project> 
```
 
In tal modo verrà garantita la presenza di `<OutputPath>` nella cartella `<BaseOutputPath>`. 
 
Non eseguire l'override di `<OutDir>` direttamente nel processo di compilazione, ma eseguire l'override `<OutputPath>` per rilasciare gli artefatti di compilazione in un percorso specifico.
  
## <a name="setting-the-location-of-live-unit-testing-build-artifacts"></a>Impostazione del percorso degli artefatti di compilazione di Live Unit Testing

**Si vogliono impostare gli artefatti di una compilazione di Live Unit Testing in modo che vengano rilasciati in un percorso specifico invece di quello predefinito nella cartella `.vs`. Come si può modificare questa impostazione?**
 
**Risposta:**

Impostare la variabile di ambiente a livello di utente `LiveUnitTesting_BuildRoot` sul percorso in cui si vuole che vengano rilasciati gli artefatti di compilazione di Live Unit Testing.  

## <a name="how-is-running-tests-from-test-explorer-window-different-from-running-tests-in-live-unit-testing"></a>Quali sono le differenze tra l'esecuzione di test dalla finestra Esplora test e l'esecuzione di test in Live Unit Testing? 

**Risposta:**

Esistono numerose differenze: 

- Durante l'esecuzione o il debug di test dalla finestra Esplora test vengono eseguiti file binari normali, mentre con Live Unit Testing vengono eseguiti file instrumentati. Se si vuole eseguire il debug di file binari instrumentati, provare ad aggiungere una chiamata al metodo [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) nel metodo di test per fare in modo che il debugger venga avviato ogni volta che si esegue tale metodo (incluso quando viene eseguito da Live Unit Testing). A questo punto è possibile collegare ed eseguire il debug del file binario instrumentato. Ci auguriamo però che le tecniche di strumentazione siano note per la maggior parte degli scenari utente e che non sia necessario eseguire il debug di file binari instrumentati. 

- Live Unit Testing non crea un nuovo dominio applicazione per eseguire i test, ma i test vengono eseguiti dalla finestra Esplora test per creare un nuovo dominio applicazione. 

- Live Unit Testing esegue i test di ogni assembly di test in modo sequenziale, mentre più test eseguiti dalla finestra Esplora test con il pulsante **Esegui test in parallelo** selezionato verranno eseguiti in parallelo. 

- Per l'individuazione e l'esecuzione di test in Live Unit Testing viene usata la versione 2 di `TestPlatform`, mentre nella finestra Esplora test viene usata la versione 1. Nella maggior parte dei casi non si dovrebbero però notare differenze.  

- Per impostazione predefinita, Esplora test esegue attualmente i test in un apartment a thread singolo, mentre Live Unit Testing esegue i test in un apartment a thread multipli. Per eseguire test MSTest nell'apartment a thread singolo in Live Unit Testing, decorare il metodo di test o la classe contenitore con l'attributo `<STATestMethod>` o `<STATestClass>` reperibili nel pacchetto NuGet `MSTest.STAExtensions 1.0.3-beta`. Per NUnit e xUnit decorare il metodo di test rispettivamente con l'attributo `<RequiresThread(ApartmentState.STA)>` e con l'attributo `<STAFact>`.
 
## <a name="how-do-i-exclude-tests-from-participating-in-live-unit-testing"></a>Come si escludono i test da Live Unit Testing?

**Risposta:**

Per l'impostazione specifica dell'utente, vedere la sezione "Inclusione ed esclusione di progetti e metodi di test" dell'argomento [Usare Live Unit Testing in Visual Studio 2017 Enterprise Edition](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods). Questa opzione è particolarmente utile quando si vuole eseguire un set specifico di test per una determinata sessione di modifica oppure per rendere persistenti le proprie preferenze personali.
  
Per le impostazioni specifiche della soluzione è possibile applicare l'attributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> a livello di codice per evitare che metodi, proprietà, classi o strutture vengano instrumentati da Live Unit Testing. È anche possibile impostare la proprietà `<ExcludeFromCodeCoverage>` su `true` nel file di progetto per evitare che l'intero progetto venga instrumentato. Live Unit Testing eseguirà ancora i test non instrumentati, ma le informazioni di code coverage non verranno visualizzate.

È anche possibile verificare se `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` è caricato nel dominio applicazione corrente e disabilitare i test sulla base di tale elemento. Ad esempio, è possibile eseguire quanto segue con xUnit:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name == 
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

## <a name="why-are-win32-pe-headers-different-in-instrumented-assemblies-built-by-live-unit-testing"></a>Perché le intestazioni PE di Win32 sono diverse negli assembly instrumentati compilati da Live Unit Testing? 

**Risposta:**

Questo problema è risolto e non esiste in Visual Studio 2017 versione 15.3. Eseguire l'aggiornamento di questa versione di Visual Studio.

Per le versioni precedenti di Visual Studio 2017, esiste un bug noto che potrebbe impedire alle compilazioni di Live Unit Testing di incorporare i dati seguenti dell'intestazione PE di Win32: 

- Versione del file (specificata da @System.Reflection.AssemblyFileVersionAttribute nel codice). 

- Icona Win32 (specificata da `/win32icon:` nella riga di comando). 

- Manifesto Win32 (specificato da `/win32manifest:` nella riga di comando). 

I test che si basano su questi valori potrebbero non riuscire quando vengono eseguiti da Live Unit Testing.

## <a name="why-does-live-unit-testing-keep-building-my-solution-all-the-time-even-if-i-am-not-making-any-edits"></a>Perché Live Unit Testing continua a compilare la soluzione ogni volta anche se non si apportano modifiche? 

**Risposta:**

Questa situazione può verificarsi se il processo di compilazione della soluzione genera codice sorgente che fa parte della soluzione stessa e non sono stati specificati input e output appropriati per i file di destinazione della compilazione. È necessario specificare un elenco di input e di output per le destinazioni in modo che MSBuild possa eseguire i controlli di aggiornamento appropriati e stabilire se è necessaria una nuova compilazione. 

Live Unit Testing avvia una compilazione ogni volta che rileva una modifica nei file di origine. Dal momento che la compilazione della soluzione genera file di origine, Live Unit Testing entrerà in un ciclo di compilazione infinito. Se però la verifica degli input e degli output della destinazione viene eseguita quando Live Unit Testing avvia la seconda compilazione (dopo il rilevamento dei file di origine appena generati dalla compilazione precedente), il ciclo verrà interrotto perché la verifica degli input e degli output indica che non ci sono stati altri aggiornamenti.   

## <a name="how-does-live-unit-testing-work-with-the-lightweight-solution-load-feature"></a>Come funziona Live Unit Testing con la funzionalità di caricamento leggero delle soluzioni? 

**Risposta:**

Live Unit Testing attualmente non funziona bene con la funzionalità di caricamento della soluzione Lightweight. Funziona solo dopo il caricamento di almeno uno dei progetti di test. Fino ad allora non funzionerà perché attualmente Live Unit Testing è dipendente da almeno uno dei progetti di test che fanno riferimento a un adattatore di test (MSTest, xUnit o NUnit).
 
## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>Perché Live Unit Testing non acquisisce le informazioni di code coverage da un nuovo processo creato da un test?
 
**Risposta:**

Si tratta di un problema noto e dovrebbe essere risolto in un prossimo aggiornamento di Visual Studio 2017. 

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>Perché non succede nulla dopo che sono stati inclusi o esclusi test dal set di test attivi? 

**Risposta:**

Questo problema è stato risolto e non sussiste in Visual Studio 2017 versione 15.3. Eseguire l'aggiornamento a questa versione di Visual Studio. 

Per le versioni precedenti di Visual Studio 2017, si tratta di un problema noto. Per ovviare al problema, è necessario apportare una modifica in un file qualsiasi dopo aver incluso o escluso i test.  

## <a name="live-unit-testing-and-editor-icons"></a>Live Unit Testing e icone dell'editor 

**Perché nell'editor non sono presenti icone anche se Live Unit Testing sembra eseguire i test in base ai messaggi nella finestra di output?** 

**Risposta:**

Questa situazione si verifica se gli assembly su cui Live Unit Testing è in esecuzione non sono instrumentati per un qualsiasi motivo. Live Unit Testing non è ad esempio compatibile con progetti che impostano `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. In questo caso, è necessario aggiornare il processo di compilazione in modo da rimuovere questa impostazione o modificarla in `true` per consentire il corretto funzionamento di Live Unit Testing.  

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>In che modo è possibile raccogliere log più dettagliati per le segnalazioni di bug? 

**Risposta:**

Per raccogliere log più dettagliati, è possibile eseguire diverse operazioni: 

- Passare a **Strumenti**, **Opzioni**, **Live Unit Testing** e impostare l'opzione del livello di registrazione su **Dettagliato**, in modo che vengano visualizzati log più dettagliati nella finestra di output. 

- Impostare la variabile di ambiente utente `LiveUnitTesting_BuildLog` sul nome del file da usare per acquisire il log di MSBuild. Sarà quindi possibile recuperare da tale file i messaggi dettagliati del log di MSBuild restituiti da compilazioni di Live Unit Testing.

- Impostare la variabile di ambiente utente `LiveUnitTesting_TestPlatformLog` su `1` per acquisire il log della piattaforma di test. Sarà quindi possibile recuperare i messaggi dettagliati del log della piattaforma di test generati dalle esecuzioni di Live Unit Testing da `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Creare una variabile di ambiente a livello di utente denominata `VS_UTE_DIAGNOSTICS` e impostarla su 1 (o su un valore qualsiasi) e quindi riavviare Visual Studio. A questo punto verranno visualizzati molti più messaggi di registrazione nella scheda **Output - Test** di Visual Studio. 
  
## <a name="see-also"></a>Vedere anche

[Live Unit Testing](live-unit-testing.md)
 

