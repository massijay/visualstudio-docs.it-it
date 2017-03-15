---
title: "Procedura dettagliata: debug di un Windows Form | Microsoft Docs"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Connetti a processo (finestra di dialogo)"
  - "Connetti a processo (finestra di dialogo), procedure dettagliate"
  - "debugger, connessione a programmi"
  - "debug [Visual Studio], procedure dettagliate"
  - "debug [Visual Studio], Windows Form"
  - "debug di codice gestito, Windows Form"
  - "debug di Windows Form, procedure dettagliate"
  - "Windows Form, debug"
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Procedura dettagliata: debug di un Windows Form
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un Windows Form è una delle più comuni applicazioni gestite.  Un Windows Form consente di creare un'applicazione Windows standard.  È possibile completare questa procedura dettagliata utilizzando Visual Basic, C\# o C\+\+.  
  
 Innanzitutto, è necessario chiudere tutte le soluzioni aperte.  
  
### Per preparare la procedura dettagliata  
  
-   Se già aperta una soluzione aperta, chiuderla. \(Sulla  **File** dal menu  **Chiudi soluzione**.\)  
  
## Creare un nuovo Windows Form  
 Si creerà quindi un nuovo Windows Form.  
  
#### Per creare Windows form per questa procedura dettagliata  
  
1.  Nella  **File** menu, scegliere  **Nuovo** e fare clic su  **progetto**.  
  
     Il  **Nuovo progetto** verrà visualizzata la finestra di dialogo.  
  
2.  Nel riquadro Tipi progetto, aprire la  **di Visual Basic**,  **Visual C\#**, o  **Visual C\+\+** nodo,  
  
    1.  Per Visual Basic o Visual C\#, selezionare il  **Windows** nodo, quindi selezionare  **Applicazione Windows Form** nella  **modelli** riquadro.  
  
    2.  Per Visual C\+\+, selezionare il  **CLR** nodo, quindi selezionare  **Applicazione Windows Form** nella  **modelli** riquadro..  
  
3.  Nella  **modelli** riquadro, seleziona  **Applicazione Windows**.  
  
4.  Nella  **nome** , assegnare al progetto un nome univoco, ad esempio IMetaDataImport:: Procedura\_DebugSemplice.  
  
5.  Click **OK**.  
  
     Visual Studio viene creato un nuovo progetto e verrà visualizzato un nuovo form nella finestra di progettazione Windows Form.  Per ulteriori informazioni, vedere  [Progettazione Windows Form](http://msdn.microsoft.com/it-it/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6.  Nella  **visualizzazione** dal menu  **della casella degli strumenti**.  
  
     Verrà visualizzata la casella degli strumenti.  Per ulteriori informazioni, vedere  [della casella degli strumenti](../ide/reference/toolbox.md).  
  
7.  Nella casella degli strumenti, fare clic sui  **pulsante** di controllo e trascinarlo nell'area di progettazione del Form.  Rilasciare il pulsante sul form.  
  
8.  Nella casella degli strumenti, fare clic sui  **TextBox** di controllo e trascinarlo nell'area di progettazione del Form.  Rilasciare il  **TextBox** nel modulo.  
  
9. Nell'area di progettazione di form, fare doppio clic sul pulsante.  
  
     Verrà visualizzata la pagina di codice.  Il cursore dovrebbe trovarsi in  `button1_Click`.  
  
10. Nella funzione  `button1_Click`., aggiungere il seguente codice:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. Nella  **Build** dal menu  **Compila soluzione**.  
  
     Il progetto dovrebbe essere compilato senza errori.  
  
## Il modulo di debug  
 A questo punto, si è pronti per iniziare il debug.  
  
#### Per eseguire il debug del Windows Form creato per questa procedura dettagliata  
  
1.  Nella finestra di origine, fare clic sul margine sinistro sulla stessa riga in cui è stato aggiunto il testo:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Verrà visualizzato un punto rosso e il testo nella riga verrà evidenziato in rosso.  Il punto rosso rappresenta un punto di interruzione.  Per ulteriori informazioni, vedere  [punti di interruzione](http://msdn.microsoft.com/it-it/fe4eedc1-71aa-4928-962f-0912c334d583).  Quando si esegue l'applicazione nel debugger, il debugger interromperà l'esecuzione in tale posizione quando viene raggiunto il codice.  È quindi possibile visualizzare lo stato dell'applicazione ed eseguirne il debug.  
  
    > [!NOTE]
    >  È anche possibile destro del mouse su qualsiasi riga di codice, scegliere  **punto di interruzione**, quindi fare clic su  **Inserisci punto di interruzione** per aggiungere un punto di interruzione su tale riga.  
  
2.  VIA il  **Debug** menu, scegliere  **Start**.  
  
     Windows Form viene avviato automaticamente.  
  
3.  In Windows Form, fare clic sul pulsante aggiunto.  
  
     In Visual Studio, verrà visualizzata nella riga dove è possibile impostare il punto di interruzione sulla tabella codici.  Questa riga dovrebbe essere evidenziata in giallo.  È ora possibile visualizzare le variabili nell'applicazione e controllarne l'esecuzione.  L'applicazione viene interrotta l'esecuzione, in attesa di un'azione da parte dell'utente.  
  
4.  Nella  **Debug** menu, scegliere  **Windows**, quindi  **espressioni di controllo**e fare clic su  **Watch1**.  
  
5.  Nella  **Watch1** finestra, fare clic su una riga vuota.  Nella  **nome** , digitare  `textBox1.Text`\(se si utilizza Visual Basic, Visual C\# o j\#\) o  `textBox1->Text`\(se si utilizza C\+\+\), quindi premere INVIO.  
  
     Il  **Watch1** finestra Mostra il valore di questa variabile tra virgolette come:  
  
    ```  
    ""  
    ```  
  
6.  Nella  **Debug** menu, scegliere  **Passaggio in**.  
  
     Il valore di textBox1. Text verrà modificato nel  **Watch1**finestra per:  
  
    ```  
    Button was clicked!  
    ```  
  
7.  Nella  **Debug** menu, scegliere  **Continua** per riprendere il debug del programma.  
  
8.  In Windows Form, fare clic sul pulsante.  
  
     Visual Studio interromperà nuovamente l'esecuzione.  
  
9. Fare clic sul punto rosso che rappresenta il punto di interruzione.  
  
     Consente di rimuovere il punto di interruzione dal codice.  
  
10. Nella  **Debug** menu, scegliere  **Termina debug**.  
  
## Allegare all'applicazione Windows Form per il debug  
 In  [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], è possibile connettere il debugger a un processo in esecuzione.  Se si utilizza una versione Express Edition, questa funzionalità non è supportata.  
  
#### Per la connessione all'applicazione Windows Form per il debug  
  
1.  Nel progetto creato in precedenza, fare clic sul margine sinistro per impostare nuovamente un punto di interruzione nella riga aggiunta:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2.  Nella  **Debug** dal menu  **Avvia senza eseguire debug**.  
  
     Windows Form verrà eseguito in Windows, come se si fosse fatto doppio clic, il file eseguibile.  Il debugger non è connesso.  
  
3.  Nella  **Debug** dal menu  **Connetti a processo**. \(Questo comando è disponibile anche nella  **Strumenti di** menu.\)  
  
     Il  **Connetti a processo** verrà visualizzata la finestra di dialogo.  
  
4.  Nella  **Processi disponibili** riquadro, trova il nome del processo \(Walkthrough\_SimpleDebug.exe\) nella  **processo** colonna e fare clic su esso.  
  
5.  Scegliere la  **Connetti** pulsante.  
  
6.  In Windows Form, fare clic su quello e solo pulsante.  
  
     Il debugger interrompe l'esecuzione del Windows Form al punto di interruzione.  
  
## Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)