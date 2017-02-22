---
title: "Passaggio 4: creare il layout del form con un controllo TableLayoutPanel | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Passaggio 4: creare il layout del form con un controllo TableLayoutPanel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo passaggio si aggiunge un controllo `TableLayoutPanel` al form.  TableLayoutPanel consente di allineare in modo corretto i controlli nel form che si aggiungerà successivamente.  
  
 ![Collegamento a video](../data-tools/media/playvideo.png "PlayVideo") Per una versione video di questo argomento, vedere [Esercitazione 1: creare un visualizzatore di immagini in Visual Basic \- Video 2](http://go.microsoft.com/fwlink/?LinkId=205211) oppure [Esercitazione 1: creare un visualizzatore di immagini in C\# \- Video 2](http://go.microsoft.com/fwlink/?LinkId=205200).  In questi video viene utilizzata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente.  Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.  
  
### Per creare il layout del form con un controllo TableLayoutPanel  
  
1.  Sul lato sinistro dell'IDE di Visual Studio individuare la scheda **Casella degli strumenti**.  Scegliere la scheda **Casella degli strumenti**. Verrà visualizzata la casella degli strumenti. In alternativa, sulla barra dei menu scegliere **Visualizza**, **Casella degli strumenti**.  
  
2.  Scegliere il piccolo simbolo del triangolo accanto al gruppo **Contenitori** per aprirlo, come mostrato nell'immagine seguente.  
  
     ![Gruppo di contenitori](../ide/media/express_toolbox.png "Express\_Toolbox")  
Gruppo Contenitori  
  
3.  È possibile aggiungere al form controlli quali pulsanti, caselle di controllo ed etichette.  Fare doppio clic sul controllo `TableLayoutPanel` nella Casella degli strumenti. In alternativa, è possibile trascinare il controllo dalla casella degli strumenti al form. Quando si esegue questa operazione, l'IDE aggiunge un controllo `TableLayoutPanel` al form, come mostrato nell'immagine seguente.  
  
     ![Controllo TableLayoutPanel](../ide/media/express_formtablelayout.png "Express\_FormTableLayout")  
Controllo TableLayoutPanel  
  
    > [!NOTE]
    >  Dopo aver aggiunto il controllo TableLayoutPanel, se nel form viene visualizzata una finestra con il titolo **Attività di TableLayoutPanel**, fare clic ovunque all'interno del form per chiuderla.  Verranno fornite ulteriori informazioni su questa finestra più avanti nell'esercitazione.  
  
     Si noti come la Casella degli strumenti si espanda per includere il form quando si fa clic sulla scheda e come si chiuda quando si fa clic in un punto esterno.  Si tratta della funzionalità Nascondi automaticamente dell'IDE.  È possibile attivarla o disattivarla e bloccare in posizione qualsiasi finestra facendo clic sull'icona a forma di puntina da disegno nell'angolo superiore destro della finestra.  L'icona a forma di puntina da disegno ha l'aspetto seguente.  
  
     ![Icona della puntina da disegno](../ide/media/express_pushpintoolbox.png "Express\_PushpinToolbox")  
Icona a forma di puntina da disegno  
  
4.  Accertarsi che **TableLayoutPanel** sia selezionato facendo clic su di esso.  È possibile verificare quale controllo è selezionato osservando l'elenco a discesa nella parte superiore della finestra **Proprietà**, come mostrato nell'immagine seguente.  
  
     ![Finestra Proprietà con il controllo TableLayoutPanel](../ide/media/express_controlspropwin.png "Express\_ControlsPropWin")  
Finestra Proprietà che mostra il controllo TableLayoutPanel  
  
5.  Scegliere il pulsante **Alfabetico** sulla barra degli strumenti della finestra **Proprietà**.  In questo modo, l'elenco delle proprietà nella finestra **Proprietà** viene visualizzato in ordine alfabetico, per semplificare l'individuazione delle proprietà in questa esercitazione.  
  
6.  Il selettore dei controlli è un elenco a discesa che si trova nella parte superiore della finestra **Proprietà**.  In questo esempio, viene mostrato che è selezionato un controllo denominato `tableLayoutPanel1`.  È possibile selezionare i controlli scegliendo un'area in Progettazione Windows Form o selezionandoli dal selettore dei controlli.  Ora che `TableLayoutPanel` è selezionato, individuare la proprietà **Dock** e scegliere **Ancora**, che dovrebbe essere impostato su **Nessuno**.  Si noti che viene visualizzata una freccia a discesa accanto al valore.  Fare clic sulla freccia, quindi selezionare il pulsante **Fill** \(il pulsante grande al centro\), come mostrato nell'immagine seguente.  
  
     ![Finestra Proprietà con Fill selezionato](../ide/media/express_docktable.png "Express\_DockTable")  
Finestra Proprietà con Fill selezionato  
  
     Il termine *ancoraggio* in Visual Studio indica quando una finestra è associata a un'altra finestra o area nell'IDE.  Ad esempio, la finestra Proprietà può essere non ancorata, ovvero non collegata e mobile all'interno di Visual Studio, oppure può essere ancorata a **Esplora soluzioni**.  
  
7.  Dopo aver impostato la proprietà **Dock** di TableLayoutPanel su **Fill**, il pannello riempie l'intero form.  Se si ridimensiona nuovamente il form, TableLayoutPanel resta ancorato e viene ridimensionato correttamente.  
  
    > [!NOTE]
    >  Un controllo TableLayoutPanel funziona come una tabella di Microsoft Office Word: dispone di righe e colonne e una singola cella può estendersi su più righe e colonne.  Ogni cella può contenere un controllo \(come un pulsante, una casella di controllo o un'etichetta\).  TableLayoutPanel disporrà di un controllo `PictureBox` che si estende sull'intera riga superiore, un controllo `CheckBox` nella cella inferiore sinistra e quattro controlli `Button` nella cella inferiore destra.  
  
8.  Attualmente, TableLayoutPanel dispone di due righe delle stesse dimensioni e di due colonne delle stesse dimensioni.  È necessario ridimensionarle in modo che la riga superiore e la colonna a destra siano entrambe molto più grandi.  In Progettazione Windows Form selezionare il controllo TableLayoutPanel.  Nell'angolo superiore destro si trova un piccolo pulsante a forma di triangolo nero, illustrato di seguito.  
  
     ![Pulsante triangolare](../ide/media/express_iconblacktriangle.png "Express\_IconBlackTriangle")  
Pulsante a forma di triangolo  
  
     Questo pulsante indica che il controllo dispone di attività che consentono di impostare automaticamente le proprietà.  
  
9. Scegliere il triangolo per visualizzare l'elenco attività del controllo, come mostrato nell'immagine seguente.  
  
     ![Attività di TableLayoutPanel](../ide/media/express_tablepanel.png "Express\_TablePanel")  
Attività relative di TableLayoutPanel  
  
10. Scegliere l'attività **Modifica righe e colonne** per visualizzare la finestra **Stili di riga e colonna**.  Fare clic su **Column1** e impostare le dimensioni su 15% verificando che il pulsante **%** sia selezionato e immettendo `15` nella casella **%**. Si tratta di un controllo `NumericUpDown` che si utilizzerà in un'esercitazione successiva. Scegliere **Column2** e impostarla su 85%.  Non scegliere ancora il pulsante **OK**, perché la finestra verrebbe chiusa. Se tuttavia si fa clic su OK, è possibile riaprire la finestra utilizzando l'elenco attività.  
  
     ![Stili per riga e colonna di TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png "VS\_TableLayoutPanel\_Setup")  
Stili di riga e colonna di TableLayoutPanel  
  
11. Dall'elenco a discesa **Mostra** nella parte superiore della finestra scegliere **Righe**.  Impostare **Row1** su 90% e **Row2** su 10%.  
  
12. Fare clic sul pulsante **OK**.  Il controllo TableLayoutPanel dispone ora di una riga grande nella parte superiore, una riga piccola nella parte inferiore, una colonna piccola a sinistra e una colonna grande a destra.  È possibile ridimensionare righe e colonne in TableLayoutPanel scegliendo tableLayoutPanel1 nel form e trascinando quindi i bordi di righe e colonne.  
  
     ![Form1 con TableLayoutPanel ridimensionato](../ide/media/vs_formafterlayoutpanel.png "VS\_FormAfterLayoutPanel")  
Form1 con TableLayoutPanel ridimensionato  
  
### Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 5: aggiungere controlli al form](../Topic/Step%205:%20Add%20Controls%20to%20Your%20Form.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 3: impostare le proprietà del form](../ide/step-3-set-your-form-properties.md).