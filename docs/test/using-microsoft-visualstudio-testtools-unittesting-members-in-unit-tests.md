---
title: "Utilizzo di membri Microsoft.VisualStudio.TestTools.UnitTesting in unit test | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mlearned"
manager: "douge"
---
# Utilizzo di membri Microsoft.VisualStudio.TestTools.UnitTesting in unit test
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il framework unit test supporta l'esecuzione di unit test in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Per la codifica degli unit test, utilizzare le classi e i membri nello spazio dei nomi <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>.  Questi elementi devono essere utilizzati quando si scrivono unit test completamente nuovi oppure quando si definiscono unit test generati dal codice sottoposto al test.  
  
## Gruppi di elementi  
 Per fornire una panoramica più accurata del framework unit test, in questa sezione gli elementi dello spazio dei nomi UnitTesting vengono organizzati in gruppi di funzioni correlate.  
  
> [!NOTE]
>  Gli elementi dell'attributo, i cui nomi terminano con la stringa Attribute, possono essere utilizzati con o senza la stringa Attribute.  Ad esempio, nei due esempi di codice seguenti il funzionamento è identico:  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### Elementi utilizzati per il test basato sui dati  
 Utilizzare i seguenti elementi per impostare unit test basati sui dati.  Per ulteriori informazioni, vedere [Procedura: Creare uno unit test basato sui dati](../test/how-to-create-a-data-driven-unit-test.md) e [Procedura dettagliata: utilizzo di un file di configurazione per definire un'origine dati](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection>  
  
## Attributi utilizzati per stabilire un ordine di chiamata  
 Un elemento di codice decorato con uno dei seguenti attributi viene chiamato al momento specificato.  Per ulteriori informazioni, vedere [Anatomy of a Unit Test](http://msdn.microsoft.com/it-it/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
### Per gli assembly  
 AssemblyInitialize e AssemblyCleanup vengono chiamati subito dopo che l'assembly è stato caricato e subito prima che venga scaricato.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute>  
  
### Per le classi  
 ClassInitialize e ClassCleanup vengono chiamati subito dopo che la classe è stata caricata e subito prima che venga scaricata.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute>  
  
### Per i metodi di test  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute>  
  
## Attributi utilizzati per identificare le classi e i metodi di test  
 Tutte le classi di test devono disporre dell'attributo TestClass e tutti i metodi di test devono disporre dell'attributo TestMethod.  Per ulteriori informazioni, vedere [Anatomy of a Unit Test](http://msdn.microsoft.com/it-it/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute>  
  
## Classi Assert ed eccezioni correlate  
 Gli unit test consentono di verificare il comportamento di specifiche applicazioni grazie all'utilizzo di vari tipi di eccezioni, attributi e istruzioni Assert.  Per ulteriori informazioni, vedere [Utilizzo di classi Assert](../test/using-the-assert-classes.md).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute>  
  
## Classe TestContext  
 I seguenti attributi e relativi valori vengono visualizzati nella finestra Proprietà di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per un determinato metodo di test.  Questi attributi non sono stati realizzati per accedere tramite il codice dello unit test.  Invece, sono in grado di modificare l'utilizzo o l'esecuzione di unit test tramite l'ambiente IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oppure tramite il modulo del test [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ad esempio, alcuni di questi attributi sono visualizzati come colonne nell'Editor elenco dei test e nella finestra Risultati test e possono quindi essere utilizzati per raggruppare e ordinare i test e i relativi risultati.  Uno di questi attributi è TestPropertyAttribute, che consente di aggiungere i metadati arbitrari agli unit test.  Ad esempio, è possibile utilizzarlo per archiviare il nome dell'esito del test coperto da questo test, contrassegnando lo unit test con `[TestProperty("TestPass", "Accessibility")]`.  In alternativa, è possibile utilizzarlo per archiviare un indicatore di quale tipo di test è: `[TestProperty("TestKind", "Localization")]`.  La proprietà che viene creata utilizzando questo attributo e il valore della proprietà assegnato vengono visualizzati nella finestra Proprietà di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sotto l'intestazione **Specifico del test**.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute>  
  
## Classi di configurazione del test  
  
-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection>  
  
## Attributi utilizzati per la generazione di rapporti  
 Gli attributi in questa sezione consentono di collegare il metodo di test decorato alle entità nella gerarchia del progetto di un progetto team [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute>  
  
## Classi utilizzate con accessi privati  
 Come descritto in [Using Publicize to Create a Private Accessor](http://msdn.microsoft.com/it-it/2056c6a7-6672-42a7-8f53-fead33c56deb), è possibile generare uno unit test per un metodo privato.  Tale operazione crea una classe di accesso privata che consente di creare istanze di un oggetto della classe PrivateObject.  La classe PrivateObject è una classe wrapper in cui la reflection viene utilizzata come parte del processo della funzione di accesso privato.  La classe PrivateType è simile, ma viene utilizzata per chiamare i metodi statici privati anziché i metodi di istanza privata.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType>  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>