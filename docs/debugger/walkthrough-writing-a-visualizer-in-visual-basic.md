---
title: "Procedura dettagliata: scrittura di un visualizzatore in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Procedura dettagliata: scrittura di un visualizzatore in Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura dettagliata viene descritto come utilizzare [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] per scrivere un visualizzatore semplice  che consente di visualizzare il contenuto di una stringa in una finestra di messaggio di Windows Form.  Questo visualizzatore semplice di stringhe è un esempio base per illustrare la creazione di visualizzatori per altri tipi di dati più applicabili ai progetti.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Il codice del visualizzatore deve essere inserito in una DLL, che verrà letta dal debugger.  La prima operazione da effettuare consiste nel creare un progetto Libreria di classi per la DLL.  
  
## Creare e preparare un progetto Libreria di classi  
  
#### Per creare un progetto Libreria di classi  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi **Nuovo progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** selezionare **Visual Basic** in **Tipo progetto**.  
  
3.  Nella casella **Modelli** scegliere **Libreria di classi**.  
  
4.  Nella casella **Nome** digitare un nome appropriato per la libreria di classi, ad esempio MyFirstVisualizer.  
  
5.  Scegliere **OK**.  
  
 Dopo avere creato la libreria di classi, è necessario aggiungere un riferimento a Microsoft.VisualStudio.DebuggerVisualizers.DLL in modo da poter utilizzare le classi definite in questa DLL.  Innanzitutto è opportuno assegnare al progetto un nome significativo.  
  
#### Per rinominare Class1.vb e aggiungere Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Class1.vb** e scegliere **Rinomina** dal menu di scelta rapida.  
  
2.  Sostituire Class1.vb con un nome significativo, ad esempio DebuggerSide.vb.  
  
    > [!NOTE]
    >  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la dichiarazione di classe viene modificata automaticamente in base al nuovo nome di file DebuggerSide.vb.  
  
3.  In **Esplora soluzioni**, fare clic con il pulsante destro del mouse su **My First Visualizer** e scegliere **Aggiungi riferimento** dal menu di scelta rapida.  
  
4.  Nella scheda **.NET** della finestra di dialogo **Aggiungi riferimento** scegliere Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Scegliere **OK**.  
  
6.  In DebuggerSide.vb aggiungere l'istruzione seguente alle istruzioni `Imports`:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## Aggiungere il codice sul lato debugger  
 A questo punto è possibile creare il codice sul lato debugger.  Questo codice verrà eseguito all'interno del debugger per visualizzare le informazioni desiderate.  È innanzitutto necessario modificare la dichiarazione dell'oggetto `DebuggerSide` in modo da ereditare dalla classe di base `DialogDebuggerVisualizer`.  
  
#### Per ereditare da DialogDebuggerVisualizer  
  
1.  In DebuggerSide.vb posizionarsi sulla riga di codice seguente:  
  
    ```  
    Public Class DebuggerSide  
    ```  
  
2.  Modificare il codice nel modo seguente:  
  
    ```  
    Public Class DebuggerSide  
    Inherits DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` dispone di un metodo astratto, `Show`, di cui è necessario eseguire l'override.  
  
#### Per eseguire l'override del metodo DialogDebuggerVisualizer.Show  
  
-   In `public class DebuggerSide` aggiungere il metodo seguente:  
  
    ```  
    Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
        End Sub  
    ```  
  
 Il metodo `Show` contiene il codice per la creazione della finestra di dialogo del visualizzatore o un'altra interfaccia utente e per la visualizzazione delle informazioni passate al visualizzatore dal debugger.  Questo codice deve essere aggiunto dallo sviluppatore.  A tale scopo, in questa procedura dettagliata verrà utilizzata una finestra di messaggio Windows Form.  È innanzitutto necessario aggiungere un riferimento e l'istruzione `Imports` per <xref:System.Windows.Forms>.  
  
#### Per aggiungere System.Windows.Forms  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Riferimenti**, quindi scegliere **Aggiungi riferimento** dal menu di scelta rapida.  
  
2.  Nella scheda **.NET** della finestra di dialogo **Aggiungi riferimento** scegliere **System.Windows.Forms**.  
  
3.  Scegliere **OK**.  
  
4.  In DebuggerSide.cs aggiungere l'istruzione seguente alle istruzioni `Imports`:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## Creare un'interfaccia utente del visualizzatore  
 A questo punto è necessario aggiungere una sezione di codice per la creazione e la visualizzazione dell'interfaccia utente del visualizzatore.  Poiché si tratta del primo visualizzatore creato, l'interfaccia utente sarà semplice e verrà utilizzata una finestra di messaggio.  
  
#### Per visualizzare l'output del visualizzatore in una finestra di dialogo  
  
1.  Nel metodo `Show` aggiungere la riga di codice seguente:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Questo codice di esempio non include la gestione degli errori.  In un vero visualizzatore o in un qualsiasi altro tipo di applicazione è consigliabile includere la gestione degli errori.  
  
2.  Scegliere **Compila MyFirstVisualizer** dal menu **Compila**.  La compilazione del progetto dovrebbe avvenire senza problemi.  Correggere gli eventuali errori di compilazione prima di continuare.  
  
## Aggiungere l'attributo necessario  
 Il codice sul lato debugger è stato completato.  È tuttavia necessario eseguire un altro passaggio, ovvero specificare l'attributo che indica al lato dell'oggetto del debug la raccolta di classi che comprende il visualizzatore.  
  
#### Per aggiungere il codice del lato oggetto del debug  
  
1.  Aggiungere il codice di attributo seguente a DebuggerSide.vb, dopo le istruzioni `Imports` ma prima di `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  Scegliere **Compila MyFirstVisualizer** dal menu **Compila**.  La compilazione del progetto dovrebbe avvenire senza problemi.  Correggere gli eventuali errori di compilazione prima di continuare.  
  
## Creare un test harness  
 A questo punto il visualizzatore è pronto.  Se la procedura è stata completata in modo corretto, è possibile compilare il visualizzatore e installarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Prima di installare un visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è tuttavia consigliabile testarlo per assicurarsi che funzioni in modo corretto.  Di seguito viene descritto come creare un test harness per eseguire il visualizzatore senza installarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### Per aggiungere un metodo di test per visualizzare il visualizzatore  
  
1.  Aggiungere il metodo seguente alla classe `public DebuggerSide`:  
  
    ```  
    Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
        Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
    visualizerHost.ShowVisualizer()  
    End Sub  
    ```  
  
2.  Scegliere **Compila MyFirstVisualizer** dal menu **Compila**.  La compilazione del progetto dovrebbe avvenire senza problemi.  Correggere gli eventuali errori di compilazione prima di continuare.  
  
 Creare quindi un progetto eseguibile per chiamare la DLL del visualizzatore.  Per semplicità, utilizzare un progetto applicazione console.  
  
#### Per aggiungere un progetto applicazione console alla soluzione  
  
1.  Scegliere **Aggiungi** dal menu **File**, quindi **Nuovo progetto**.  
  
2.  Nel riquadro **Modelli** della finestra di dialogo **Aggiungi nuovo progetto** fare clic su **Applicazione console**.  
  
3.  Nella casella **Nome**, digitare un nome significativo per l'applicazione console, ad esempio MyTestConsole.  
  
4.  Scegliere **OK**.  
  
 A questo punto è necessario aggiungere i riferimenti appropriati affinché MyTestConsole possa chiamare MyFirstVisualizer.  
  
#### Per aggiungere riferimenti necessari a MyTestConsole  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **MyTestConsole**, quindi scegliere **Aggiungi riferimento** dal menu di scelta rapida.  
  
2.  Nella scheda **.NET** della finestra di dialogo **Aggiungi riferimento** scegliere Microsoft.VisualStudio.DebuggerVisualizers.  
  
3.  Scegliere **OK**.  
  
4.  Fare clic con il pulsante destro del mouse su **MyTestConsole** e scegliere nuovamente **Aggiungi riferimento**.  
  
5.  Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **Progetti** e selezionare MyFirstVisualizer.  
  
6.  Scegliere **OK**.  
  
## Completare il test harness ed eseguire il test del visualizzatore  
 A questo punto verrà aggiunto il codice per completare il test harness.  
  
#### Per aggiungere codice a MyTestConsole  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Program.vb** e scegliere **Rinomina** dal menu di scelta rapida.  
  
2.  Sostituire Module1.vb con un nome appropriato, ad esempio TestConsole.vb.  
  
     Si noti che in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la dichiarazione di classe viene modificata automaticamente in TestConsole.vb in base al nuovo nome file.  
  
3.  In TestConsole.vb aggiungere l'istruzione `Imports` seguente:  
  
    ```  
    Imports MyFirstVisualizer  
    ```  
  
4.  Nel metodo `Main` aggiungere il codice seguente:  
  
    ```  
    Dim myString As String = "Hello, World"  
    DebuggerSide.TestShowVisualizer(myString)  
    ```  
  
 A questo punto è possibile eseguire il test del visualizzatore.  
  
#### Per eseguire il test del visualizzatore  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **MyTestConsole**, quindi scegliere **Imposta come progetto di avvio** dal menu di scelta rapida.  
  
2.  Scegliere **Avvia** dal menu **Debug**.  
  
     Verrà avviata l'applicazione console.  Verrà aperto il visualizzatore contenente la stringa "Hello, World".  
  
 Il visualizzatore  è stato compilato e sottoposto a test.  
  
 Se si desidera utilizzare il visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anziché chiamarlo semplicemente dal test harness, è necessario installarlo.  Per ulteriori informazioni, vedere [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).  
  
## Vedere anche  
 [Architettura del visualizzatore](../debugger/visualizer-architecture.md)   
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Visualizzatori](../debugger/create-custom-visualizers-of-data.md)