---
title: Eseguire unit test del codice | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 62
ms.author: douge
manager: douge
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: 2e777b966cd332871533434728a6a565c51a5336
ms.contentlocale: it-it
ms.lasthandoff: 05/26/2017

---
# <a name="unit-test-your-code"></a>Eseguire unit test del codice
Gli unit test rappresentano per sviluppatori e tester un modo rapido per verificare la presenza di errori di logica nei metodi delle classi in progetti [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)], [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] e [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)].  
  
 Gli strumenti di unit test includono:  
  
1.  **Esplora test.** Esplora test consente di eseguire unit test e visualizzare i relativi risultati. Esplora test può utilizzare qualsiasi framework per unit test, incluso un framework di terze parti provvisto di un apposito adapter.  
  
2.  **Framework per unit test di Microsoft per codice gestito.** Il framework per unit test di Microsoft per il codice gestito viene installato con Visual Studio e fornisce un framework per testare il codice .NET.  
  
3.  **Framework per unit test di Microsoft per C++.** Il framework per unit test di Microsoft per C++ viene installato con Visual Studio e fornisce un framework per testare il codice nativo.  
  
4.  **Strumenti di code coverage.** È possibile determinare la quantità di codice del prodotto sottoposta agli unit test da un comando in Esplora test.  
  
5.  **Framework di isolamento Microsoft Fakes.** Il framework di isolamento Microsoft Fakes può creare classi e metodi sostitutivi per il codice di sistema e di produzione che creano le dipendenze nel codice sottoposto a test. L'implementazione di delegati falsi per una funzione consente di controllare il comportamento e l'output dell'oggetto di dipendenza.  
  
 È anche possibile creare [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) che esplorano il codice .NET per generare dati di test e un gruppo di unit test. Per ogni istruzione nel codice viene generato un input di test che eseguirà l'istruzione. Viene eseguita un'analisi del caso per ogni branch condizionale nel codice.  
  
## <a name="key-tasks"></a>Attività chiave  
 Usare gli argomenti seguenti per la comprensione e la creazione di unit test:  
  
|Attività|Argomenti correlati|  
|-----------|-----------------------|  
|**Guide introduttive e procedure dettagliate:** usare gli argomenti seguenti per ottenere informazioni sugli unit test in Visual Studio da esempi di codice.|-   [Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Guida introduttiva allo sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Aggiunta di unit test alle applicazioni C++ esistenti](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Unit test di codice nativo con Esplora test](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**Unit test con Esplora test:** informazioni su come Esplora test può agevolare la creazione di unit test più produttivi ed efficienti.|-   [Nozioni fondamentali sugli unit test](../test/unit-test-basics.md)<br />-   [Creare un progetto di unit test](../test/create-a-unit-test-project.md)<br />-   [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)<br />-   [Installare framework di unit test di terze parti](../test/install-third-party-unit-test-frameworks.md)<br />-   [Aggiornamento di unit test da Visual Studio 2010](http://msdn.microsoft.com/en-us/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**Testing unità di codice gestito:**|-   [Scrittura di unit test per .NET Framework con il framework unit test di Microsoft per codice gestito](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Eseguire unit test del codice**|-   [Scrittura di unit test per C-C++ con il framework di unit test Microsoft per C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Isolamento degli unit test**|-   [Isolamento del codice sottoposto a test con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Usare code coverage per identificare la percentuale del codice del progetto in fase di test mediante unit test:** informazioni sulla funzionalità code coverage degli strumenti di test di [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)].|-   [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Eseguire analisi di stress e prestazioni usando test di carico per gli unit test:** è possibile creare un test di carico e aggiungervi gli unit test per isolare problemi di prestazioni e di stress nell'applicazione. **Nota:** per la creazione e l'uso dei test di carico è necessario Visual Studio Enterprise.|-   [Creazione e modifica dei test di carico](http://msdn.microsoft.com/en-us/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Procedura: Aggiungere test prestazioni Web e unit test a uno scenario di test di carico](http://msdn.microsoft.com/en-us/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Procedura: Rimuovere test Web e unit test da uno scenario di test di carico](http://msdn.microsoft.com/en-us/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**Impostare e applicare controlli di qualità:** è possibile creare controlli di qualità che stabiliscano l'esecuzione dei test prima dell'archiviazione del codice, in modo da garantire la qualità di quest'ultimo.|-   [Impostare e applicare controlli di qualità](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Estendere il tipo di unit test:** è possibile aggiungere ai test funzionalità che possono non essere presenti nel framework di unit test. Ad esempio, è possibile aggiungere una proprietà di test che specifica se un test deve essere eseguito o meno come utente normale. Oppure è possibile estendere il framework per aggiungere attributi di riga a un metodo e utilizzare i dati in tale riga all'interno del test.|Per codice di esempio su come estendere il framework per unit test, visitare il [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkId=185591) seguente.|  
|**Impostare le opzioni di test:** ad esempio, è possibile specificare dove archiviare i risultati dei test.|[Configurazione di unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
 [Revisione dei risultati dei test in Microsoft Test Manager](http://msdn.microsoft.com/en-us/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 Vengono descritti i risultati dei test e le relative modalità di utilizzo, ad esempio come visualizzarli, salvarli ed eliminarli.  
  
 [Esecuzione di test di sistema mediante Microsoft Visual Studio](/devops-test-docs/test/running-automated-tests-using-microsoft-visual-studio)  
  
 Fornisce collegamenti alle informazioni sull'utilizzo di Visual Studio rispetto all'utilizzo di  [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] per eseguire test automatizzati.  
  
## <a name="reference"></a>Riferimento  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Viene descritto lo spazio dei nomi UnitTesting, che rende disponibili attributi, eccezioni, asserzioni e altre classi che supportano il testing unità.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Viene descritto lo spazio dei nomi UnitTesting.Web, che estende lo spazio dei nomi UnitTesting fornendo il supporto per gli unit test [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e dei servizi Web.  
  
## <a name="external-resources"></a>Risorse esterne  
  
### <a name="videos"></a>Video  
 [Channel 9: Unit testing your Windows Store apps built using XAML (Testing unità delle app di Windows Store scritte in XAML)](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Forum  
 [Visual Studio Unit Testing](http://go.microsoft.com/fwlink/?LinkId=224477) (Testing unità con Visual Studio)  
  
### <a name="guidance"></a>Materiale sussidiario  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside](http://go.microsoft.com/fwlink/?LinkID=255188) (Test per la distribuzione continua con Visual Studio 2012 - Capitolo 2: Testing unità: Test interni)  
  
### <a name="reference"></a>Riferimento  
 [Indice dei contenuti relativi agli unit test](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>Vedere anche  
 [Migliorare la qualità del codice](/visualstudio/test/improve-code-quality)   
 [Test dell'applicazione](/devops-test-docs/test/test-apps-early-and-often)

