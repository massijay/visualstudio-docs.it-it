---
title: "Walkthrough: Creating and Accessing WCF Services | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, walkthrough [Visual Studio]"
  - "WCF, Visual Studio tools for"
  - "WCF services"
  - "WCF services, walkthrough"
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 25
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Walkthrough: Creating and Accessing WCF Services
In questa procedura dettagliata viene illustrato come creare un semplice servizio [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], testarlo e accedervi da un'applicazione Windows Form.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Creazione del servizio  
  
#### Per creare un servizio WCF  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi scegliere **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual Basic** o **Visual C\#** e fare clic su **WCF**, seguito da **Libreria del servizio WCF**.  Fare clic su **OK** per aprire il progetto.  
  
     ![Progetto della libreria di servizi WCF](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Viene creato un servizio di lavoro che può essere testato e a cui è possibile accedere.  I due passaggi seguenti mostrano come modificare il metodo predefinito per usare un tipo di dati diverso.  In un'applicazione reale verrebbero aggiunte anche le funzioni dell'utente al servizio.  
  
3.  ![File IService1](~/data-tools/media/wcf2.png "wcf2")  
  
     In **Esplora soluzioni** fare doppio clic su IService1.vb o IService1.cs, quindi trovare la seguente riga:  
  
     [!code-cs[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]  
  
     Modificare il tipo per il parametro `value` su `String`:  
  
     [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]  
  
     Nel codice precedente annotare gli attributi `<OperationContract()>` o `[OperationContract]`.  Questi attributi sono richiesti per tutti i metodi esposti dal servizio.  
  
4.  ![File Service1](../data-tools/media/wcf3.png "wcf3")  
  
     In **Esplora soluzioni** fare doppio clic su Service1.vb o Service1.cs, quindi trovare la seguente riga:  
  
     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-cs[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]  
  
     Modificare il tipo per il parametro value su `String`:  
  
     [!code-cs[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]  
  
## Test del servizio  
  
#### Per testare un servizio WCF  
  
1.  Premere **F5** per eseguire il servizio.  Viene visualizzato un form **Client di prova WCF** che carica il servizio.  
  
2.  Nel form **Client di prova WCF** fare doppio clic sul metodo **GetData\(\)** in **IService1**.  Viene visualizzata la scheda **GetData**.  
  
     ![Metodo GetData &#40;&#41;](../data-tools/media/wcf4.png "wcf4")  
  
3.  Nella casella **Richiesta** selezionare il campo **Valore** e digitare `Hello`.  
  
     ![Campo Valore](../data-tools/media/wcf5.png "wcf5")  
  
4.  Fare clic sul pulsante **Richiama**.  Se viene visualizzata una finestra di dialogo **Avviso di sicurezza** fare clic su **OK**.  Il risultato viene visualizzato nella casella **Risposta**.  
  
     ![Risultato nella casella Risposta](../data-tools/media/wcf6.png "wcf6")  
  
5.  Nel menu **File** fare clic su **Esci** per chiudere il form di test.  
  
## Accesso al servizio  
  
#### Per fare riferimento a un servizio WCF  
  
1.  Nel menu **File** scegliere **Aggiungi** e fare clic su **Nuovo progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual Basic** o **Visual C\#**, selezionare **Windows**, quindi scegliere **Applicazione Windows Form**.  Fare clic su **OK** per aprire il progetto.  
  
     ![Progetto Applicazione Windows Form](../data-tools/media/wcf7.png "wcf7")  
  
3.  Fare clic con il pulsante destro del mouse su **WindowsApplication1**, quindi scegliere **Aggiungi riferimento al servizio**.  La finestra di dialogo **Aggiungi riferimento al servizio** viene visualizzata.  
  
4.  Nella finestra di dialogo **Aggiungi riferimento al servizio** fare clic su **Individua**.  
  
     ![Finestra di dialogo Aggiungi riferimento al servizio](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** viene visualizzato nel riquadro **Servizi**.  
  
5.  Fare clic su **OK** per aggiungere il riferimento al servizio.  
  
#### Per compilare un'applicazione client  
  
1.  In **Esplora soluzioni** fare doppio clic su **Form1.vb** o **Form1.cs** per aprire Progettazione Windows Form, se non è già aperto.  
  
2.  Dalla **Casella degli strumenti** trascinare i controlli `TextBox`, `Label` e `Button` nel form.  
  
     ![Aggiunta di controlli al form](../data-tools/media/wcf9.png "wcf9")  
  
3.  Fare doppio clic su `Button` e aggiungere il seguente codice nel gestore eventi `Click`:  
  
     [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]  
  
4.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **WindowsApplication1**, quindi scegliere **Imposta come progetto di avvio**.  
  
5.  Premere **F5** per eseguire il progetto.  Immettere del testo e fare clic sul pulsante.  L'etichetta visualizza "Valore immesso:" e il testo immesso.  
  
     ![Form che visualizza il risultato](~/data-tools/media/wcf10.png "wcf10")  
  
## Vedere anche  
 [Esempio di uso di servizi ASMX e WCF](http://msdn.microsoft.com/it-it/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)