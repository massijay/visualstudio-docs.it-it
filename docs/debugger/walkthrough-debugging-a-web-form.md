---
title: "Procedura dettagliata: debug di un Web Form | Microsoft Docs"
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
  - "ASP.NET (pagine Web), debug"
  - "ASP.NET (siti Web), debug"
  - "ASP.NET, debug di applicazioni Web"
  - "debug [Visual Studio], Web Form"
  - "debug di applicazioni Web ASP.NET, Web Form"
  - "applicazioni Web [.NET Framework], debug"
  - "pagine Web [.NET Framework], debug"
  - "siti Web [.NET Framework], debug"
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 31
---
# Procedura dettagliata: debug di un Web Form
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nei passaggi di questa procedura dettagliata viene illustrato come eseguire il debug di un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], noto anche come Web Form.  Viene spiegato come avviare e arrestare l'esecuzione, impostare punti di interruzione ed esaminare le variabili nella finestra **Espressioni di controllo**.  
  
> [!NOTE]
>  Per completare la procedura dettagliata, è necessario disporre di privilegi di amministratore per il computer server.  Per impostazione predefinita, il processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], aspnet\_wp.exe o w3wp.exe viene eseguito come processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Per eseguire il debug di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], è necessario disporre dei privilegi di amministratore per il computer in cui [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] viene eseguito.  Per ulteriori informazioni, vedere [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
 Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per creare il Web Form  
  
1.  Se una soluzione è già aperta, chiuderla.  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Sito Web**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo sito Web**.  
  
3.  Nel riquadro **Modelli** selezionare **Sito Web ASP.NET**.  
  
4.  Nella riga **Percorso** selezionare **HTTP** dall'elenco e digitare http:\/\/localhost\/WebSite nella casella di testo.  
  
5.  Nell'elenco **Linguaggio** fare clic su **Visual C\#** oppure su **Visual Basic**.  
  
6.  Scegliere **OK**.  
  
     In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene creato un nuovo progetto e viene visualizzato il codice sorgente HTML predefinito.  Viene inoltre creata una nuova directory virtuale denominata **WebSite** in **Sito Web predefinito** di IIS.  
  
7.  Fare clic sulla scheda **Progettazione** sul margine inferiore.  
  
8.  Scegliere la scheda **Casella degli strumenti** sul margine sinistro o selezionarla dal menu **Visualizza**.  
  
     Verrà aperta la **Casella degli strumenti**.  
  
9. Nella **Casella degli strumenti** fare clic sul controllo **Button** e aggiungerlo nell'area di progettazione principale Default.aspx.  
  
10. Nella **Casella degli strumenti** fare clic sul controllo **Textbox** e trascinarlo nell'area di progettazione principale Default.aspx.  
  
11. Fare doppio clic sul controllo Button trascinato.  
  
     Verrà visualizzata la tabella codici: Default.aspx.cs per C\# o Default.aspx.vb per [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  Il cursore dovrebbe trovarsi in corrispondenza della funzione `Button1_Click`.  
  
12. Nella funzione `Button1_Click` aggiungere il codice seguente:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Il progetto dovrebbe essere compilato senza errori.  
  
     A questo punto sarà possibile avviare il debug.  
  
### Per eseguire il debug del Web Form  
  
1.  Nella finestra Default.aspx.cs o Default.aspx.vb fare clic sul margine sinistro della stessa riga del testo aggiunto:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Verrà visualizzato un punto di colore rosso e il testo sulla riga verrà evidenziato in rosso.  Il punto di colore rosso rappresenta un punto di interruzione.  Quando verrà raggiunto questo punto nel codice, l'esecuzione dell'applicazione nel debugger verrà interrotta.  Sarà quindi possibile visualizzare lo stato dell'applicazione ed eseguirne il debug.  Per ulteriori informazioni, vedere [Punti di interruzione](http://msdn.microsoft.com/it-it/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Scegliere **Avvia debug** dal menu **Debug**.  
  
3.  Viene visualizzata la finestra di dialogo **Debug non attivato**.  Selezionare l'opzione **Modifica file Web.config per abilitare il debug**, quindi fare clic su **OK**.  
  
     Verrà avviato Internet Explorer e verrà visualizzata la pagina appena progettata.  
  
4.  In Internet Explorer fare clic sul pulsante.  
  
     In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà visualizzata la riga in cui si imposta il punto di interruzione sulla tabella codici Default.aspx.cs o Default.aspx.vb.  Tale riga dovrebbe essere evidenziata in giallo.  A questo punto è possibile visualizzare le variabili dell'applicazione e controllarne l'esecuzione.  L'esecuzione dell'applicazione verrà interrotta e sarà necessario eseguire un comando.  
  
5.  Scegliere **Finestre** dal menu **Debug**, quindi **Espressioni di controllo** e infine **Espressione di controllo 1**.  
  
6.  Nella finestra **Espressioni di controllo** digitare TextBox1.Text.  
  
     Nella finestra **Espressioni di controllo** verrà visualizzato il valore della variabile `TextBox1.Text`:  
  
    ```  
    ""  
    ```  
  
7.  Scegliere **Esegui istruzione\/routine** dal menu **Debug**.  
  
     Nella finestra **Espressioni di controllo** il valore di `TextBox1.Text` viene modificato.  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  Scegliere **Continua** dal menu **Debug**.  
  
9. In Internet Explorer fare di nuovo clic sul pulsante.  
  
     L'esecuzione verrà nuovamente interrotta in corrispondenza del punto di interruzione.  
  
10. Nella finestra Default.aspx.cs o Default.aspx.vb fare clic sul punto di colore rosso sul margine sinistro.  
  
     Il punto di interruzione verrà rimosso.  
  
11. Scegliere **Termina debug** dal menu **Debug**.  
  
### Per connettere il debugger al Web Form  
  
1.  È possibile connettere il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a un processo in esecuzione.  Per ottimizzare l'efficacia del debug, compilare il file eseguibile come versione di debug con i file dei simboli con estensione pdb.  
  
2.  Nella finestra Default.aspx.cs o Default.aspx.vb fare clic sul margine sinistro per impostare nuovamente un punto di interruzione in corrispondenza della riga aggiunta:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  Scegliere **Avvia senza eseguire debug** dal menu **Debug**.  
  
     Verrà eseguito il Web Form in Internet Explorer, ma il debugger non verrà connesso.  
  
4.  Connettersi al processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Per ulteriori informazioni, vedere [Debug di applicazioni Web distribuite](../debugger/debugging-deployed-web-applications.md).  
  
5.  In Internet Explorer fare clic sul pulsante nel form.  
  
     In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è necessario raggiungere il punto di interruzione in Default.aspx.cs, Default.aspx.vb o Default.aspx.  
  
6.  Una volta terminato il debug, scegliere **Termina debug** dal menu **Debug**.  
  
## Vedere anche  
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)