---
title: "Procedura: Creare uno unit test basato sui dati | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.test.testresults.unittest.datadriven"
  - "vs.test.testresults.unittest.datadriven.failure"
helpviewer_keywords: 
  - "unit test, esecuzione"
  - "unit test basati sui dati"
  - "unit test basati su dati"
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 33
caps.handback.revision: 33
ms.author: "mlearned"
manager: "douge"
---
# Procedura: Creare uno unit test basato sui dati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzando il framework dei test d'unità Microsoft per il codice gestito, è possibile impostare un metodo nel test per recuperare i valori utilizzati da esso provenienti da una sorgente dati.  Il metodo viene eseguito in successione per ogni riga della sorgente dati, che semplifica il verificare di vari input tramite l'uso di un singolo metodo.  
  
 Di seguito sono elencate le diverse sezioni di questo argomento:  
  
-   [Il metodo sottoposto a test](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [Creazione di un'origine dati](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [Aggiunta di un TestContext alla classe di test](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [Scrittura di un metodo di test](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [Specificare il DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [Utilizzare TestContext.DataRow per accedere ai dati](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [Esecuzione del test e visualizzazione dei risultati](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 Creare un test d'unità basato sui dati include i passaggi seguenti:  
  
1.  Creare una sorgente dati che contiene i valori utilizzati nel metodo di test.  L'origine dei dati può essere di qualsiasi tipo che viene registrato nel computer che esegue il test.  
  
2.  Aggiungere un campo privato <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> e una proprietà pubblica `TestContext` alla classe di test.  
  
3.  Creare un metodo di unit test con un attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.  
  
4.  Utilizzare la proprietà dell'indicizzatore <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> per recuperare i valori utilizzati in un test.  
  
##  <a name="BKMK_The_method_under_test"></a> Il metodo sottoposto a test  
 Ad esempio, si presupponga di aver creato:  
  
1.  Una soluzione denominata `MyBank` che accetta ed elabora le transazioni per diversi tipi di account.  
  
2.  Un progetto in `MyBank` ha chiamato `BankDb` che gestisce le transazioni per gli account.  
  
3.  La classe ha chiamato `Maths` nel progetto `DbBank` che esegue funzioni matematiche per assicurare che qualsiasi transazione sia vantaggiosa per la banca.  
  
4.  Un progetto di unit test ha chiamato `BankDbTests` per verificare il comportamento del componente `BankDb`.  
  
5.  Una classe di unit test ha chiamato `MathsTests` per verificare il comportamento della classe `Maths`.  
  
 Verificheremo un metodo in `Maths` che aggiunge due interi utilizzando un ciclo:  
  
```  
public int AddIntegers(int first, int second)  
{  
    int sum = first;  
    for( int i = 0; i < second; i++)  
    {  
        sum += 1;  
    }  
    return sum;  
}  
```  
  
##  <a name="BKMK_Creating_a_data_source"></a> Creazione di un'origine dati  
 Per testare il metodo `AddIntegers`, viene creata un'origine dati che specifica un intervallo di valori per i parametri e la somma che si prevede venga restituita.  Nell'esempio, viene creato un Sql Compact database denominato `MathsData` ed una tabella denominata `AddIntegersData` che contenente i nomi di colonna ed i valori  
  
|FirstNumber|SecondNumber|Somma|  
|-----------------|------------------|-----------|  
|0|1|1|  
|1|1|2|  
|2|\-3|\-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> Aggiunta di un TestContext alla classe di test  
 Il framework di unit test crea un oggetto `TestContext` per archiviare le informazioni di un'origine dati per un test basato su dati.  Il framework quindi imposta l'oggetto come valore della proprietà `TestContext` che crea.  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 Nel metodo di test, è possibile accedere ai dati tramite la proprietà dell'indicizzatore `DataRow` del `TestContext`.  
  
##  <a name="BKMK_Writing_the_test_method"></a> Scrittura di un metodo di test  
 Il metodo di test per `AddIntegers` è abbastanza semplice.  Per ogni riga della sorgente dati, verrà chiamato `AddIntegers` con i valori della colonna **FirstNumber** e **SecondNumber** come parametri e verificato il valore restituito confrontandolo con il valore della colonna **Sum** :  
  
```  
  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]  
[TestMethod()]  
public void AddIntegers_FromDataSourceTest()  
{  
    var target = new Maths();  
  
    // Access the data  
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);   
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);  
    int actual = target.IntegerMethod(x, y);  
    Assert.AreEqual(expected, actual,  
        "x:<{0}> y:<{1}>",  
        new object[] {x, y});  
  
}  
  
```  
  
 Si noti che il metodo `Assert` include un messaggio che visualizza i valori `x` ed `y` di un'iterazione non riuscita.  Per impostazione predefinita, i valori asseriti, `expected` e `actual`, sono già inclusi nei dettagli di un test non superato.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Specificare il DataSourceAttribute  
 L'attributo `DataSource` specifica la stringa di connessione per l'origine dati ed il nome della tabella utilizzato nel metodo di test.  Le informazioni esatte nella stringa di connessione possono variare a seconda del tipo di origine dati utilizzato.  In questo esempio, si utilizza un database di SqlServerCe.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 L'attributo DataSource dispone di tre costruttori.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Un costruttore con un parametro utilizza le informazioni di connessione archiviate nel file app.config per la soluzione.  Il nome dell'elemento XML nel file di configurazione che specifica le informazioni di connessione è *dataSourceSettingsName*.  
  
 L'utilizzo di un file app.config permette di cambiare il percorso della sorgente dati senza necessità di modificare il test d'unità stesso.  Per informazioni su come creare e utilizzare un file app.config, vedere [Procedura dettagliata: utilizzo di un file di configurazione per definire un'origine dati](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 Il costruttore `DataSource` con due parametri specifica la stringa di connessione per l'origine dati ed il nome della tabella contenente i dati per il metodo di test.  
  
 Le stringhe di connessione dipendono dal tipo del tipo di origine dati, ma deve contenere un elemento del provider che specifica il nome invariabile del provider di dati.  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Utilizzare TestContext.DataRow per accedere ai dati  
 Per accedere ai dati nella tabella `AddIntegersData`, utilizzare l'indicizzatore `TestContext.DataRow`.  `DataRow` è un oggetto <xref:System.Data.DataRow>, pertanto si recupereranno i valori della colonna tramite indice o tramite i nomi di colonna.  Poiché i valori vengono restituiti come oggetti, è necessario convertirli nel tipo appropriato:  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> Esecuzione del test e visualizzazione dei risultati  
 Dopo avere completato di scrivere un metodo di test, compilare il progetto di test.  Il metodo di test verrà visualizzato nella finestra di esplorazione del test nel gruppo **Test non eseguiti**.  Quando si esegue, si scrive e si riesegue i test, Esplora test mostra i risultati nei gruppi **Test non superati**, **Test superati** e **Test non eseguiti**.  È possibile scegliere **Esegui tutto** per eseguire tutti i test, oppure scegliere **Esegui…** per selezionare un sottoinsieme dei test da eseguire.  
  
 La barra dei risultati del test all'inizio di Esplora test viene animata quando il test viene eseguito.  Alla fine dell'esecuzione dei test, la barra sarà verde se i test vengono superati o rossa se i test hanno avuto esito negativo.  Un riepilogo dell'esecuzione dei test viene visualizzato nel riquadro dei dettagli nella parte inferiore della finestra di Esplora test.  Selezionare un test per visualizzare i dettagli del test nel riquadro inferiore.  
  
 Se si esegue il metodo `AddIntegers_FromDataSourceTest` nell'esempio, la barra dei risultati diventa rossa ed il metodo di test viene spostato in **Test non superati**. Un test basato su dati fallisce se qualche metodo iterato dalla sorgente dati fallisce.  Quando si sceglie un test, basato sui dati, non superato nella finestra di esplorazione del test, il riquadro dei dettagli contiene i risultati di ogni iterazione identificata dall'indice della riga di dati.  Nell'esempio, sembra che l'algoritmo `AddIntegers` non gestisca i valori negativi correttamente.  
  
 Quando il metodo sottoposto a test è stato corretto ed eseguito nuovamente, la barra dei risultati diventerà verde ed il metodo di test verrà spostato nel gruppo **Test superati**.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [How to: Create and Run a Unit Test](http://msdn.microsoft.com/it-it/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [Eseguire unit test del codice](../test/unit-test-your-code.md)   
 [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)   
 [Scrittura di unit test per .NET Framework con il framework unit test di Microsoft per codice gestito](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)