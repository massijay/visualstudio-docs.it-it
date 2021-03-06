---
title: Live Unit Testing in Visual Studio | Microsoft Docs
ms.date: 2017-03-07
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
ms.assetid: 5b51fb96-94f4-4926-92b9-262156c05b85
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
ms.translationtype: Human Translation
ms.sourcegitcommit: c559290c8e88c8b4e37feabc7014188fad15434d
ms.openlocfilehash: 0a939044b9806236cf55333c30bce24ae0fdb28a
ms.contentlocale: it-it
ms.lasthandoff: 06/08/2017

---

# <a name="live-unit-testing-with-visual-studio-2017"></a>Live Unit Testing con Visual Studio 2017

Mentre si sviluppa un'applicazione, Live Unit Testing esegue automaticamente tutti gli unit test interessati in background, visualizzando in tempo reale i risultati e il code coverage nell'IDE di Visual Studio. Durante la modifica del codice, Live Unit Testing fornisce commenti e suggerimenti sull'impatto delle modifiche sui test esistenti e indica se il nuovo codice aggiunto è coperto da uno o più test esistenti. In questo modo si riceverà un promemoria relativo alla scrittura di unit test durante la correzione di bug o l'aggiunta di nuove funzionalità.

> [!NOTE]
> Live Unit Testing è disponibile per progetti C# e Visual Basic destinati a .NET Core o .NET Framework in Visual Studio 2017 Enterprise Edition.

## <a name="supported-test-frameworks"></a>Framework di test supportati
Live Unit Testing è compatibile con i tre framework di unit test elencati nella tabella seguente. Nella tabella è indicata anche la versione minima supportata degli adattatori e dei framework. I framework di unit test sono tutti disponibili su NuGet.org.
 
<table> 
<tr>
   <th>Framework di test</th>
   <th>Versione minima dell'adattatore di Visual Studio</th>
   <th>Versione minima del framework</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio versione 2.2.0-beta3-build1187</td>
   <td>xUnit 2.0</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter versione 3.5.1</td>  
   <td>NUnit versione 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.11</td>
   <td>MSTest.TestFramework 1.1.11</td>
</tr>
</table>

Assicurarsi di rimuovere eventuali riferimenti meno recenti ad adattatori e framework di test. Se si usa MSTest, assicurarsi di rimuovere il riferimento a `Microsoft.VisualStudio.QualityTools.UnitTestFramework`. Aggiungere quelli nuovi se Live Unit Testing non funziona. 

In alcuni casi, per consentire il funzionamento di Live Unit Testing, potrebbe essere necessario ripristinare in modo esplicito i pacchetti NuGet a cui viene fatto riferimento nei progetti della soluzione. Per eseguire questa operazione, compilare in modo esplicito la soluzione (selezionare **Compila**, **Ricompila soluzione** dal menu di primo livello di Visual Studio) oppure ripristinare i pacchetti nella soluzione (fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Ripristina pacchetti NuGet**) prima di abilitare Living Unit Testing. 

#   <a name="configuring-live-unit-testing"></a>Configurazione di Live Unit Testing

Per configurare Live Unit Testing, selezionare **Strumenti**, **Opzioni** dal menu di primo livello di Visual Studio e quindi scegliere **Live Unit Testing** nel riquadro di sinistra della finestra di dialogo **Opzioni**. La figura seguente illustra le opzioni di configurazione di Live Unit Testing disponibili nella finestra di dialogo.

  ![Immagine](./media/lut-options.png)

Le opzioni configurabili includono:

- Esecuzione automatica di Live Unit Testing all'apertura di una soluzione.
- Sospensione dell'esecuzione di Live Unit Testing durante la compilazione o il debug di una soluzione oppure quando l'alimentazione a batteria del sistema scende sotto una soglia specificata.
- Intervallo dopo il quale si verifica il timeout di un test case; il valore predefinito è 30 secondi. 
- Numero massimo di processi di test creati da Live Unit Testing. 
- Livello delle informazioni scritte nella finestra **Output** di Live Unit Testing. È possibile scegliere di non visualizzare informazioni di log (Nessuno), solo i messaggi errore (Errore), messaggi di errore e messaggi informativi (Informazioni, che corrisponde al valore predefinito) o tutti i dettagli (Dettagliato).

Per visualizzare l'output dettagliato nella finestra **Output** di Live Unit Testing, è anche possibile assegnare il valore "1" a una variabile di ambiente a livello di utente denominata `VS_UTE_DIAGNOSTICS` e riavviare Visual Studio. 

Per acquisire in un file i messaggi di log dettagliati di MSBuild restituiti da Live Unit Testing, impostare la variabile di ambiente a livello di utente `LiveUnitTesting_BuildLog` sul nome del file in cui salvare il log.

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Avvio, sospensione e arresto di Live Unit Testing

Per abilitare Live Unit Testing, selezionare **Test**, **Live Unit Testing**, **Avvia** dal menu di primo livello di Visual Studio. Dopo l'abilitazione, le opzioni disponibili nel menu di **Live Unit Testing** cambiano e passano da una voce, ovvero **Avvia**, a tre, ovvero **Sospendi**, **Arresta** e **Riavvia**.

È possibile sospendere temporaneamente o arrestare completamente Live Unit Testing in qualsiasi momento. È opportuno scegliere una di queste opzioni se, ad esempio, è in corso un'operazione di refactoring e si sa che i test verranno interrotti per un certo periodo di tempo. Le tre opzioni di menu sono:

- **Sospendi**, che sospende temporaneamente l'esecuzione di Live Unit Testing. 
    Quando l'esecuzione di Live Unit Testing è sospesa, la visualizzazione del code coverage non è presente nell'editor, ma tutti i dati raccolti vengono mantenuti. Per riprendere l'esecuzione di Live Unit Testing, selezionare "Continua" dal menu Live Unit Testing menu. Live Unit Testing eseguirà le operazioni necessarie per intercettare tutte le modifiche apportate da quando è stata sospesa l'esecuzione e aggiornerà i glifi di conseguenza. 
- **Arresta**, che consente di arrestare completamente l'esecuzione di Live Unit Testing. Con questa opzione tutti i dati raccolti vengono rimossi.
- **Riavvia**, che equivale a selezionare **Arresta** seguito da **Start** dal menu **Live Unit Testing**.

##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>Accesso alla visualizzazione del code coverage nell'editor durante la digitazione

Dopo l'abilitazione, Live Unit Testing aggiorna le singole righe di codice nell'editor di Visual Studio in modo da indicare se il codice scritto è coperto da unit test e se i test coperti vengono superati.  La figura seguente mostra le righe di codice con test superati e non superati, nonché le righe di codice non coperte dai test. Le righe contraddistinte da un segno di spunta "✓" verde sono coperte solo da test superati, quelle contraddistinte da una "🞩" rossa sono coperte da uno o più test non superati, mentre quelle contraddistinte da un simbolo "" blu non sono coperte da alcun test.

  ![Image](./media/lut-codewindow.png)

La visualizzazione del code coverage di Live Unit Testing viene aggiornata immediatamente quando si modifica il codice nell'editor del codice. Durante l'elaborazione delle modifiche, la visualizzazione cambia per indicare che i dati non sono aggiornati e viene aggiunta l'immagine di un timer rotondo sotto i test superati, non superati e non coperti, come illustrato nella figura seguente.

  ![Immagine](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>Recupero delle informazioni su test superati o non superati

Per visualizzare il numero di test eseguiti su una certa riga, è possibile passare il puntatore sul simbolo di test superato o non superato nella finestra del codice. Se si fa clic sul simbolo, verrà visualizzato lo stato dei singoli test, come illustrato nella figura seguente.
 
  ![Immagine](./media/lut-failedinfo.png) 

Quando si passa il puntatore sul test non superato nella descrizione comando, questa si espande e visualizza informazioni aggiuntive sull'errore, come illustrato nell'immagine seguente. Fare clic sul test non superato nella descrizione comando per visualizzarla.

  ![Immagine](./media/lut-failedmsg.png) 

## <a name="diagnosing-and-correcting-test-failures"></a>Diagnosi e correzione degli errori di test

A partire dal test non superato è possibile eseguire facilmente il debug nel codice del prodotto, apportare modifiche e continuare a sviluppare l'applicazione. Dal momento che Live Unit Testing viene eseguito in background, non è necessario arrestare e riavviare tale funzionalità durante il ciclo di debug, modifica e continuazione.

L'errore di test illustrato nella figura precedente, ad esempio, è stato causato da un presupposto non corretto presente nel metodo di test in base al quale i caratteri non alfabetici restituiscono `true` quando vengono passati al metodo [Char.IsLower](xref:System.Char.IsLower(System.Char)). Dopo aver corretto il metodo di test, tutti i test vengono superati. Mentre si esegue questa operazione, non è necessario sospendere o arrestare l'esecuzione di Live Unit Testing.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing ed Esplora test

**Esplora test** offre in genere l'interfaccia che consente di avviare, eseguire il debug e analizzare i risultati del test. Live Unit Testing si integra con **Esplora test**. Quando Live Unit Testing non è abilitato o è stato arrestato, **Esplora Test** visualizza lo stato degli unit test durante l'ultima esecuzione di un test. Se si apportano modifiche al codice sorgente, è necessario eseguire di nuovo i test. Quando invece è abilitato Live Unit Testing, lo stato degli unit test in **Esplora test** viene aggiornato immediatamente. Non è quindi più necessario eseguire gli unit test in modo esplicito. 

Esistono tuttavia alcune differenze tra l'esecuzione automatica di Live Unit Testing e l'aggiornamento dei risultati dei test e l'esecuzione esplicita di test da **Esplora test**. Sono inclusi:

- Durante l'esecuzione o il debug di test dalla finestra Esplora test vengono eseguiti file binari normali, mentre con Live Unit Testing vengono eseguiti file instrumentati. 
- Live Unit Testing non crea un nuovo dominio applicazione per eseguire i test, ma esegue i test dal dominio predefinito. Quando i test vengono eseguiti dalla finestra **Esplora test**, viene invece creato un nuovo dominio applicazione.
- Live Unit Testing esegue i test di ogni assembly di test in modo sequenziale. Se si eseguono più test dalla finestra **Esplora test** e il pulsante **Esegui test in parallelo** è selezionato, i test verranno eseguiti in parallelo.

## <a name="including-and-excluding-test-projects-and-test-methods"></a>Inclusione ed esclusione di progetti e metodi di test

Per le soluzioni che contengono molti progetti di test, è possibile controllare i progetti e i singoli metodi di un progetto inclusi in Live Unit Testing. 

Se ad esempio una soluzione contiene centinaia di progetti di test, è possibile selezionare un set specifico di progetti di test da includere in Live Unit Testing. Per selezionare i singoli progetti negli unit test, eseguire le operazioni seguenti dopo aver avviato Live Unit Testing:

1.  Fare clic con il pulsante destro del mouse sulla soluzione in Esplora soluzioni e scegliere **Test attivi**, **Escludi** per escludere l'intera soluzione.
2.  Fare clic con il pulsante destro del mouse su ogni progetto di test da includere nei test e scegliere **Test attivi**, **Includi**.
 
Per includere o escludere singoli metodi di test, si usa la finestra dell'editor del codice. Fare clic con il pulsante destro del mouse sulla firma del metodo di test nella finestra dell'editor del codice e scegliere **Test attivi**, **Includi** o **Test attivi**, **Escludi**. 

In alternativa, è anche possibile applicare l'attributo [<ExcludeFromCodeCoverage>](https://msdn.microsoft.com/library/system.diagnostics.codeanalysis.excludefromcodecoverageattribute.aspx) per evitare a livello di codice che metodi, classi o strutture restituiscano informazioni sul code coverage in Live Unit Testing.

In Live Unit Testing lo stato di inclusione/esclusione viene salvato come impostazione utente e memorizzato alla chiusura o alla riapertura di una soluzione. 

## <a name="see-also"></a>Vedere anche

[Live Unit Testing Blog](https://go.microsoft.com/fwlink/?linkid=842514)  (Blog di Live Unit Testing)  
[Domande frequenti su Live Unit Testing](live-unit-testing-faq.md)    
[Channel 9 Video: Live Unit Testing in Visual Studio 2017](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105) (Video di Channel 9: Live Unit Testing in Visual Studio 2017)


