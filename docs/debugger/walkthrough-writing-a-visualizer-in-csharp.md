---
title: "Procedura dettagliata: scrittura di un visualizzatore in C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "visualizzatori, scrittura"
  - "procedure dettagliate [Visual Studio], visualizzatori"
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura dettagliata: scrittura di un visualizzatore in C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura dettagliata viene descritto come utilizzare C\# per scrivere un visualizzatore semplice,  che consente di visualizzare il contenuto di una stringa in una finestra di messaggio di Windows Form.  Questo semplice visualizzatore di stringhe non è particolarmente utile, ma consente di acquisire familiarità con le operazioni di base da effettuare per creare visualizzatori più utili per altri tipi di dati.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Il codice del visualizzatore deve essere inserito in una DLL, che verrà letta dal debugger.  La prima operazione da effettuare consiste pertanto nel creare un progetto Libreria di classi per la DLL.  
  
#### Per creare un progetto Libreria di classi  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi **Nuovo progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** selezionare **Visual C\#** in **Tipo progetto**.  
  
3.  Nella casella **Modelli** scegliere **Libreria di classi**.  
  
4.  Nella casella **Nome** digitare un nome appropriato per la libreria di classi, ad esempio MyFirstVisualizer.  
  
5.  Fare clic su **OK**.  
  
 Dopo avere creato la libreria di classi, è necessario aggiungere un riferimento a Microsoft.VisualStudio.DebuggerVisualizers.DLL in modo da poter utilizzare le classi definite in questa DLL.  Prima di aggiungere il riferimento, è tuttavia necessario rinominare alcune classi con nomi significativi.  
  
#### Per rinominare Class1.cs e aggiungere Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su Class1.cs e scegliere **Rinomina** dal menu di scelta rapida.  
  
2.  Sostituire Class1.cs con un nome significativo, ad esempio DebuggerSide.cs.  
  
    > [!NOTE]
    >  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la dichiarazione di classe viene modificata automaticamente in base al nuovo nome di file DebuggerSide.cs.  
  
3.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Riferimenti**, quindi scegliere **Aggiungi riferimento** dal menu di scelta rapida.  
  
4.  Nella scheda **.NET** della finestra di dialogo **Aggiungi riferimento** scegliere Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Fare clic su **OK**.  
  
6.  In DebuggerSide.cs aggiungere la seguente istruzione alle istruzioni `using`:  
  
    ```  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 A questo punto è possibile creare il codice sul lato debugger.  Questo codice verrà eseguito all'interno del debugger per visualizzare le informazioni desiderate.  È innanzitutto necessario modificare la dichiarazione dell'oggetto `DebuggerSide` in modo da ereditare dalla classe di base `DialogDebuggerVisualizer`.  
  
#### Per ereditare da DialogDebuggerVisualizer  
  
1.  In DebuggerSide.cs posizionarsi sulla seguente riga di codice:  
  
    ```  
    public class DebuggerSide  
    ```  
  
2.  Modificare il codice in:  
  
    ```  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` dispone di un metodo astratto \(`Show`\) di cui è necessario eseguire l'override.  
  
#### Per eseguire l'override del metodo DialogDebuggerVisualizer.Show  
  
-   In `public class DebuggerSide` aggiungere il seguente metodo:  
  
    ```  
    override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 Il metodo `Show` contiene il codice per la creazione della finestra di dialogo del visualizzatore o di un'altra interfaccia utente e per la visualizzazione delle informazioni passate al visualizzatore dal debugger.  Questo codice deve essere aggiunto dallo sviluppatore.  A tale scopo, in questa procedura dettagliata verrà utilizzata una finestra di messaggio di Windows Form.  È innanzitutto necessario aggiungere un riferimento e l'istruzione `using` per System.Windows.Forms.  
  
#### Per aggiungere System.Windows.Forms  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Riferimenti**, quindi scegliere **Aggiungi riferimento** dal menu di scelta rapida.  
  
2.  Nella scheda **.NET** della finestra di dialogo **Aggiungi riferimento** scegliere System.Windows.Forms.DLL.  
  
3.  Fare clic su **OK**.  
  
4.  In DebuggerSide.cs aggiungere la seguente istruzione alle istruzioni `using`:  
  
    ```  
    using System.Windows.Forms;  
    ```  
  
 A questo punto è necessario aggiungere una sezione di codice per la creazione e la visualizzazione dell'interfaccia utente del visualizzatore.  Poiché si tratta del primo visualizzatore creato, l'interfaccia utente sarà semplice e verrà utilizzata una finestra di messaggio.  
  
#### Per visualizzare l'output del visualizzatore in una finestra di dialogo  
  
1.  Nel metodo `Show` aggiungere la riga di codice seguente:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     Questo codice di esempio non include la gestione degli errori.  In un vero visualizzatore o in un qualsiasi altro tipo di applicazione è consigliabile includere la gestione degli errori.  
  
2.  Scegliere **Compila MyFirstVisualizer** dal menu **Compila**.  La compilazione del progetto dovrebbe avvenire senza problemi.  Correggere gli eventuali errori di compilazione prima di continuare.  
  
 Il codice sul lato debugger è stato completato.  È tuttavia necessario eseguire un altro passaggio, ovvero specificare l'attributo che indica al lato dell'oggetto del debug la raccolta di classi che comprende il visualizzatore.  
  
#### Per aggiungere il codice dell'oggetto del debug  
  
1.  Aggiungere il seguente codice di attributo a DebuggerSide.cs, dopo le istruzioni `using` ma prima di `namespace MyFirstVisualizer`:  
  
    ```  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target  = typeof(System.String),  
    Description  = "My First Visualizer")]  
    ```  
  
2.  Scegliere **Compila MyFirstVisualizer** dal menu **Compila**.  La compilazione del progetto dovrebbe avvenire senza problemi.  Correggere gli eventuali errori di compilazione prima di continuare.  
  
 A questo punto il visualizzatore è pronto.  Se la procedura è stata completata in modo corretto, è possibile compilare il visualizzatore e installarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Prima di installare un visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è tuttavia consigliabile testarlo per assicurarsi che funzioni in modo corretto.  Di seguito viene descritto come creare un test harness per eseguire il visualizzatore senza installarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### Per aggiungere un metodo di test per visualizzare il visualizzatore  
  
1.  Aggiungere il metodo seguente alla classe `public DebuggerSide`:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  Scegliere **Compila MyFirstVisualizer** dal menu **Compila**.  La compilazione del progetto dovrebbe avvenire senza problemi.  Correggere gli eventuali errori di compilazione prima di continuare.  
  
 Creare quindi un progetto eseguibile per chiamare la DLL del visualizzatore.  Per motivi di semplicità, verrà utilizzato un progetto di applicazione console.  
  
#### Per aggiungere un progetto applicazione console alla soluzione  
  
1.  Scegliere **Aggiungi** dal menu **File**, quindi **Nuovo progetto**.  
  
2.  Nel riquadro **Modelli** della finestra di dialogo **Aggiungi nuovo progetto** scegliere **Applicazione console**.  
  
3.  Nella casella **Nome** digitare un nome significativo per l'applicazione console, ad esempio `MyTestConsole`.  
  
4.  Fare clic su **OK**.  
  
 A questo punto è necessario aggiungere i riferimenti appropriati affinché MyTestConsole possa chiamare MyFirstVisualizer.  
  
#### Per aggiungere riferimenti necessari a MyTestConsole  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **MyTestConsole**, quindi scegliere **Aggiungi riferimento** dal menu di scelta rapida.  
  
2.  Nella scheda **.NET** della finestra di dialogo **Aggiungi riferimento** scegliere Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
3.  Fare clic su **OK**.  
  
4.  Fare clic con il pulsante destro del mouse su **MyTestConsole** e scegliere di nuovo **Aggiungi riferimento**.  
  
5.  Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **Progetti** e quindi selezionare MyFirstVisualizer.  
  
6.  Fare clic su **OK**.  
  
 A questo punto verrà aggiunto il codice per completare il test harness.  
  
#### Per aggiungere codice a MyTestConsole  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su Program.cs e scegliere **Rinomina** dal menu di scelta rapida.  
  
2.  Sostituire Program.cs con un nome più significativo, ad esempio TestConsole.cs.  
  
     **Nota** In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la dichiarazione di classe viene modificata automaticamente in base al nuovo nome di file TestConsole.cs.  
  
3.  In TestConsole.cs aggiungere il codice seguente alle istruzioni `using`:  
  
    ```  
    using MyFirstVisualizer;  
    ```  
  
4.  Nel metodo `Main` aggiungere il codice seguente:  
  
    ```  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 A questo punto è possibile testare il visualizzatore.  
  
#### Per eseguire il test del visualizzatore  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **MyTestConsole**, quindi scegliere **Imposta come progetto di avvio** dal menu di scelta rapida.  
  
2.  Scegliere **Avvia** dal menu **Debug**.  
  
     L'applicazione console verrà avviata e verrà aperto il visualizzatore contenente la stringa "Hello, World".  
  
 Il visualizzatore  è stato compilato e sottoposto a test.  
  
 Se si desidera utilizzare il visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anziché chiamarlo semplicemente dal test harness, è necessario installarlo.  Per ulteriori informazioni, vedere [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).  
  
## Utilizzo del modello per la creazione di elementi visualizzatore  
 Fino a questo momento, in questa procedura dettagliata è stato descritto come creare un visualizzatore manualmente  a scopo di esercitazione.  Esiste tuttavia una procedura più facile per creare un visualizzatore, che consiste nell'utilizzare il modello per la creazione di elementi visualizzatore.  
  
 È innanzitutto necessario creare un nuovo progetto Libreria di classi.  
  
#### Per creare una nuova libreria di classi  
  
1.  Scegliere **Aggiungi** dal menu **File**, quindi **Nuovo progetto**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare **Visual C\#** in **Tipo progetto**.  
  
3.  Nella casella **Modelli** scegliere **Libreria di classi**.  
  
4.  Nella casella **Nome** digitare un nome appropriato per la libreria di classi, ad esempio MySecondVisualizer.  
  
5.  Fare clic su **OK**.  
  
 A questo punto è possibile aggiungere un elemento visualizzatore alla libreria.  
  
#### Per aggiungere un elemento visualizzatore  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su MySecondVisualizer.  
  
2.  Scegliere **Aggiungi** dal menu di scelta rapida, quindi **Nuovo elemento**.  
  
3.  Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere **Modelli Visual Studio installati** in **Modelli** e selezionare **Visualizzatore debugger**.  
  
4.  Nella casella **Nome** immettere un nome appropriato, ad esempio SecondVisualizer.cs.  
  
5.  Scegliere **Aggiungi**.  
  
 La procedura per la creazione di un visualizzatore a partire da un modello è stata completata.  Aprire il file SecondVisualizer.cs e controllare il codice aggiunto automaticamente dal modello.  Provare a modificare il codice.  Dopo avere appreso le nozioni di base, è possibile iniziare a creare visualizzatori personalizzati più utili e complessi.  
  
## Vedere anche  
 [Architettura del visualizzatore](../debugger/visualizer-architecture.md)   
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Visualizzatori](../debugger/create-custom-visualizers-of-data.md)