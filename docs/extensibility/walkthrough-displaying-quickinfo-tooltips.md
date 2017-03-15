---
title: 'Procedura dettagliata: Visualizzazione delle descrizioni comandi informazioni rapide | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b533e77a2310194b2bccc225f9902e5a8d502da5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Procedura dettagliata: Visualizzazione delle descrizioni comandi informazioni rapide
Informazioni rapide sono una funzionalità IntelliSense che consente di visualizzare le firme del metodo e le descrizioni quando l'utente sposta il puntatore su un nome di metodo. È possibile implementare funzionalità basate sul linguaggio, come informazioni rapide, che definisce gli identificatori per il quale si desidera fornire le descrizioni di informazioni rapide e quindi creare una descrizione comandi in cui visualizzare il contenuto. È possibile definire informazioni rapide nel contesto di un servizio di linguaggio, è possibile definire il tipo di estensione e il contenuto di nome file e visualizzare le informazioni rapide per il solo tipo, o è possibile visualizzare informazioni rapide per un tipo di contenuto esistente (ad esempio "text"). Questa procedura dettagliata viene illustrato come visualizzare informazioni rapide per il tipo di contenuto "text".  
  
 Nell'esempio di informazioni rapide in questa procedura dettagliata vengono visualizzate le descrizioni comandi quando si sposta il puntatore del mouse su un nome di metodo. Questa progettazione è necessario implementare queste quattro interfacce:  
  
-   interfaccia di origine  
  
-   interfaccia del provider di origine  
  
-   interfaccia del controller  
  
-   interfaccia provider controller  
  
 I provider di origine e di controller sono componenti Managed Extensibility Framework (MEF) e sono responsabili per l'esportazione di classi di origine e il controller e l'importazione dei servizi e di connessione, ad esempio il <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, che consente di creare buffer di testo della descrizione comando e <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, che attiva la sessione di informazioni rapide.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> </xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>  
  
 In questo esempio, l'origine di informazioni rapide utilizza un elenco hardcoded di nomi di metodo e le descrizioni, ma in implementazioni complete, il servizio di linguaggio e la documentazione del linguaggio sono responsabili per fornire tale contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo, selezionare **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `QuickInfoTest`.  
  
2.  Aggiungere un modello di elemento Editor classificatore al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementazione dell'origine di informazioni rapide  
 L'origine di informazioni rapide è responsabile della raccolta al set di identificatori e le relative descrizioni e aggiungendo il contenuto del buffer di testo della descrizione comando quando viene rilevato uno degli identificatori. In questo esempio, gli identificatori e le relative descrizioni vengono aggiunti solo nel costruttore di origine.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Per implementare l'origine di informazioni rapide  
  
1.  Aggiungere un file di classe e denominarla `TestQuickInfoSource`.  
  
2.  Aggiungere un riferimento a Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Aggiungere le seguenti istruzioni imports.  
  
     [!code-vb[N.&1; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n.&1;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>e denominarla `TestQuickInfoSource`.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[N.&2; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n.&2;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Aggiungere campi per il provider di origine di informazioni rapide, il buffer di testo e un set di nomi di metodi e le firme del metodo. In questo esempio, i nomi dei metodi e le firme vengono inizializzate le `TestQuickInfoSource` costruttore.  
  
     [!code-vb[N.&3; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n.&3;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Aggiungere un costruttore che imposta il provider di origine di informazioni rapide e buffer di testo e popola il set di nomi di metodo e le firme del metodo e le descrizioni.  
  
     [!code-vb[N.&4; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n.&4;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>(metodo).</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> In questo esempio, il metodo trova la parola o la parola precedente se il cursore si trova alla fine di una riga o di un buffer di testo. Se la parola è uno dei nomi di metodo, la descrizione di tale nome viene aggiunto al contenuto di informazioni rapide.  
  
     [!code-vb[N.&5; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n.&5;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  È inoltre necessario implementare un metodo Dispose (), poiché <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>implementa <xref:System.IDisposable>:</xref:System.IDisposable> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[VSSDKQuickInfoTest&6;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n.&6;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementazione di un Provider di origine di informazioni rapide  
 Il provider dell'origine di informazioni rapide serve principalmente per esportare se stessa come componente MEF e creare un'istanza dell'origine di informazioni rapide. Poiché si tratta di un componente MEF, è possibile importare altri componenti MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Implementare un provider di origine di informazioni rapide  
  
1.  Dichiarare un provider di origine di informazioni rapide denominato `TestQuickInfoSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>"Descrizione comando informazioni rapide dell'origine di", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>di prima = "default" e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>di "text".</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
     [!code-vb[VSSDKQuickInfoTest&#7;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#7;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Importare due servizi di editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>e <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, come proprietà di `TestQuickInfoSourceProvider`.</xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
     [!code-vb[N.&8; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n.&8;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>per restituire un nuovo `TestQuickInfoSource`.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&9;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&9;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementazione di un Controller di informazioni rapide  
 Informazioni rapide controller determinano quando devono essere visualizzata nelle informazioni rapide. In questo esempio, informazioni rapide viene visualizzata quando il puntatore si trova su una parola che corrisponde a uno dei nomi di metodo. Il controller di informazioni rapide implementa un gestore di eventi di passaggio del mouse che attiva una sessione di informazioni rapide.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Per implementare un controller di informazioni rapide  
  
1.  Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>e denominarla `TestQuickInfoController`.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>  
  
     [!code-vb[VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Aggiungere campi privati per la visualizzazione di testo, i buffer di testo rappresentati nella visualizzazione di testo, la sessione di informazioni rapide e il provider di controller di informazioni rapide.  
  
     [!code-vb[VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Aggiungere un costruttore che imposta i campi e aggiunta il gestore di eventi del mouse al passaggio del mouse.  
  
     [!code-vb[VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Aggiungere il gestore di eventi di passaggio del mouse che attiva la sessione di informazioni rapide.  
  
     [!code-vb[VSSDKQuickInfoTest&13;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&13;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>metodo in modo che rimuove il gestore dell'evento del mouse al passaggio del mouse quando il controller viene disconnesso dalla visualizzazione del testo.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&14;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&14;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>(metodo) e <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>metodo come metodi vuoti per questo esempio.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementazione del Provider di informazioni rapide Controller  
 Il provider del controller di informazioni rapide serve principalmente per esportare se stessa come componente MEF e creare un'istanza del controller di informazioni rapide. Poiché si tratta di un componente MEF, è possibile importare altri componenti MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Per implementare il provider di controller di informazioni rapide  
  
1.  Dichiarare una classe denominata `TestQuickInfoControllerProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>di "Descrizione comando informazioni rapide Controller" e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>di "testo":</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>  
  
     [!code-vb[VSSDKQuickInfoTest&#16;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#16;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Importazione di <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>come una proprietà.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>  
  
     [!code-vb[N.&17; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n.&17;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>metodo creando un'istanza del controller di informazioni rapide.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#18;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#18;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione QuickInfoTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Per compilare e testare la soluzione QuickInfoTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e tipo di testo che include le parole "Aggiungi" e "sottrazione".  
  
4.  Spostare il puntatore su una delle occorrenze di "Aggiungi". La firma e la descrizione di `add` metodo deve essere visualizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione nome File](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
