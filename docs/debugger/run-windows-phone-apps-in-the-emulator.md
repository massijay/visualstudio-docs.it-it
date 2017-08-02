---
title: "Eseguire app di Windows Phone nell&#39;emulatore | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Eseguire app di Windows Phone nell&#39;emulatore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Si applica solo a Windows Phone](~/debugger/media/phone_only_content.png "phone\_only\_content")  
  
 L'emulatore Windows Phone è un'applicazione desktop che simula un dispositivo Windows Phone. L'emulatore fornisce un ambiente virtualizzato che ti consente di eseguire debug e test di app Windows Phone nel computer senza un dispositivo fisico. Puoi simulare eventi comuni di tocco e rotazione e scegliere le dimensioni fisiche dello schermo e la risoluzione che vuoi emulare. Puoi anche testare numerose funzionalità comuni, come posizione, rete, notifiche, sensori, accelerometro e scheda SD opzionale.  
  
 Per altre informazioni sulle funzionalità che puoi testare nell'emulatore, vedi [Eseguire app di Windows Phone nell'emulatore](http://msdn.microsoft.com/it-it/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Insieme a Visual Studio, l'emulatore offre un ambiente completo in cui puoi progettare, sviluppare e testare le app di Windows Phone, nonché eseguirne il debug.  
  
## In questo argomento  
  
-   [Eseguire un'app Windows Phone nell'emulatore](#BKMK_run)  
  
    -   [Eseguire un'app da Visual Studio](#BKMK_vs)  
  
    -   [Eseguire un'app con lo strumento Distribuzione applicazione](#BKMK_depltool)  
  
-   [Configurare l'emulatore Windows Phone con la barra degli strumenti dell'emulatore](#BKMK_toolbar)  
  
-   [Usare i pulsanti hardware simulati nell'emulatore](#BKMK_buttons)  
  
-   [Usare la tastiera del computer con l'emulatore](#BKMK_tasks_kbd)  
  
-   [Salvare e caricare checkpoint personalizzati](#BKMK_checkpoints)  
  
-   [Acquisire schermate nell'emulatore](#BKMK_tasks_shot)  
  
##  <a name="BKMK_run"></a> Eseguire un'app Windows Phone nell'emulatore  
 Quando sviluppi un'app di Windows Phone, puoi usare l'emulatore Windows Phone per distribuire e testare rapidamente l'app. Ti consigliamo, tuttavia, di testare l'app in un dispositivo Windows Phone reale prima di pubblicarla in Windows Phone Store. In questo modo potrai provare l'app sperimentando la stessa esperienza che proverà l'utente.  
  
 Quando esegui un'app di Windows Phone per la prima volta nell'emulatore Windows Phone, si verificano gli eventi seguenti:  
  
1.  L'emulatore si avvia.  
  
2.  L'emulatore carica il sistema operativo Windows Phone.  
  
3.  L'emulatore visualizza la schermata iniziale di Windows Phone.  
  
4.  L'app viene distribuita nell'emulatore.  
  
5.  L'app viene eseguita nell'emulatore.  
  
 Se l'emulatore selezionato è già in esecuzione, l'app viene distribuita e avviata nell'emulatore in esecuzione. Può essere in esecuzione una sola istanza di ogni emulatore per volta.  
  
> [!TIP]
>  Quando testi l'app nell'emulatore, lascia aperto l'emulatore tra le sessioni di debug per poter eseguire di nuovo l'app rapidamente.  
  
###  <a name="BKMK_vs"></a> Eseguire un'app da Visual Studio  
  
##### Per distribuire ed eseguire un'app da Visual Studio  
  
1.  In Visual Studio apri un progetto Windows Phone.  
  
2.  seleziona una delle opzioni per l'emulatore dalla barra degli strumenti **Standard**.  
  
     ![Elenco di immagini dell'emulatore di Windows Phone](~/debugger/media/wp_emulator_list.png "WP\_Emulator\_list")  
  
3.  Per distribuire ed eseguire l’app con il debug, scegli **Avvia debug** dal menu **Debug** o premi F5.  
  
     Per distribuire ed eseguire l'app senza eseguire il debug, scegli **Avvia senza eseguire debug** dal menu **Debug** o premi CTRL\+F5.  
  
     L’app viene distribuita e avviata.  
  
     Per distribuire l'app senza eseguirla, scegli **Distribuisci soluzione** dal menu **Compila**.  
  
##### Per arrestare un'app in esecuzione  
  
-   Per arrestare un'app in esecuzione, effettua una delle seguenti operazioni:  
  
    -   In Visual Studio scegli **Arresta debug** dal menu **Debug** oppure premi MAIUSC\+F5.  
  
    -   Nell'emulatore premi il pulsante **Indietro** per uscire dall'app. Se la pagina attiva dell'app non era quella iniziale, potrebbe essere necessario premere il pulsante **Indietro** più di una volta.  
  
     L'app si chiude e viene visualizzata la schermata iniziale. Termina così la sessione di debug corrente.  
  
##### Per riavviare un'app senza eseguire il debug  
  
1.  Nell'emulatore, nella schermata iniziale, scorri rapidamente verso sinistra per visualizzare l'elenco di app.  
  
2.  Nell'elenco tocca l'icona dell'app. L'app viene riavviata senza eseguire il debug.  
  
##### Per disattivare un'app in esecuzione  
  
1.  Prima di eseguire l'app, in Visual Studio fai clic con il pulsante destro del mouse sul progetto in Esplora soluzioni, quindi scegli **Proprietà** per aprire **Progettazione progetti**.  
  
2.  In **Progettazione progetti**, nella pagina **Debug**, lascia deselezionata la casella di controllo **Rimozione definitiva al momento della disattivazione durante il debug** se desideri che l'app passi a uno stato inattivo quando viene disattivata. Seleziona la casella di controllo se desideri che l'app venga rimossa definitivamente quando viene disattivata.  
  
3.  Scegli **Avvia debug** dal menu **Debug** oppure premi F5 per eseguire l'app.  
  
4.  Nell'emulatore fai clic sul pulsante di avvio. Viene visualizzata la schermata iniziale e l'app viene disattivata. L'app passa a uno stato inattivo oppure viene rimossa definitivamente, a seconda dell'impostazione della casella di controllo **Rimozione definitiva al momento della disattivazione durante il debug**.  
  
##### Per riattivare un'app inattiva o rimossa definitivamente  
  
-   Nell'emulatore premi il pulsante **Indietro** per tornare all'app. Se sei passato ad altre pagine o hai aperto un'altra app, potrebbe essere necessario premere il pulsante **Indietro** più di una volta per riattivare l'app.  
  
     La sessione di debug viene ripresa. Se il debugger si è scollegato dall'app, potrebbe essere necessario premere F5 per riprendere la sessione di debug.  
  
###  <a name="BKMK_depltool"></a> Eseguire un'app con lo strumento Distribuzione applicazione  
 Puoi anche usare lo strumento Distribuzione applicazione di Windows Phone \(**AppDeploy.exe**\) per eseguire l'app nell'emulatore. Questo strumento è un'app autonoma che viene installata al momento dell'installazione degli strumenti di sviluppo di Windows Phone.  
  
 Vedi [Distribuire app di Windows Phone 8.1 con lo strumento Distribuzione applicazione](../Topic/Deploy%20Windows%20Phone%208.1%20apps%20with%20the%20Application%20Deployment%20tool.md).  
  
##  <a name="BKMK_toolbar"></a> Configurare l'emulatore Windows Phone con la barra degli strumenti dell'emulatore  
 La schermata seguente mostra i pulsanti di configurazione disponibili sulla barra degli strumenti dell'emulatore.  
  
 f21574ab-5970-4b7a-9281-c13073bf6767  
  
|Pulsanti della barra degli strumenti|Opzioni di configurazione|  
|------------------------------------------|-------------------------------|  
|![Opzioni di input sulla barra degli strumenti dell'emulatore di Windows Phone](~/debugger/media/wp_emulator_.png "WP\_Emulator\_")|**Configurazione input punto singolo o multipunto**<br /><br /> Abilitando la configurazione dell'input multipunto, puoi fare clic con il pulsante destro del mouse per spostare i punti di tocco senza toccare lo schermo. Puoi quindi fare clic con il pulsante sinistro del mouse per spostare entrambi i punti di tocco simultaneamente.|  
|![Orientamento sulla barra degli strumenti dell'emulatore di Windows Phone](~/debugger/media/wp_emulator_rotation.png "WP\_Emulator\_rotation")|**Configurazione dell'orientamento dell'emulatore**<br /><br /> Puoi modificare l'orientamento nell'emulatore Windows Phone scegliendo una delle tre opzioni disponibili: verticale, orizzontale verso sinistra o orizzontale verso destra. Le dimensioni dell'emulatore non cambiano quando modifichi l'orientamento.<br /><br /> Per modificare l'orientamento, fai clic sul pulsante **Ruota a sinistra** o **Ruota a destra**.|  
|![Opzioni per le dimensioni sulla barra degli strumenti dell'emulatore di Windows Phone](~/debugger/media/wp_emulator_size.png "WP\_Emulator\_size")|**Configurazione delle dimensioni dell'emulatore**<br /><br /> Puoi modificare le dimensioni dell'emulatore sullo schermo del computer host. I punti per pollice \(DPI, Dots Per Inch\) per l'emulatore sono basati sul valore DPI del monitor host, indipendentemente dal valore dello zoom.<br /><br /> -   Per adattare l'emulatore allo schermo, fai clic sul pulsante **Adatta allo schermo**.<br />-   Per modificare l'impostazione dello zoom, fai clic sul pulsante **Zoom**. Viene visualizzata la finestra di dialogo **Zoom**. Nella finestra di dialogo **Zoom** immetti un valore per lo zoom compreso tra 33 e 100.|  
  
##  <a name="BKMK_buttons"></a> Usare i pulsanti hardware simulati nell'emulatore  
 Per simulare l'uso dei pulsanti hardware di un telefono, puoi usare i pulsanti hardware simulati sul lato destro dello schermo dell'emulatore.  
  
-   Fai clic sul pulsante di accensione per simulare l'accensione e lo spegnimento dello schermo. Fai clic e tieni premuto per simulare lo spegnimento del telefono.  
  
-   Fai clic sul pulsante per alzare o abbassare il volume per simulare la modifica del volume dell'altoparlante del telefono per le chiamate e le notifiche.  
  
-   Il pulsante della fotocamera consente di avviare la relativa app. Puoi simulare lo scatto di una foto o l'acquisizione di un video usando i controlli nell'app della fotocamera.  
  
 La schermata seguente mostra i pulsanti hardware simulati.  
  
1.  L'immagine a sinistra mostra la schermata iniziale dell'emulatore.  
  
2.  L'immagine centrale mostra l'emulatore dopo avere toccato il pulsante di accensione per disattivare lo schermo.  
  
3.  L'immagine a destra mostra lo schermo dell'emulatore dopo avere toccato il pulsante per alzare il volume.  
  
 ![Pulsanti dell'emulatore di Windows Phone](~/debugger/media/wp_emulator_buttons.png "WP\_Emulator\_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a> Usare la tastiera del computer con l'emulatore  
 L'emulatore consente di mappare la tastiera hardware del computer di sviluppo alla tastiera di un dispositivo Windows Phone. Il comportamento dei tasti corrisponde a quello in un dispositivo Windows Phone.  
  
 Per impostazione predefinita, la tastiera hardware non è abilitata. Questa implementazione equivale a una tastiera scorrevole che deve essere distribuita per poter essere usata. Prima di abilitare la tastiera hardware, l'emulatore accetta l'input solo dai tasti CTRL.  
  
 I caratteri speciali sulla tastiera di una versione localizzata di un computer di sviluppo Windows non sono supportati dall'emulatore. Per immettere caratteri speciali presenti su una tastiera localizzata, usa il pannello di input software.  
  
#### Per usare la tastiera del computer nell'emulatore  
  
-   Premi PGSU.  
  
     \- oppure \-  
  
-   Premi PAUSA\/INTERR.  
  
#### Per smettere di usare la tastiera hardware del computer nell'emulatore  
  
-   Premi PGGIÙ.  
  
     \- oppure \-  
  
-   Premi PAUSA\/INTERR.  
  
 La tabella seguente illustra i tasti di una tastiera hardware che puoi usare per emulare i pulsanti e altri controlli di un dispositivo .  
  
|Tasto hardware del computer|Pulsante hardware di Windows Phone|Note|  
|---------------------------------|----------------------------------------|----------|  
|F1|INDIETRO|Le pressioni lunghe funzionano come previsto.|  
|F2|AVVIO|Le pressioni lunghe funzionano come previsto.|  
|F3|CERCA||  
|F4|Non applicabile.||  
|F5|Non applicabile.||  
|F6|FOTOCAMERA METÀ|Pulsante dedicato della fotocamera che viene premuto fino a metà.|  
|F7|FOTOCAMERA COMPLETO|Pulsante dedicato della fotocamera.|  
|F8|Non applicabile.||  
|F9|VOLUME SU||  
|F10|VOLUME GIÙ||  
|F11|Non applicabile.||  
|F12|ACCENSIONE|Premi il tasto F12 due volte per abilitare la schermata di blocco.<br /><br /> Le pressioni lunghe funzionano come previsto.|  
|ESC|INDIETRO|Le pressioni lunghe funzionano come previsto.|  
|PAUSA\/INTERR|Attiva\/disattiva tastiera|Attiva o disattiva la tastiera hardware.|  
|PGSU|Freccia SU tastiera|Abilita la tastiera hardware.|  
|PGGIÙ|Freccia GIÙ tastiera|Disabilita la tastiera hardware.|  
  
##  <a name="BKMK_checkpoints"></a> Salvare e caricare checkpoint personalizzati  
 Per salvare uno snapshot dello stato dell'emulatore puoi usare la scheda **Checkpoint** disponibile nell'emulatore in **Strumenti aggiuntivi**. Questa funzionalità è utile se testi frequentemente l'app con gli stessi dati e le stesse impostazioni.  
  
 Se, ad esempio, l'app richiede diversi contatti, puoi creare i record dei contatti una volta e salvare uno snapshot dell'emulatore. In caso contrario, dovrai ricreare i record dei contatti ogni volta che avvii l'emulatore.  
  
-   Fai clic su **Nuovo checkpoint** per acquisire un nuovo snapshot dello stato dell'emulatore con le impostazioni e i dati necessari per testare di nuovo l'app in un secondo momento. Il nuovo checkpoint viene aggiunto all'elenco **Checkpoint**.  
  
     Non puoi acquisire un checkpoint mentre il debugger è collegato all'emulatore.  
  
-   Seleziona un checkpoint nell'elenco **Checkpoint** per visualizzare le relative informazioni.  
  
-   Seleziona il pulsante di opzione nella colonna **Predefinito** per impostare un checkpoint salvato come predefinito per l'emulatore attivo.  
  
-   Fai clic su **Ripristina** per riavviare il sistema operativo Windows Phone nell'emulatore e caricare lo snapshot selezionato.  
  
-   Fai clic su **Elimina** per eliminare uno snapshot non più necessario.  
  
 L'immagine dell'emulatore originale viene sempre visualizzata come primo elemento nell'elenco **Checkpoint** e non può essere modificata o eliminata. Puoi tuttavia selezionare uno snapshot diverso come immagine dell'emulatore originale.  
  
 ![Scheda Checkpoints dell'emulatore di Windows Phone](~/debugger/media/wp_emulator_checkpoints.png "WP\_Emulator\_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a> Acquisire schermate nell'emulatore  
 Puoi creare schermate delle app di Windows Phone usando lo strumento per l'acquisizione delle schermate disponibile nella finestra Strumenti aggiunti. Lo strumento crea file PNG corrispondenti alla risoluzione dell'emulatore in esecuzione.  
  
 ![Schermate dell'emulatore di Windows Phone](~/debugger/media/wp_emulator_screenshots.png "WP\_Emulator\_screenshots")  
  
#### Per creare una schermata di un'app usando lo strumento integrato nell'emulatore  
  
1.  Per ottimizzare la qualità delle schermate, imposta il livello di zoom dell'emulatore su 100%. Maggiore è il livello di zoom, migliore sarà la qualità della schermata.  
  
2.  Avvia l'app nell'emulatore.  
  
3.  Sulla barra degli strumenti dell'emulatore fai clic sul pulsante di espansione per aprire la finestra **Strumenti aggiuntivi**.  
  
4.  Fai clic sulla scheda **Schermata**.  
  
5.  Quando l'app è pronta, fai clic sul pulsante **Acquisisci**.  
  
     La schermata viene visualizzata nell'area di lavoro.  
  
6.  Fai clic sul pulsante **Salva** per aprire la finestra di dialogo **Salva con nome**.  
  
7.  Scegli la posizione e il nome file desiderati, quindi fai clic su **Salva**.  
  
8.  Se lo desideri, puoi passare ad altre pagine dell'app e acquisire ulteriori schermate.  
  
9. Avvia un emulatore con una risoluzione dello schermo diversa per acquisire la stessa schermata con diverse risoluzioni. Se hai eseguito l'app con il debug, devi arrestare il debug prima di eseguire di nuovo l’app in un altro emulatore.  
  
 Disabilita i contatori della frequenza dei fotogrammi sullo schermo dell'emulatore prima di acquisire le schermate che verranno inviate a Windows Phone Store.  
  
#### Per disabilitare i contatori della frequenza dei fotogrammi nell'emulatore prima di acquisire le schermate  
  
-   Specifica una build di rilascio in Visual Studio. Dopo aver specificato una build di rilascio, avvia l'app facendo clic sul link **Distribuisci *\[nome app\]*** nel menu **Compila**.  
  
-   In alternativa, puoi impostare come commento la riga di codice nel file app.xaml.cs o app.xaml.vb che imposta il valore di `EnableFrameRateCounter` su `true`.