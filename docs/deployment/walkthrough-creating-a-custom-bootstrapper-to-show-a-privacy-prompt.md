---
title: "Procedura dettagliata: creazione di un programma di avvio automatico per visualizzare un prompt di privacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "distribuzione ClickOnce, prerequisiti"
  - "dipendenze [.NET Framework], pacchetto del programma di avvio automatico personalizzato"
  - "distribuzione di applicazioni [Visual Studio], prerequisiti personalizzati"
  - "prerequisiti [.NET Framework], pacchetto del programma di avvio automatico personalizzato"
  - "distribuzione di Windows Installer, prerequisiti"
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# Procedura dettagliata: creazione di un programma di avvio automatico per visualizzare un prompt di privacy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile configurare le applicazioni ClickOnce in modo che vengano aggiornate automaticamente quando diventano disponibili assembly con versioni di file e di assembly più recenti.  Per assicurarsi che i clienti acconsentano a questo comportamento, è possibile visualizzare un prompt di privacy.  I clienti possono quindi scegliere se concedere l'autorizzazione per l'aggiornamento automatico dell'applicazione.  Se l'aggiornamento automatico non viene consentito, l'applicazione non verrà installata.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Visual Studio 2010.  
  
## Creazione di una finestra di dialogo di consenso all'aggiornamento  
 Per visualizzare un prompt di privacy, creare un'applicazione che richieda al lettore di acconsentire agli aggiornamenti automatici per l'applicazione.  
  
#### Per creare una finestra di dialogo di consenso  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** fare clic su **Windows**, quindi scegliere **Applicazione Windows Form**.  
  
3.  In **Nome** digitare ConsentDialog, quindi fare clic su **OK**.  
  
4.  Nella finestra di progettazione fare clic sul form.  
  
5.  Nella finestra **Proprietà** impostare la proprietà **Text** su Update Consent Dialog.  
  
6.  Nella **Casella degli strumenti** espandere **Tutti i Windows Form** e trascinare il controllo **Label** nel form.  
  
7.  Nella finestra di progettazione fare clic sul controllo etichetta.  
  
8.  Nella finestra **Proprietà** modificare la proprietà **Text** in **Aspetto** nel modo seguente:  
  
     L'applicazione che si sta per installare controlla gli ultimi aggiornamenti nel Web.  Facendo clic su "Accetto", si autorizza l'applicazione a verificare e installare automaticamente gli aggiornamenti da Internet.  
  
9. Nella **Casella degli strumenti** trascinare il controllo **CheckBox** al centro del form.  
  
10. Nella finestra **Proprietà** impostare la proprietà **Text** in **Layout** su Accetto.  
  
11. Nella **Casella degli strumenti** trascinare il controllo **Button** in basso a sinistra nel form.  
  
12. Nella finestra **Proprietà** impostare la proprietà **Text** in **Layout** su Continua.  
  
13. Nella finestra **Proprietà** impostare la proprietà **\(Name\)** in **Design** su ProceedButton.  
  
14. Nella **Casella degli strumenti** trascinare il controllo **Button** in basso a destra nel form.  
  
15. Nella finestra **Proprietà** impostare la proprietà **Text** in **Layout** su Annulla.  
  
16. Nella finestra **Proprietà** impostare la proprietà **\(Nome\)** in **Design** su CancelButton.  
  
17. Nella finestra di progettazione fare doppio clic sulla casella di controllo **Accetto** per generare il gestore dell'evento CheckedChanged.  
  
18. Nel file di codice Form1 aggiungere il codice seguente per il gestore dell'evento CheckedChanged.  
  
     [!code-cs[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Aggiornare il costruttore di classe per disabilitare il pulsante **Continua** per impostazione predefinita.  
  
     [!code-cs[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. Nel file di codice Form1, aggiungere il codice seguente per consentire a una variabile booleana di tenere traccia del consenso agli aggiornamenti online da parte dell'utente finale.  
  
     [!code-cs[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. Nella finestra di progettazione fare doppio clic sul pulsante **Continua** per generare il gestore dell'evento Click.  
  
22. Nel file di codice Form1 aggiungere il codice seguente al gestore dell'evento Click per il pulsante **Continua**.  
  
     [!code-cs[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. Nella finestra di progettazione fare doppio clic sul pulsante **Annulla** per generare il gestore dell'evento Click.  
  
24. Nel file di codice Form1 aggiungere il codice seguente per il gestore dell'evento Click per il pulsante **Annulla**.  
  
     [!code-cs[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Aggiornare l'applicazione in modo da restituire un errore se l'utente finale non acconsente agli aggiornamenti online.  
  
     Solo per sviluppatori Visual Basic:  
  
    1.  In **Esplora soluzioni** fare clic su **ConsentDialog**.  
  
    2.  Scegliere **Aggiungi modulo** dal menu **Progetto**, quindi fare clic su **Aggiungi**.  
  
    3.  Nel file di codice Module1.vb aggiungere il codice seguente.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  Scegliere **Proprietà ConsentDialog** dal menu **Progetto**, quindi fare clic sulla scheda**Applicazione**.  
  
    5.  Deselezionare **Abilita framework applicazione**.  
  
    6.  Nel menu a discesa **Oggetto di avvio** selezionare **Module1**.  
  
        > [!NOTE]
        >  Disabilitando il framework applicazione vengono disabilitate funzionalità quali gli stili di visualizzazione di Windows XP, gli eventi applicazioni, la schermata iniziale, l'applicazione a istanza singola e altro ancora.  Per ulteriori informazioni, vedere [Pagina Applicazione, Creazione progetti \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Solo per sviluppatori Visual C\#:  
  
     Aprire il file di codice Program.cs e aggiungervi il codice seguente.  
  
     [!code-cs[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. Dal menu **Compila**, scegliere **Compila Soluzione**.  
  
## Creazione del pacchetto del programma di avvio automatico personalizzato  
 Per visualizzare il prompt di privacy agli utenti finali, è possibile creare un pacchetto del programma di avvio automatico personalizzato per l'applicazione della finestra di consenso all'aggiornamento e includerlo come prerequisito in tutte le applicazioni ClickOnce.  
  
 Questa procedura dimostra come creare un pacchetto del programma di avvio automatico personalizzato creando i documenti seguenti:  
  
-   Un file manifesto product.xml per descrivere il contenuto del programma di avvio automatico.  
  
-   Un file manifesto package.xml per elencare gli aspetti specifici della localizzazione del pacchetto, ad esempio le stringhe e le condizioni di licenza software.  
  
-   Un documento per le condizioni di licenza software.  
  
#### Passaggio 1: per creare la directory del programma di avvio automatico.  
  
1.  Creare una directory denominata UpdateConsentDialog in %PROGRAMMI%\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
    > [!NOTE]
    >  Potrebbe essere necessario disporre di privilegi amministrativi per creare questa cartella.  
  
2.  Nella directory UpdateConsentDialog, creare una sottodirectory denominata en.  
  
    > [!NOTE]
    >  Creare una nuova directory per ogni impostazione locale.  Ad esempio, è possibile aggiungere sottodirectory per le impostazioni locali fr e de.  Queste directory potrebbero contenere le stringhe e i Language Pack francesi e tedeschi, se necessario.  
  
#### Passaggio 2: per creare il file manifesto product.xml  
  
1.  Creare un file di testo denominato `product.xml`.  
  
2.  Nel file product.xml aggiungere il codice XML seguente.  Assicurarsi di non sovrascrivere il codice XML esistente.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  Salvare il file nella directory del programma di avvio automatico UpdateConsentDialog.  
  
#### Passaggio 3: per creare il file manifesto package.xml e le condizioni di licenza software  
  
1.  Creare un file di testo denominato `package.xml`.  
  
2.  Nel file package.xml, aggiungere il codice XML seguente per definire le impostazioni locali e includere le condizioni di licenza software.  Assicurarsi di non sovrascrivere il codice XML esistente.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  Salvare il file nella sottodirectory en della directory del programma di avvio automatico UpdateConsentDialog.  
  
4.  Creare un documento denominato eula.rtf per le condizioni di licenza software.  
  
    > [!NOTE]
    >  Le condizioni di licenza software devono includere informazioni su licenza, garanzie, responsabilità e leggi locali.  Questi file devono essere specifici delle impostazioni locali, pertanto accertarsi che il file venga salvato in un formato che supporti i caratteri Multibyte Character Set o Unicode.  Consultare il proprio ufficio legale per il contenuto delle condizioni di licenza software.  
  
5.  Salvare il documento nella sottodirectory en della directory del programma di avvio automatico UpdateConsentDialog.  
  
6.  Se necessario, creare un nuovo file manifesto package.xml e un nuovo documento eula.rtf per le condizioni di licenza software per ciascuna impostazione locale.  Ad esempio, se sono state create sottodirectory per le impostazioni locali fr e de, creare file manifesto package.xml e condizioni di licenza software separati e salvarli nelle sottodirectory fr e de.  
  
## Impostazione dell'applicazione di consenso all'aggiornamento come prerequisito  
 In Visual Studio è possibile impostare l'applicazione di consenso all'aggiornamento come prerequisito.  
  
#### Per impostare l'applicazione di consenso all'aggiornamento come prerequisito  
  
1.  In **Esplora soluzioni** fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2.  Scegliere **Proprietà** *Nomeprogetto* dal menu **Progetto**.  
  
3.  Fare clic sulla pagina **Pubblica** e quindi su **Prerequisiti**.  
  
4.  Selezionare **Update Consent Dialog**.  
  
    > [!NOTE]
    >  È possibile che sia necessario chiudere e riaprire Visual Studio per vedere la finestra di consenso all'aggiornamento nella finestra di dialogo Prerequisiti.  
  
5.  Scegliere **OK**.  
  
## Creazione e test del programma di installazione  
 Dopo aver impostato l'applicazione di consenso all'aggiornamento come prerequisito, è possibile generare il programma di installazione e il programma di avvio automatico per l'applicazione.  
  
#### Per creare e testare il programma di installazione non facendo clic su Accetto  
  
1.  In **Esplora soluzioni** fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2.  Scegliere **Proprietà** *Nomeprogetto* dal menu **Progetto**.  
  
3.  Fare clic sulla pagina **Pubblica** e quindi su **Pubblica**.  
  
4.  Se l'output di pubblicazione non viene visualizzato automaticamente, visualizzarlo manualmente.  
  
5.  Eseguire il programma Setup.exe.  
  
     Il programma di installazione mostra il contratto di licenza software della finestra di consenso all'aggiornamento.  
  
6.  Leggere il contratto di licenza software, quindi fare clic su **Accetta**.  
  
     Viene visualizzata l'applicazione della finestra di consenso all'aggiornamento e viene mostrato il testo seguente: L'applicazione che si sta per installare controlla gli ultimi aggiornamenti nel Web.  Facendo clic su Accetto, si autorizza l'applicazione a verificare automaticamente gli aggiornamenti in Internet.  
  
7.  Chiudere l'applicazione o fare clic su Annulla.  
  
     Viene visualizzato un errore: Errore durante l'installazione dei componenti di sistema per *NomeApplicazione*.  Impossibile continuare fino alla corretta installazione di tutti i componenti di sistema.  
  
8.  Fare clic su Dettagli per visualizzare il messaggio di errore seguente: Impossibile installare il componente Update Consent Dialog. Messaggi di errore: "Il contratto di aggiornamento automatico non è stato accettato." Impossibile installare i seguenti componenti: \- Update Consent Dialog  
  
9. Fare clic su **Chiudi**.  
  
#### Per creare e testare il programma di installazione facendo clic su Accetto  
  
1.  In **Esplora soluzioni** fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2.  Scegliere **Proprietà** *Nomeprogetto* dal menu **Progetto**.  
  
3.  Fare clic sulla pagina **Pubblica** e quindi su **Pubblica**.  
  
4.  Se l'output di pubblicazione non viene visualizzato automaticamente, visualizzarlo manualmente.  
  
5.  Eseguire il programma Setup.exe.  
  
     Il programma di installazione mostra il contratto di licenza software della finestra di consenso all'aggiornamento.  
  
6.  Leggere il contratto di licenza software, quindi fare clic su **Accetta**.  
  
     Viene visualizzata l'applicazione della finestra di consenso all'aggiornamento e viene mostrato il testo seguente: L'applicazione che si sta per installare controlla gli ultimi aggiornamenti nel Web.  Facendo clic su Accetto, si autorizza l'applicazione a verificare automaticamente gli aggiornamenti in Internet.  
  
7.  Fare clic su **Accetto**, quindi su **Continua**.  
  
     L'installazione dell'applicazione viene avviata.  
  
8.  Se viene visualizzata la finestra di dialogo Installazione applicazione, fare clic su **Installa**.  
  
## Vedere anche  
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)   
 [Creazione di programmi di avvio automatico](../deployment/creating-bootstrapper-packages.md)   
 [Procedura: creare il manifesto di un prodotto](../deployment/how-to-create-a-product-manifest.md)   
 [Procedura: creare un manifesto di pacchetto](../deployment/how-to-create-a-package-manifest.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)